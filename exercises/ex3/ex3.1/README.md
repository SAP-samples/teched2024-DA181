# Exercise 3.1 - Adding Business Partner Service

In this exercise, you will extend your CAP service with the consumption of an external Business Partner service.

1. In this step, go to the [SAP Business Accerlator Hub](https://api.sap.com/) and find the  [Business Partner API (A2X)](https://api.sap.com/api/API_BUSINESS_PARTNER/overview) 

<br>![](/exercises/ex3/ex3.1//images/bpapi.png)

2. In API Resources, select API Specification. From the list of files, download the EDMX file.

<br>![](/exercises/ex3/ex3.1//images/bpodata.png)

In the project explorer, right-click on the project’s root folder and choose Upload. Select the API_BUSINESS_PARTNER.edmx file and upload it to your project folder.

<br>![](/exercises/ex3/ex3.1//images/upload.png)

3. In SAP Build Code, navigate to the project root folder and upload the downloaded API_BUSINESS_PARTNER.edmx. Add the below command in the terminal.

```
cds import API_BUSINESS_PARTNER.edmx --as cds
```
4. Navigate into the srv/external/API_BUSINESS_PARTER.cds. This contains the schema definition of the external service.

<br>![](/exercises/ex3/ex3.1//images/cdsext.png)

5. In your project, add the below code after the namespace (your project name) in the db/schema.cds file 

```cds
//namespace techedda181demo;

using { API_BUSINESS_PARTNER } from '../srv/external/API_BUSINESS_PARTNER.cds';

using { cuid } from '@sap/cds/common';

entity Risks : cuid
{
    risksID : String(10)
        @mandatory;
    description : String(500);
    impact : Integer;
    criticality : Integer;
    mitigations : Association to many Mitigations on mitigations.risk = $self;
    BusinessPartner : Association to one API_BUSINESS_PARTNER.A_BusinessPartner;
}

entity Mitigations : cuid
{
    mitigationsID : String(10)
        @mandatory;
    description : String(500);
    counter : Integer;
    risk : Association to one Risks;
}

```

6. Replace the code snippet of srv/service.cds to the below given code. With this code you can now create a projection of your new service.Of the many entities and properties in these entities that are defined in the API_BUSINESS_PARTNER service, you just look at one of the entities (A_BusinessPartner) and just three of its properties - BusinessPartner, LastName, and FirstName - so that your projection is using a subset of everything the original service has to offer.

```cds
using { API_BUSINESS_PARTNER } from './external/API_BUSINESS_PARTNER.cds';

using { techedda181demo as my } from '../db/schema.cds';

@path : '/service/techedda181demo'
service techedda181demoSrv
{
    @odata.draft.enabled
    entity Risks as
        projection on my.Risks;

    @odata.draft.enabled
    entity Mitigations as
        projection on my.Mitigations;

    entity A_BusinessPartner as
        projection on API_BUSINESS_PARTNER.A_BusinessPartner
        {
            BusinessPartner,
            FirstName,
            LastName
        };
}

annotate techedda181demoSrv with @requires :
[
    'authenticated-user'
];


```

```
NOTE : Please cross check on the name of the service and the entities
```

# Exercise 3.2 Connect your application to the Business Partner API Sandbox Enviroment

Now you have a new service exposed with a definition based on the imported CDS file. However, the CDS file only contains the schema and not the connectivity to the backend, so there is no data yet. In this case, you do not create local data as with your risks and mitigations entities, but you connect your service to the Sandbox environment of the SAP Business Accelerator Hub for the Business Partner API that you want to use. To use the API Business Hub Sandbox APIs, you require an API key. This key will authenticate your application with the API endpoint.

1. Go to the [SAP Business Accerlator Hub](https://api.sap.com/) and make sure you are logged in.

<br>![](/exercises/ex3/ex3.1//images/apilogin.png)

2. Navigate to the Business Partner API (SAP S/4HANA Cloud → Business Partner (A2X)).In the upper-right corner, choose Show API Key to see your API key.

<br>![](/exercises/ex3/ex3.1//images/apikey.png)

3. Copy the API key

<br>![](/exercises/ex3/ex3.1//images/copyapi.png)

4. Go to your project in the SAP Build Code and add the below and replace the <YOUR-API-KEY> with the api key copied from the SAP Business Accerlator Hub.

```
apikey=<YOUR-API-KEY>
```
You are going to use the API key to call the Business Partner API of the sandbox system provided through the SAP Business Accelerator Hub.
<br>![](/exercises/ex3/ex3.1//images/apikeycode.png)

5. Open the package.json file and add the credentials configuration to the API_BUSINESS_PARTNER configuration.

```

"credentials": {
          "url": "https://sandbox.api.sap.com/s4hanacloud/sap/opu/odata/sap/API_BUSINESS_PARTNER/"
        }

```

6. It should look like the following 

<br>![](/exercises/ex3/ex3.1//images/json.png)

7. Open service.js and replace the following.

```javascript
 * @version(2.0)
 */
const LCAPApplicationService = require('@sap/low-code-event-handler');
const risks_Logic = require('./code/risks-logic');

class techedda181demoSrv extends LCAPApplicationService {
    async init() {

        this.after('READ', 'Risks', async (results, request) => {
            await risks_Logic(results, request);
        });

        // connect to remote service
        const BPsrv = await cds.connect.to("API_BUSINESS_PARTNER");
        const { BusinessPartners } = this.entities;
        /**
     * Event-handler for read-events on the BusinessPartners entity.
     * Each request to the API Business Hub requires the apikey in the header.
     */
        this.on("READ", BusinessPartners, async (req) => {
            // The API Sandbox returns alot of business partners with empty names.
            // We don't want them in our application
            req.query.where("LastName <> '' and FirstName <> '' ");

            return await BPsrv.transaction(req).send({
                query: req.query,
                headers: {
                    apikey: process.env.apikey,
                },
            });
        });



        return super.init();
    }
}


module.exports = {
    techedda181demoSrv
};
```

You've now created a custom handler for your service. This time it called on for the READ event.

The handler is invoked when your BusinessPartner service is called for a READ, so whenever there’s a request for business partner data, this handler is called. It ensures the request for the business partner is directed to the external business partner service. Furthermore, you have added a where clause to the request, which selects only business partners where the first and last name is set.

## Summary

You have now successfully extended the CAP service with the consumption of an external Business Partner Service

Continue to -Continue to - [Exercise 4 - Add Application Logic](../ex4/README.md)


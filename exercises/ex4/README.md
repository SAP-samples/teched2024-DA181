# Exercise 4 - Adding Business Partner Service

In this exercise, you will extend your CAP service with the consumption of an external Business Partner service from [SAP Business Accelerator Hub](https://api.sap.com/).

 ## Exercise 4.1 Connect your application to the Business Partner API Sandbox Enviroment

1. In order to import the API_BUSINESS_PARTNER from [SAP Business Accerlator Hub](https://api.sap.com/) lets begin with loging in with your credentials.

<br>![](/exercises/ex4/images/apilogin.png)

2. Once you have logged in, search for Business Partner (A2X)
![alt text](/exercises/ex4/images/api_search.png)   
<br> 
3. Select and open the Business Partner API from the SAP S/4HANA Cloud Public Edition.
![alt text](/exercises/ex4/images/api_search_result.png)  
<br>![alt text](/exercises/ex4/images/image-13.png)

4. Scroll down to API Resources > under __API Specifications__ __download__ the EDMX file.

![alt text](/exercises/ex4/images/image-14.png)

Once downloaded, upload the .edmx file to root folder of your project.
![alt text](/exercises/ex4/images/upload2.png)
![alt text](/exercises/ex4/images/image-15.png)

5. Import the Business Partner file by running the below cds command in the terminal. Click on the icon as shown below, select terminal > new terminal

<br>![](/exercises/ex4/images/image-9.png)
```cds

cds import API_BUSINESS_PARTNER.edmx

```
<br>![](/exercises/ex4/images/terminal_import.png)  

6. The API_BUSINESS_PARTNER.edmx has been imported to the folder srv/external, also it generates API_BUSINESS_PARTNER.csn file. This CSN file is used by the CDS framework.

![alt text](/exercises/ex4/images/{3AFE8A0A-B73A-4461-8D3A-F77554C6E081}.png)

6. The package.json file is now updated in the requires section with the external service.

![alt text](/exercises/ex4/images2/image.png)

7. Add the below line in ./db/schema.cds and ./srv/service.cds

```cds 
using { API_BUSINESS_PARTNER } from '../srv/external/API_BUSINESS_PARTNER';

```
Updated schema.cds will be as follows :

![alt text](/exercises/ex4/images2/image-3.png)

![alt text](/exercises/ex4/images2/image-2.png)


## Ex 4.2 - Edit the Data Model & Service Definition with Business Partner

1. Open the Graphical Modeller under the data models as shown below and open the graphical modeller.

![](/exercises/ex4/images/image-2.png)

2.  Click on the risks entity and click on Add relationship and click on an empty space.
![alt text](/exercises/ex4/images/{49D580CE-8288-4D51-B0B3-15779AA08018}.png)


3. Once the dialog box opens, look for the target entity shown in the image below and rename the a_BusinessPartner to BusinessPartner.

![alt text](/exercises/ex4/images2/image-4.png)

4. Now the data model would look as follows :

![alt text](/exercises/ex4/images2/image-5.png)

5. Go back to your storyboard,  under service, select 'Add Service Entity' as shown below. 

![alt text](/exercises/ex4/images2/image-10.png)

6. Under Projection, choose 'API_BUSINESS_PARTNER.A_BusinessPartner'. Uncheck all properties, and choose only BusinessPartner, FirstName and LastName and save.

![alt text](/exercises/ex4/images2/image-6.png) 

7. Graphical Model & Storyboard will look as follows: 

![alt text](/exercises/ex4/images2/image-7.png)

![alt text](/exercises/ex4/images/{C2A0C7F6-67EB-4BA2-AF39-EDEEE4421B16}.png)



## Ex 4.3 Connect your application to the Business Partner API Sandbox Enviroment

1. In order to read the entity, create a custom handler. In the project folder, under ./srv create a service-handler file *.js, you can name it __bp_api.js__. Copy the below code into the file:

```cds 

const cds = require('@sap/cds');
module.exports = cds.service.impl(async function() {
    const bp = await cds.connect.to('API_BUSINESS_PARTNER');    
    this.on('READ', 'A_BusinessPartner', async req => {        
        return bp.run(req.query);       
    });
});

```
2. Now, go back to the SAP Business Accerlator hub and copy the API Key for the selected Business Partner (A2X) and add it to API_BUSINESS_PARTNER configuration in the package.json file

![alt text](/exercises/ex4/images2/image-20.png)  

```json
      "API_BUSINESS_PARTNER": {
          "kind": "odata-v2",
          "model": "srv/external/API_BUSINESS_PARTNER",
          "credentials": {
            "url": "<URL>",
             "headers": {
                "APIKey": <API_KEY>
            }
          }
        },

```

3. In addition, retrieve the SANDBOX_URL from the api hub and apply it also to the package.json-file

![alt text](/exercises/ex4/images2/image-11.png)


```json
      "API_BUSINESS_PARTNER": {
          "kind": "odata-v2",
          "model": "srv/external/API_BUSINESS_PARTNER",
          "credentials": {
            "url": "https://sandbox.api.sap.com/s4hanacloud/sap/opu/odata/sap/API_BUSINESS_PARTNER/",
             "headers": {
                "APIKey": <API_KEY>
            }
          }
        },

```
You've now created a custom handler for your service. This time it called on for the READ event.

The handler is invoked when your BusinessPartner service is called for a READ, so whenever there’s a request for business partner data, this handler is called. It ensures the request for the business partner is directed to the external business partner service. Furthermore, you have added a where clause to the request, which selects only business partners where the first and last name is set.

## Summary

You have now successfully extended the CAP service with the consumption of an external Business Partner Service

Additionally if you want to try the same with S4 system, follow this - [ Add Business Partner Data ](../ex_optional/README.md)



# Exercise 4 - Consuming an external Business Partner Service

In this exercise, you will extend your application with the consumption of an external Business Partner service, to be connected to a S/4HANA Cloud Public Edition instance.
To facilitate that, we consume the API definition from the [SAP Business Accelerator Hub](https://api.sap.com/) and are able to connect to a SAP provided sandbox instance of S/4HANA Cloud Public Edition.  
By consuming the Business Partner API definition from SAP API Business Accerlator Hub, we ensure a system compliant API integration for the later runtime connection of our Risk Management Application with the real __clean core__ __"S/4HANA Cloud Public Edition"__-source system. The additional instructions for the actual S4 system connection, is given in the optional exercise  [ Add Business Partner Data ](../ex_optional/README.md).

 ## Exercise 4.1 Connect your application to the Business Partner API 

<br>__1.__ In order to import the API_BUSINESS_PARTNER from [SAP Business Accerlator Hub](https://api.sap.com/) lets begin with loging in with your credentials.
<br>![](/exercises/ex4/images/apilogin.png)

<br>__2.__ Once you have logged in, _search_ for __"Business Partner (A2X)"__
<br>![alt text](/exercises/ex4/images/api_search.png)   
 
<br>__3.__ From the returned search results, 
- _select_ and _open_ the __Business Partner (A2X)__ from the __SAP S/4HANA Cloud Public Edition__.
![alt text](/exercises/ex4/images/api_search_result.png)  
- it then shows like
![alt text](/exercises/ex4/images/image-13.png)

<br>__4.__ Let's download the API spedification
- croll down to API Resources > under __API Specifications__ __download__ the EDMX file.

![alt text](/exercises/ex4/images/image-14.png)

- Once downloaded, __upload__ the __.edmx-file__ to the root folder of your project.
![alt text](/exercises/ex4/images/upload2.png)
![alt text](/exercises/ex4/images/image-15.png)

<br>__5.__ Now, import the Business Partner API specification-file 
- Run the cds command in a project terminal. 
- To open Click on the icon as shown below, select terminal > new terminal
<br>![](/exercises/ex4/images/image-9.png)
```cds
cds import API_BUSINESS_PARTNER.edmx
```
<br>![](/exercises/ex4/images/terminal_import.png)  

<br>__6.__ The API_BUSINESS_PARTNER.edmx has been imported to the project folder __"srv/external"__
- In addition, it also generated the API_BUSINESS_PARTNER.csn file. CSN-files are used by the CDS framework, as a notation for compact representations of CDS models — tailored to serve as an optimized format to share and interpret models with minimal footprint and dependencies.

![alt text](/exercises/ex4/images/{3AFE8A0A-B73A-4461-8D3A-F77554C6E081}.png)

<br>__7.__ Furthermore, the __./package.json__ file in your project root directory, is now updated in the __requires section__ with the external service.  
![alt text](/exercises/ex4/images2/image.png)

<br>__8.__ Now, let's link to the external Business Partner API in the data- and service-model definitions
- Add the below line in ./db/schema.cds and ./srv/service.cds

```cds 
using { API_BUSINESS_PARTNER } from '../srv/external/API_BUSINESS_PARTNER';
```
- the updated schema.cds will be as follows :

![alt text](/exercises/ex4/images2/image-3.png)

![alt text](/exercises/ex4/images2/image-2.png)


## Exercise 4.2 - Edit the Data Model and Service Definition with Business Partner
In the following steps, we define the data model and service model relationship with the Business Partner API.

<br>__9.__ From your  __data model__ in the __Storyboard__  _select_ __"Open in Graphical Modeler"__ as shown below:
![](/exercises/ex4/images/image-2.png)

<br>__10.__  Select the __"Risks" entity__ 
- and __click__ on __"Add relationship", 
- then click into the empty space to open the next dialog
![alt text](/exercises/ex4/images/{49D580CE-8288-4D51-B0B3-15779AA08018}.png)

<br>__11.__ Once the dialog box opens
- look for the __target entity-relationship__ shown in the image below 
  - Type: __Association__ and Cardinality: __To-One__
- and _rename_ the a_BusinessPartner to __BusinessPartner__.

![alt text](/exercises/ex4/images2/image-4.png)

<br>__12.__ Now the data model would look as follows :
![alt text](/exercises/ex4/images2/image-5.png)

<br>__13.__ Go back to your __Storyboard__,  under __service__, select __"Add Service Entity"__ as shown below. 

![alt text](/exercises/ex4/images2/image-10.png)

<br>__14.__ Under Projection definition on the right
- first select __"API_BUSINESS_PARTNER.A_BusinessPartner"__ as _key_ element of the associated entity
- then __"un-check" all properties__, 
- and __select__ on the following columns/properties:
  - __BusinessPartner, FirstName__ and __LastName__
- Save by clicking &#x2611;

![alt text](/exercises/ex4/images2/image-6.png) 

<br>__15.__ Now, the __Graphical Service Model__ and the __Storyboard__ will look as follows: 

![alt text](/exercises/ex4/images2/image-7.png)

![alt text](/exercises/ex4/images/{C2A0C7F6-67EB-4BA2-AF39-EDEEE4421B16}.png)



## Exercise 4.3 Connect your application to the Business Partner API Sandbox Environment

<br>__16.__ As a first step, a custom Node.Js service-handler is required to be able to read from external api.
- In the project folder, under ./srv __create__ a new (service-handler) file (*.js-file), name it __bp_api.js__. 
- Then copy the below code into the file:

```cds 
const cds = require('@sap/cds');
module.exports = cds.service.impl(async function() {
    const bp = await cds.connect.to('API_BUSINESS_PARTNER');    
    this.on('READ', 'A_BusinessPartner', async req => {        
        return bp.run(req.query);       
    });
});
```
<br>__17.__ Now, go back to the __SAP Business Accerlator Hub__ and __copy__ the __API Key__ for the selected __Business Partner (A2X)__ and add it to API_BUSINESS_PARTNER configuration in the __package.json__ file

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

<br>__18.__ Moreover, __copy__ the __SANDBOX_URL__ from the __SAP Business Accerlator Hub__ and apply it also to the __package.json-file__

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
<br>__19.__ Save and close the files.

You've now created a custom handler for your service. This time it called on for the READ event.

The handler is invoked when your BusinessPartner service is called for a READ, so whenever there’s a request for business partner data, this handler is called. It ensures the request for the business partner is directed to the external business partner service. 

## Summary

You have now successfully extended the CAP service with the consumption of an external Business Partner Service

Additionally if you want to try the same with S4 system, follow this - [ Add Business Partner Data ](../ex_optional/README.md)

Continue to  - [Exercise 5 - Add UI to your application ](../ex5/README.md)


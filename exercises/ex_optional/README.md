# Add-on exercise - Add Business Partner as External Resource

In this additional instruction, it is outlined how to __change or add__ the __Business Partner API__ pointing to the the business partner entity in a __specific S/4HANA system__, which has to registered in SAP BTP cockpit as a BTP destination. 

Note: Continue with the next steps only if you have an S/4HANA system. The Business Partner API pointing to the SAP Business Accelerator HUB sandbox S/4HANA System  with the mock data (created in Exercise 4) will need to be replaced.


## Create a S/4HANA system destination in SAP BTP Cockpit

The [SAP BTP connectivity documentation](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/http-destination), provides detailed instructions on how to create a HTTP destination to your S/4HANA System.  
<br>__1.__ In SAP BTP Cockpit
- _create_ a __HTTP destination__ applying your systems destination details
- Validate the connectivity
<br>![](/exercises/ex_optional/images/btpc-created.png)
<br>![](/exercises/ex_optional/images/createnewdest.png)
- Add the additional properties
<br>![](/exercises/ex_optional/images/additionalproperties.png)

<br><br>

## Add the S/4HANA system and Business Partner API to your application

The [SAP Build Code service provider documentation](https://help.sap.com/docs/bas/sap-business-application-studio/sap-system-service-provider) gives detailed instructions on how to connect to service destinations form your project.  
<br>__2.__ Back in your SAP Build Code project
-  __Click__ on __"Service Center"__-icon in the left-side activity bar, the service center view opens
-  Click __Add System__ to add your system registered in SAP BTP cockpit in the previous step
   -  Service Center > Service > Select a Provider : SAP System 
   <br>![](/exercises/ex_optional/images/bc_servicecenter.png)
  
- Under Services, you will now see the destination for the API_BUSINESS PARTNER, pointing to your S/4HANA System destination
<br>![](/exercises/ex_optional/images/adds4.png)

<br><br>

## Adjust Business Partner API reference to data- and service model  

<br>__3.__ From Storyboard view and you will now see the external resources added : API_BUSINESS_PARTNER  
<br>![](/exercises/ex_optional/images/storyboardbupa.png)

<br>__4.__ According to the instructions given in [exercise 4.2: editing the data model and service definition with business partner](exercises/ex4#exercise-42---edit-the-data-model-and-service-definition-with-business-partner) you will now need to create the 
- __data model relationship__ from the Risks data entity to the Business Partner API,
- and the __service model relationship__ from the Risks service entity to the Business Partner API.

<br>__5.__ Updated storyboard with additon of business partner in data model & services.

<br>![](/exercises/ex_optional/images/updatedstoryboardbupa.png)



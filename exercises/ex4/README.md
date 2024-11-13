# Exercise 4 - Add Business Partner as External Resource

In this exercise, you can add the business partner into your project by adding the S/4 system as the destination in SAP Business Technology Platform ( BTP).


**NOTE: Continue with the next steps only if you have an S/4 System. You can Skip to [Exercise 3.1 - Add Business Partner Service](../ex4/ex4.1/README.md) to add the mock Business Partner Data**


## 1. Create a S/4 HANA Destination in SAP Business Technology Platform

1. [Setup a Destination in SAP Business Technology Platform ( BTP )](https://help.sap.com/docs/business-rules/business-rules-capability-for-neo-environment/configure-destination-for-sap-s-4hana-cloud)

## 2. Add the S/4 system in your application

1. Go to SAP Build Code, Click on Service Center > Service > Select a Provider : SAP System > Under Services, you will now see the destination created in Exercise 3.1

<br>![](/exercises/ex4/images/adds4.png)

2. Go to Storyboard view and you will now see the external resources added : API_BUSINESS_PARTNER

<br>![](/exercises/ex4/images/storyboardbupa.png)

## 3. Edit the Data Model with Graphical Modeller

1. Go to Storyboard, click on the downward arrow and open the graphical modeller

<br>![](/exercises/ex4/images/opengrapmod.png)

2. Click on Risks entity and select add relationship. Move the cursor to the white space to see the below dialog box.

<br>![](/exercises/ex4/images/addrelationship.png)

3. Add the new relationship as shown below:

<br>![](/exercises/ex4/images/newrelationship.png)

4. Updated data model will look as shown below:

<br>![](/exercises/ex4/images/modifieddm.png)

## 4. Edit the Service

1. Click on Service entity on storyboard and select open Graphical Modeller.

<br>![](/exercises/ex4/images/storyboardservice.png)

2. Add a new entity which opens a new projection to your service.

<br>![](/exercises/ex4/images/addprojection.png)

3. Select API_BUSINESS_PARTNER_A_BusinessPartner and uncheck <all properties> and choose the columns of your choice. In this example, we will choose 
1.BusinessPartner
2.FirstName
3.LastName

<br>![](/exercises/ex4/images/selectcolumns.png)

4. Newly updated service definition will look as follows.

<br>![](/exercises/ex4/images/newservicedefinition.png)

5. Updated storyboard with additon of business partner in data model & services.

<br>![](/exercises/ex4/images/updatedstoryboardbupa.png)

## Summary

You have now added Business Partner into your data model and the service definition.

Continue to - [Exercise 5 - Add UI to your application ](../ex5/README.md)


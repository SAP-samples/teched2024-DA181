# Exercise 3 - Add Business Partner as External Resource

In this exercise, you can add the business partner into your project by adding the S/4 system as the destination in SAP Business Technology Platform ( BTP) 

## Exercise 3.1 Create a S/4 HANA Destination in SAP Business Technology Platform

1. [Setup a Destination in SAP Business Technology Platform ( BTP )](https://help.sap.com/docs/business-rules/business-rules-capability-for-neo-environment/configure-destination-for-sap-s-4hana-cloud)

## Exercise 3.2 Add the S/4 system in your application

1. Go to SAP Build Code, Click on Service Center > Service > Select a Provider : SAP System > Under Services, you will now see the destination created in Exercise 3.1

<br>![](/exercises/ex3/images/adds4.png)

2. Go to Storyboard view and you will now see the external resources added : API_BUSINESS_PARTNER

<br>![](/exercises/ex3/images/storyboardbupa.png)

## Exercise 3.3 Edit the Data Model with Graphical Modeller

1. Go to Storyboard, click on the downward arrow and open the graphical modeller

<br>![](/exercises/ex3/images/opengrapmod.png)

2. Click on Risks entity and select add relationship.

<br>![](/exercises/ex3/images/addrelationship.png)

3. Add the new relationship as shown below:

<br>![](/exercises/ex3/images/newrelationship.png)

4. Updated data model will look as shown below:

<br>![](/exercises/ex3/images/modifieddm.png)

## Exercise 3.4 Edit the Service

1. Click on Service entity on storyboard and select open Graphical Modeller.

<br>![](/exercises/ex3/images/storyboardservice.png)

2. Add a new projection by clicking on new entity 

<br>![](/exercises/ex3/images/addprojection.png)

3. Select API_BUSINESS_PARTNER_A_BusinessPartner and uncheck <all properties> and choose the columns of your choice. In this example, we will choose BusinessPartner, FirstName, LastName.

<br>![](/exercises/ex3/images/selectcolumns.png)

4. Newly updated service definition will look as follows.

<br>![](/exercises/ex3/images/newservicedefinition.png)

5. Updated storyboard with additon of business partner in data model & services.

<br>![](/exercises/ex3/images/updatedstoryboardbupa.png)


## Summary

After completing this exercise, you have now added business partner and have uodated the data model & service definition with the new entity.

Continue to - [Exercise 4 - Add Application Logic](../ex4/README.md)

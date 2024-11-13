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

## Summary

After completing this exercise, you have now added business partner and have uodated the data model & service definition with the new entity.

Continue to - [Exercise 4.2 - Edit the Data Model & Service with Graphical Modeller](../ex4/ex4.2/README.md)

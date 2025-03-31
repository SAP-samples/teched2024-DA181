# Exercise 7 - Run your application 

In this exercise, we will configure the run configuration and set the database as SAP HANA Cloud, run the application and also see the SAP HANA Database explorer. 


## Exercise 7.1  Create a run configuration

1. Go to run configuration and click on the project launch.json
![alt text](/exercises/ex7/images/start_rungeneration.png)
- select SAP HANA Cloud as database. 
- Then select the HDI container which was created in the [Exercise 6 - Bind your application to an HDI Container ](exercises/ex6/)

![alt text](/exercises/ex7/images/image-1.png)

2. Select the OData option, and select mock data.

![alt text](/exercises/ex7/images/image.png)

3. Run the Application by clicking on either of two icons as shown below. 

![alt text](/exercises/ex7/images/image-3.png)

4.  This will automatically open a new tab in the browser. 

![alt text](/exercises/ex7/images/image-2.png)

## Exercise 7.2  Check the service details and explore the application

1. You can now also explor the data that was generated from API hub by clicking on service data details. 

![alt text](/exercises/ex7/images/image-4.png)

![alt text](/exercises/ex7/images/image-5.png)

2. Click on RiskApplication and click on go which shows the data.

<br>![](/exercises/ex7/images/riskapp.png)

3. you can edit the entry and assign a business partner id into a certain risk.

<br>![](/exercises/ex7/images/addbpid.png)

## Summary

You now have successfully built a full stack application with SAP HANA Cloud as database and Cloud Application Programming Model ( CAP ) with Fiori representation.

Check this bonus exercise to see the genAI capabilities with respect to HANA SQL [Exercise 8 - Inteligent SQL Assistant Console in Business Application Studios (BAS)  ](../ex8/README.md)




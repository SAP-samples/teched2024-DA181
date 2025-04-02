# Exercise 7 - Run your multi-target application for testing

In this exercise, we will configure the __run configuration__ and set the database as SAP HANA Cloud, in order to test to full multi-runtime target application stack
- Fiori UI
- Node.JS application runtime
- HANA Cloud database application runtime.


## Exercise 7.1  Create a run configuration

<br>__1.__ Open a run configuration view

- Click on __"Run configuration"-icon__ in the left-side activity bar
- click on the project __"launch.json"__-icon
![alt text](/exercises/ex7/images/start_rungeneration.png)  

- For Database, select __SAP HANA Cloud__. 
- Then select the __HDI container__ which was created in the [Exercise 6 - Bind your application to an HDI Container ](exercises/ex6/)
![alt text](/exercises/ex7/images/image-1.png)

- Select the __OData__ option, and select __"Mock data"__. Mock data will utilize the Business Partner-API from the sandbox S/4HANA Cloud PE system provided by the SAP Business Accelerator Hub.
![alt text](/exercises/ex7/images/image.png)

<br>__2.__ __Run the application__ for testing by _clicking_ on either of two __"Run"-icons__ as shown below. 
![alt text](/exercises/ex7/images/image-3.png)

<br>__3.__ This will automatically open the application's Fiori UI in a new tab in the browser. 

![alt text](/exercises/ex7/images/image-2.png)

<br><br>
## Exercise 7.2  Check the service details and explore the application

<br>__4.__ You can now also explore the data that was generated from Business Partner API (SAP Business Accelerator Hub) by clicking on service data details.   
![alt text](/exercises/ex7/images/image-4.png)
![alt text](/exercises/ex7/images/image-5.png)

<br>__5.__ Click on RiskApplication and click on go which shows the data.
- Note, the impact classification shown in the data view, is managed by the application logic we add in exercise 3.
<br>![](/exercises/ex7/images/riskapp.png)

<br>__6.__ you can edit the entry and assign a business partner id into a certain risk.
<br>![](/exercises/ex7/images/addbpid.png)

## Summary

You now have successfully built a full stack application with SAP HANA Cloud as database and Cloud Application Programming Model ( CAP ) with Fiori representation.

Check this bonus exercise to see the genAI capabilities with respect to HANA SQL [Exercise 8 - Inteligent SQL Assistant Console in Business Application Studios (BAS)  ](../ex8/README.md)




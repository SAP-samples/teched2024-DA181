# Exercise 6 - Bind your application to an HDI Container

In this exercise, we will create  a [SAP HANA Deployment Infrasturer ( HDI ) container](https://help.sap.com/docs/SAP_HANA_PLATFORM/3823b0f33420468ba5f1cf7f59bd6bd9/3ef0ee9da11440e4b01708455b8497a9.html) and bind that container to our project and deply the project to SAP HANA Cloud.

1. Go to Project Explorer, Click on Terminal. Enter the below command to add mta and hana. You will now see the project in the left bottom pane under SAP HANA Projects.

```shell
cds add mta
cds add hana
```

<br>![](/exercises/ex6/images/add.png)

2. Create a HDI container, Under SAP HANA Projects, click on the bind icon, select Bind to an HDI Container.

<br>![](/exercises/ex6/images/bind.png)

3. Click on Create a new service instance

<br>![](/exercises/ex6/images/create.png)

4. Enter the name of the HDI as per your choice or go ahead with the one generated and click enter.

<br>![](/exercises/ex6/images/name.png)

5. Click on Enable and do not ask again.

<br>![](/exercises/ex6/images/dia.png)


5. Now your HDI container service is created and is bound to your CAP project.

<br>![](/exercises/ex6/images/bound.png)

6. Click on the rocket icon, and deploy the SAP HANA Project.

<br>![](/exercises/ex6/images/deploy.png)


## Summary

You've now created a new HDI container and bound to your CAP Project

Continue to - [Exercise 7 - Run your application & view the data in SAP HANA Database Explorer ](exercises/ex7/)


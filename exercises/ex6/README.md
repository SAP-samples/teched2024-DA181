# Exercise 6 - Bind your application to an HDI Container & View the data in SAP HANA Database Explorer

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

6. Open the Database Explorer by clicking on the cubical icon.

<br>![](/exercises/ex6/images/dbx.png)

7. In the HDI container, you will see that the none of the artifacts are generated. Refer to the image below.

<br>![](/exercises/ex6/images/emptytables.png)

8. Go back to your SAP Build Code and deploy your project by clicking on the rocket icon, and this will deploy your project to your SAP HANA Cloud Instance

<br>![](/exercises/ex6/images/deploy.png)

## Exercise 6.2  Go to SAP HANA Database explorer and check the tables

1. Click on database exploerer icon under SAP HANA Projects, which will open the SAP HANA Database explorer view. 

<br>![](/exercises/ex7/images/dbx.png)

2. Generated artifacts are shown as below:

<br>![](/exercises/ex6/images/gen.png)

3. You can now see the initial data for the risk and mitigation is now deployed to the HDI container.

<br>![](/exercises/ex6/images/risk.png)

<br>![](/exercises/ex6/images/miti.png)












## Summary

You've now created a new HDI container and bound to your CAP Project. You can deploy the project to your SAP HANA Cloud instance and view the data in SAP HANA database explorer.

Continue to - [Exercise 7 - Run your application](../ex7/README.md)


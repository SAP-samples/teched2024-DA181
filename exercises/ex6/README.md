# Exercise 6 - Bind your application to an HDI Container and view the data in SAP HANA Database Explorer

In this exercise, you will create a [SAP HANA Deployment Infrastructure ( HDI ) container](https://help.sap.com/docs/SAP_HANA_PLATFORM/3823b0f33420468ba5f1cf7f59bd6bd9/3ef0ee9da11440e4b01708455b8497a9.html) and bind that container to our project and deploy the project to SAP HANA Cloud.

Note, as a prerequisite, you've setup a [SAP HANA Cloud Instance](https://developers.sap.com/group.hana-cloud-get-started-1-trial.html) incl. a cloud foundry environment, in case revisit the [pre-requistes check detaiks](/exercises/prerequistes/).

## Exercise 6.1  Login to your Cloud Foundry space and create a HDI container

<br>__1.__ _Login_ to __Cloud Foundry "environment"__ under your BTP subaccount and your __Cloud Foundry "space"__.  
- Click on __"CF login"-icon__ in the left-side activity bar
![alt text](/exercises/ex6/images/cf-login_icon.png)
  - or or alternative search for the CF login command in the top command search  ![alt text](/exercises/ex6/images/cf-login-cmd.png)   
- Specify the correct __"Cloud Foundry Endpoint URL"__ from your subaccount
- then select SSO Passcode and _click_ __"Open a new browser ..."__ to generate and copy a SSO passcode
- __Paste the Passcode__ and then click __"Sign in"__
![alt text](/exercises/ex6/images/cf_sso_passcode.png)  

- Now verify the __"Cloud Foundry Target environment Org ID"__ and __"CF Space"__
![alt text](/exercises/ex6/images/cf_target.png)    
  


<br>__2.__ The next step is to __prepare the Multi-Target Application definition__ (mta.yaml-file)  
Service- and target runtime-dependencies are declared within the mta.yaml-file, using some terminal commands, the file can be easily created and filled with the information about the SAP HANA and HDI container runtime.  

Go to Project Explorer, an __open a New Terminal__ window
- From top-menu in the left-side activity bar, select Terminal
- Click on __"New Terminal"__. 
<br>![](/exercises/ex6/images/new_terminal.png)
  
- Enter and execute the below commands to add mta and hana. 

```shell
cds add mta
```
```shell
cds add hana
```
- You will now see the project in the left bottom pane under SAP HANA Projects.
<br>![](/exercises/ex6/images/add.png)

<br>__3.__ Now __create__ and __bind__ your __HDI container__
- Under SAP HANA Projects, click on the __bind icon__, select Bind to an HDI Container.
![alt text](/exercises/ex6/images/image-1.png)

- Click on __"+Create a new service instance"__  
![alt text](/exercises/ex6/images/image-2.png)

- Enter the __name of the HDI container__ as per your choice or go ahead with the one generated and __press "enter"__ to confirm.  
![alt text](/exercises/ex6/images/image-3.png)

- Click on __"Enable and do not ask again"__.  
<br>![](/exercises/ex6/images/dia.png)

- Now your HDI container service is created and is bound to your CAP project.
![alt text](/exercises/ex6/images/image-4.png)

<br>__4.__ Open the Database Explorer by clicking on the cubical icon.

![alt text](/exercises/ex6/images/image-5.png)

<br>__5.__ In the SAP HANA Database Explorer, for the connected HDI container, you will see that the none of the (here table) artifacts are yet generated as they still require to be deployed to the container. Refer to the image below.
<br>![](/exercises/ex6/images/emptytables.png)

<br>__6.__ From SAP HANA Projects tree and deploy your HDI artifacts
- _Click_ on the __rocket icon__, and this will deploy your project to your SAP HANA Cloud Instance
<br>![](/exercises/ex6/images/deploy.png)
<br><br>
## Exercise 6.2  Go to SAP HANA Database explorer and check the tables

<br>__7.__ Click on database exploerer icon under SAP HANA Projects again, which will open the SAP HANA Database explorer view. 
<br>![](/exercises/ex7/images/dbx.png)

<br>__8.__ Generated (table) artifacts are now shown as below.  
However, the sample data that was generated before will not have been populated into the below tables. 
<br>![](/exercises/ex6/images/gen.png)

<br>__9.__ Populating tables with initial data.  
The test data that was generated in Exercise 2 (under /test in the project tree), will not be populated into the target HANA runtime as it is targeted for CF design-time testing purpose only.  
In order to add the data to the target HDI container
- create a new folder called under db folder
![alt text](/exercises/ex6/images/image-7.png)

- name the folder 'data' as shown below.
![alt text](/exercises/ex6/images/image-8.png)

- copy the csv files from the test-folder that is shown below.
![alt text](/exercises/ex6/images/image-6.png)

- paste the csv files in the newly created data folder ( db>data)
![alt text](/exercises/ex6/images/image-9.png)

- As a result, the folder structure should look as follows
![alt text](/exercises/ex6/images/image-10.png)


<br>__10.__ Now, the deploy to the HDI container again
![alt text](/exercises/ex6/images/image-13.png)

<br>__11.__ Once deployed successfully
- Navigate to SAP HANA Database explorer and review the data.
![alt text](/exercises/ex6/images/image-14.png)

- Review the tables and the data that is generated by the cds definitions and annotations.
![alt text](/exercises/ex6/images/image-15.png)

<br>__12.__ Explore __"initial data"__ within the project __Data Editor__ 
- Click on "Project-Overview"-icon in the left-side activity bar
- From the Risks entity in the data model, select __"Set Data"__, this will open the  __Data Editor__.  
- Note again, sample data is used for design-time testing purposes only, whereas initial data is also populated into the target runtime used for production.
![alt text](/exercises/ex6/images/Open-DataEditor.png)
![alt text](/exercises/ex6/images/image-11.png)
![alt text](/exercises/ex6/images/image-12.png)
## Summary

You've now created a new HDI container and bound to your CAP Project. You can deploy the project to your SAP HANA Cloud instance and view the data in SAP HANA database explorer.

Continue to - [Exercise 7 - Run your application](../ex7/README.md)


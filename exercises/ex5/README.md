# Exercise 5 - Add UI to your application

In this exercise, lets add a simple fiori UI to your risk management application.

# Ex 5.1 - create the basic UI from a template
1. Go to your storyboard, click on '+' icon under UI application.

<br>![](/exercises/ex5/images/createui.png)

2. Enter the details for UI application, select your Project service-object as data source

<br>![](/exercises/ex5/images/uiconfig1.png)

3. UI application type as Template based application

<br>![](/exercises/ex5/images/ui_template.png)

4. UI application template as List Report Page

<br>![](/exercises/ex5/images/uiconfig2.png)

5. Choose the main entity as Risks 

<br>![](/exercises/ex5/images/uiconfig3.png)

6. Click on finish. This step will add all the necessary libraries to your project which will take a couple of seconds.

You've now created the List report UI to your application.

# Ex 5.2 - Now modify the UI 

1. Open the page map under the UI Applications.

<br>![](/exercises/ex5/images/pagemap.png)

2. Click on the icon shown below. 

<br>![](/exercises/ex5/images/editpagemap.png)

3. In the columns list, delete the <strong>criticality</strong> column.

<br>![](/exercises/ex5/images/delcrit.png)

4. Select the column <strong>impact</strong> and on the right pane, scroll down to find the criticality property and set the value to criticality.

<br>![](/exercises/ex5/images/selcrit.png)

5. Add the criticality representation to with icon

<br>![](/exercises/ex5/images/criticon.png)

6. Go back to the page map as shown in step 2.

<br>![](/exercises/ex5/images/objpage.png)

7. Select the configure icon of object page section.

<br>![](/exercises/ex5/images/editobject.png)

8. Go to General Information > Form > Fields > Add Basic field.

<br>![](/exercises/ex5/images/editobject.png)

9. Add a new column BusinessPartner 

<br>![](/exercises/ex5/images/addbp.png)

10. Rename the BusinessPartner_BusinessPartner label to BusinessPartner 

<br>![](/exercises/ex5/images/renamebp.png)


## Summary

Now the UI of your application is ready
Continue to - [Bind your application to an HDI Container & View the data in SAP HANA Database Explorer](../ex6/README.md)


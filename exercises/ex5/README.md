# Exercise 5 - Add a UI to your application

In this exercise, let's add a simple Fiori UI to your risk management application.

## Exercise 5.1 - Create the basic UI from a template
<br>__1.__ Go to your __Storyboard__, _click_ on __'+'__ icon under __UI application__.
<br>![](/exercises/ex5/images/createui.png)

<br>__2.__ Enter the details for the UI application, 
- Display name: __RiskApplication__
- Application name: __riskapplication__
- select your project's __service-object__ as a data source
- then _click_ __"Next"__
<br>![](/exercises/ex5/images/uiconfig1.png)

<br>__3.__ Select __"UI application Type"__
- Click select __"Template-Based, Responsive Application"__
- then _click_ __"Next"__
<br>![](/exercises/ex5/images/ui_template.png)

<br>__4.__ Select the specific __"UI application Template"__
- Click select __"List Report Page"__
- then _click_ __"Next"__
<br>![](/exercises/ex5/images/uiconfig2.png)

<br>__5.__ Select the __"Data Objects"__
- Choose __"Risks"__ as the main entity 
<br>![](/exercises/ex5/images/uiconfig3.png)

<br>__6.__ Click on __Finish__. 
- This step will add all the necessary libraries to your project which will take a couple of seconds.
- You've now created the List report UI to your application.
<br><br>  
## Exercise 5.2 - Now modify the UI 
<br>__7.__ Click on __Open in Page Map__ under the UI Applications. __"Page Map"__ is a visual tool within the SAP Fiori Tools that provides a visual representation of an application’s pages, navigations, and service entities that it uses.
<br>![](/exercises/ex5/images/pagemap.png)

<br>__8.__  Click on the icon __Configure Page__ to edit the page's properties and settings. 
<br>![](/exercises/ex5/images/editpagemap.png)

<br>__9.__ In the columns list, delete the <strong>criticality</strong> column. SAP Fiori has the UI annotation of criticality which allows you to visually indicate if a value is negative, crtitical or positive via color-coding. There we dont need an additional column.
<br>![](/exercises/ex5/images/delcrit.png)

<br>__10.__ Select the column <strong>impact</strong> and on the right pane, scroll down to find the criticality property and set the value to criticality.Therefore __impact__ will now show the criticality threshold based on the risks.
<br>![](/exercises/ex5/images/selcrit.png)

<br>__11.__ Add the criticality representation with icon. This will add the icon next to the value which indicates the risk level visually. 
<br>![](/exercises/ex5/images/criticon.png)

<br>__12.__ Go back to the page map and Select the configure icon of object page section.
<br>![](/exercises/ex5/images/objpage.png)

<br>__13.__ Go to General Information > Form > Fields > Add Basic field. Here we can add the Business Partner to the UI of your application.
<br>![](/exercises/ex5/images/editobject.png)

<br>__14.__ Add a new column BusinessPartner. 
<br>![](/exercises/ex5/images/addbp.png)

<br>__15.__ Rename the BusinessPartner_BusinessPartner label to BusinessPartner. 
<br>![](/exercises/ex5/images/renamebp.png)


## Summary

Now the UI of your application is ready
Continue to - [Bind your application to an HDI Container & View the data in SAP HANA Database Explorer](../ex6/README.md)


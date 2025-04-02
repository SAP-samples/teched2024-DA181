# Exercise 2 - Create Data Model & Service with Joule

In this exercise, we will create a risk management application, helps organizations identify, assess, and track risks, while implementing mitigation strategies to minimize their impact.

## Exercise 2.1 Generate data model

<br>__1.__ _Open_ your project
-  __Click__ on __"Guide Center"__-icon in the left-side activity bar 
-  and _select_ __"Generate AI-Powered Development"__
<br>![](/exercises/ex2/images/guidecenter.png)

<br>__2.__ Within the __"Generate AI-Powered Development"__ view
-  _go_ to __"Data Model and Service Creation"__ and _Click_ on __"Open Joule"__  
<br>![](/exercises/ex2/images/openjoule.png)

<br>__3.__ Now __Joule__, the _generative AI-based code development copilot / assistant_ in SAP Build Code shows up on the left side and is now ready to use.
<br>![](/exercises/ex2/images/joule.png)

<br>__4.__ Next, __copy__ the below text to your Joule assistant to generate the data model and services.
```
Create a risk management app with risks and mitigations. Each risk may refer to one or more mitigations. Add realistic properties to each entity, risks should include a property impact and criticality which should be an integer. Impacts should be in range of 1 to 20000 dollars. Mitigation should include a counter
```

<br>__5.__ You will now __see__ the __generated data model__, as suggested by the Joule assistant according to your previous textual instruction.
<br>![](/exercises/ex2/images/jouledatamodel1.png)

<br>__6.__ The data model should include a __Risks__ and __Mitigations entity__ and respective __schema-, service- and annotations-cds files__.
- __Accept__ the data model if it reflects the files as shown below.
<br>![](/exercises/ex2/images/datamodel2.png)

<br>__7.__ _Open_ the Project __Storyboard__
- __Click__ on __"Project Overview"__-icon in the left-side activity bar
- From your project's context actions menue __"ooo"__, _select_ __Open Storyboard__ and you will see the newly generated data model and services.
<br>![](/exercises/ex2/images/open_storyboard.png)
<br>![](/exercises/ex2/images/storyboard_overview.png)

<br>__8.__ Review the generated cds-files from the project explorer
- __Click__ on __"Explorer"__-icon in the left-side activity bar
- Open and review the files from the project tree i.e ./db/schema.cds and ./srv/service.cds
<br>![](/exercises/ex2/images/project_explorer.png)
<br>![](/exercises/ex2/images/cdsfiles.png)

## Exercise 2.2 Add Sample Data using Joule

<br>__9.__ Go back to the __"Generate AI-Powered Development"__-view
- Go to __""Generate Sample Data"__ > __"Open Joule"__. 
- Select the entity context by _clicking_ __"#db/schema.cds"__ and then enter the below prompt text. By preceding the prompt with __#-some-object-context__ you can more specifically instruct the context of the Joule generation task.
![alt text](/exercises/ex2/images/image.png)

```
 Generate sample data
```
![alt text](/exercises/ex2/images/image-1.png)

<br>__10.__  __Accept__ the generated sample data, and you can see 2 csv files in the project test folder.
![alt text](/exercises/ex2/images/accept_sampledata.png)
<!--[alt text](/exercises/ex2/images/{FE7255FC-AF99-4224-A56A-47DA10941159}.png)-->
![alt text](/exercises/ex2/images/testdata_projecttree.png)  

<br>__11.__ Go to the __"Open Data Editor"__ and to review the generated sample data.  
Note, sample data generated to the /test/data-project folder, by default will not be copied to the SAP HANA runtime, however is only used within SAP Build Code itself.

![alt text](/exercises/ex2/images/open_editor-sampledata.png)  
![alt text](/exercises/ex2/images/{BA0BA16D-280F-499D-9CC0-46189648A513}.png)



## Summary

Joule lets you create CAP-based data entities and OData services with contextual sample data with just one text prompt. 

Continue to - [Exercise 3 - Add Application Logic](../ex3/README.md)


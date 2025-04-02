# Exercise 1 - Create a New Project
<br>__1.__ Navigate to the SAP Build lobby.

<br>__2.__ In the Lobby's __All Projects__ view, _click_ __Create__, and from the dropdown list _select_ __Create__ to create a new project from scratch.
<br>![](/exercises/ex1/images/1_create_from_lobby.png)

Alternatively to the __Create__ (from scratch) option, once could copy existing projects to your SAP Build workspace in the following ways:
- __Clone from Git__: to clone an existing project from a Git repository.
- __Add from Dev Space__: to add a project from an existing SAP Business Application studio dev space to your SAP Build Code tenant.    

<br>__3.__ Then in the build application dialog _Select_ the __Build an Application__ tile:
<br>![](/exercises/ex1/images/2_build_an_app.png)  

<br>__4.__ Next _Select_ the __SAP Build Code__ tile to develop your project in SAP Business Application Studio, the SAP Build Code development environment, leveraging the capabilities of the services included in SAP Build Code.
<br>![](/exercises/ex1/images/3_bc.png)

<br>__5.__ Select the __type of application__ you want to create.
   - Select __Full-Stack Application__ to create an application of type Full Stack with Productivity Tools. This will enable you to develop, extend, and deploy your app. 
<br>![](/exercises/ex1/images/4_types.png)


<br>__6.__ Enter a name for your project: e.g. __My_New_Project__ 

<br>__7.__ Select __Node__ (not Java) as your application development stack language.
<br>![](/exercises/ex1/images/5_development%20stack.png)

<br><br>
<br><br>__8.__ Select the __dev space__ where you want the project to reside, the one you created in the previous exercise.

- SAP Build Code recommends the dev space it deems most suitable, and it will automatically create a new one for you if you don’t already have one. If you have other dev spaces of the same type (for example, Full-Stack), you can select between them. If you want to create a different dev space, or a dev space or another type, go to the Dev Space Manager. See Working in the Dev Space Manager.

<br>![](/exercises/ex1/images/6_devspace.png)

<br><br>
<br>__9.__ Click __Create__.

- You can see the project being created in the project table view of the lobby. The creation of the project may take a few moments.
<br>![](/exercises/ex1/images/7_pending.png)
<br><br>

<br><br>
<br>__10.__ Once created you see a message stating that the project has been created successfully, click the project to open it.  
<br>![](/exercises/ex1/images/8_toaster.png)

__Success__, the project is now prepared.
You can now open in SAP Business Application Studio, the SAP Build Code development environment. 

## SAP Build Code IDE Configurations

Open the newly created project, right click on the activity bar and check if the below extensions are enabled.

<br>![](/exercises/ex1/images/10_activity_bar_list.png)

Additionally, to display the menu bar on the top. Click on the settings icon.

<br>![](/exercises/ex1/images/11_settings.png)

Search for __Menu Bar Visibility__ and click on the drop down and choose __Classic__

<br>![](/exercises/ex1/images/12_menu_bar_visibility.png)

Now your menu bar will look as shown below:

<br>![](/exercises/ex1/images/13_menu_bar.png)

Continue to - [Exercise 2 - Create Data Model & Service with Joule](../ex2/README.md)
# Exercise 3 - Add Application Logic

In this exercise, lets create a logic for the service with the help of Joule. We have our risks and mitigation as our entities, lets create a logic where if the impact of risk is greather than 10000, set the criticality of that risk to high or set it to warning.

<br>__1.__ Go to your __"Storyboard"__, 
- under the services, _select_ __"Open in Graphical Modeler"__, 
![](/exercises/ex3/images/{11492D55-E974-4F09-9F4F-49EB5FC6E34D}.png)  

- choose the risk entity and select add logic.
<br>![](/exercises/ex3/images/addlogic.png)

<br>__2.__ Once the dialog box appears, _select_ the __default entries__ and then _click_ __Add__
<br>![](/exercises/ex3/images/dialoglogic.png)

<br>__3.__ _Specify_ the __logic handlers__ as shown below
- Phase __"After"__
- Standard event __"Read"__

<br>![](/exercises/ex3/images/risklogicedit.png)

<br>__4.__ From the Open code editor-drop down, select __Application Logic__
<br>![](/exercises/ex3/images/applicationlogicopen.png)

<br>__5.__ Upon the initial object creation of the risk handling applicatin logic, let's use Joule assistant, to generate a more specific logic
- In the Joule prompt, enter the below text preceded with the context  #srv/code/risks-logic.js  
![](/exercises/ex3/images/joule_context.png)
```
if the impact of the current risk is greater than 10000 dollars set the criticality to 1 otherwise to 2
```
![](/exercises/ex3/images/{CCF7F81C-FF03-45D5-B2C8-E05903D3FB9C}.png)

<br>__6.__ You can now review and accept the AI-generated js-code, then the changes will be reflected in your project file.
<br>![](/exercises/ex3/images/joulesuggestion.png)

<br>__7.__ The code in the ./srv/code/risks-logic.js-file now looks as follows :
```javascript
/**
 * 
 * @After(event = { "READ" }, entity = "techedda181demoSrv.Risks")
 * @param {(Object|Object[])} results - For the After phase only: the results of the event processing
 * @param {Object} request - User information, tenant-specific CDS model, headers and query parameters
*/
module.exports = async function(results, request) {
    if (!results) return;

    const { Risks } = cds.entities;

    // Ensure results is an array
    if (!Array.isArray(results)) {
        results = [results];
    }

    for (const risk of results) {
        if (risk.impact !== undefined) {
            risk.criticality = risk.impact > 10000 ? 1 : 2;
        }
    }
};
```

## Summary

You've now added a service logic to your risk management application.

Continue to  [Exercise 4 - Add Business Partner Service & Connect your application to the Sandbox](../ex4/README.md)


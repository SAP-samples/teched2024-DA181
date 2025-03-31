# Exercise 3 - Add Application Logic

In this exercise, lets create a logic for the service with the help of Joule. We have our risks and mitigation as our entities, lets create a logic where if the impact of risk is greather than 10000, set the criticality of that risk to high or set it to warning.

1. Go to your storyboard, under the services, open the graphical modeller, choose the risk entity and select add logic.

![](/exercises/ex3/images/{11492D55-E974-4F09-9F4F-49EB5FC6E34D}.png)

<br>![](/exercises/ex3/images/addlogic.png)

2. Once the dialog box appears, select the defaults and click __Add__

<br>![](/exercises/ex3/images/dialoglogic.png)

3. Specify the logic handlers as shown below
- Phase __after__
- Standard even __read__

<br>![](/exercises/ex3/images/risklogicedit.png)

4. From the Open code editor-drop down, select __Application Logic__

<br>![](/exercises/ex3/images/applicationlogicopen.png)

5. Enter the below prompt text with context in Joule  
Note, upon typing __#__ in the Joule prompt, a context is suggested, select #srv/code/risks-logic.js  
![](/exercises/ex3/images/joule_context.png)
```
if the impact of the current risk is greater than 10000 dollars set the criticality to 1 otherwise to 2
```
![](/exercises/ex3/images/{CCF7F81C-FF03-45D5-B2C8-E05903D3FB9C}.png)

6. You can now review & accept the suggested code and the new changes will be reflected in your project.

<br>![](/exercises/ex3/images/joulesuggestion.png)

7. The ./srv/code/risks-logic.js-code now looks as follows :
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


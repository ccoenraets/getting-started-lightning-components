---
layout: module
title: Part 9&#58; Interacting with the Salesforce1 Application
---

In this module, you use a standard event to interact with the Salesforce1 application. When a user clicks a marker on the map, you load the default Salesforce1 details view for the selected account.

## What you will learn

- Use force events to interact with the Salesforce1 application

## Steps

1. In the developer console, open the **AccountMap** component.

1. Click **CONTROLLER** (upper right corner in the code editor).

1. In the **accountsLoaded** function, add a click event handler to markers as follows:

    ```
    L.marker(latLng, {account: account}).addTo(map).on('click', function(event) {
        helper.navigateToDetailsView(event.target.options.account.Id);
    });
    ```

    ### Code Highlights:
    - When the marker is clicked, invoke the navigateToDetailsView().
    - You create the navigateToDetailsView function below.


1. Click **File** > **Save** to save the controller.

1. Click **HELPER** (upper right corner in the code editor), and define a new **navigateToDetailsView** function implemented as follows:

    ```
    ({
        navigateToDetailsView : function(accountId) {
            var event = $A.get("e.force:navigateToSObject");
            event.setParams({
                "recordId": accountId
            });
            event.fire();
        }
    })
    ```

    ### Code Highlights:
    - You first get an instance of the **force:navigateToSObject** event.
    - You then set the event's **recordId** parameter to the selected account id.
    - Finally, you **fire** the event so that the Salesforce1 app can catch it and navigate to the default Salesforce1 details view for the selected account.

1. Click **File** > **Save** to save the file.

1. Go back to the Salesforce1 app and reload **Account Locator** from the menu to see the changes. Click a marker on the map: the Salesforce1 details view for the selected account should load automatically.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="using-lightning-events2.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="next.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>

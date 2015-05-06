---
layout: module
title: Part 8&#58; Using Events to Center the Map
---

In this module, you create a Lightning event used by AccountListItem to notify AccountMap that an account has been selected in the list. In response to this event, AccountMap centers the map on the selected account.

## What you will learn

- Communicate between components using events
- Create custom Lightning Events
- Trigger Lightning events
- Register event listeners and handle Lightning events

## Step 1: Create the AccountSelected Event

1. In the Developer Console, click **File** > **New** > **Lightning Event**. Specify **AccountSelected** as the bundle name and click **Submit**.

1. Implement the event as follows:

    ```
    <aura:event type="APPLICATION">
        <aura:attribute name="account" Type="Account"/>
    </aura:event>
    ```
    ### Code Highlights:
    - The event holds a single argument: the selected account

1. Click **File** > **Save** to save the file.

## Step 2: Trigger the AccountSelected Event

1. In the developer console, go back to the **AccountListItem** component.

2. Add an **onclick** handler to the anchor tag:

    ```
    <a onclick="{!c.accountSelected}">{!v.account.Name}</a>
    ```

1. Click **File** > **Save** to save the component.

1. Click **CONTROLLER** (upper right corner in the code editor).

1. Define an **accountSelected** function defined as follows:

    ```
    ({
        accountSelected : function(component) {
            var event = $A.get("e.c:AccountSelected");
            event.setParams({"account": component.get("v.account")});
            event.fire();
        }
    })
    ```

    ### Code Highlights:
    - You first get an instance of the **AccountSelected** event.
    - You then set the event's **account** parameter to the selected account.
    - Finally, you **fire** the event so that registered listeners can catch it.

1. Click **File** > **Save** to save the controller.


## Step 3: Handle the AccountSelected Event

1. In the developer console, go back to the **AccountMap** component.

1. Add the following event registration immediately after the AccountsLoaded handler declaration:

    ```
    <aura:handler event="c:AccountSelected" action="{!c.accountSelected}"/>

    ```

1. Click **File** > **Save** to save the component.

1. Click **CONTROLLER** (upper right corner in the code editor), and define a new accountSelected function positioned after accountsLoaded and implemented as follows:

    > Make sure you add a comma after the accountsLoaded function block.

    ```
    accountSelected: function(component, event, helper) {
        // Center the map on the account selected in the list
        var map = component.get('v.map');
        var account = event.getParam("account");
        map.panTo([account.Location__Latitude__s, account.Location__Longitude__s]);
    }
    ```

1. Click **File** > **Save** to save the controller.

1. Go back to the Salesforce1 app and reload **Account Locator** from the menu to see the changes. Select an account in the list: the map should automatically center on the selected account.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="using-lightning-events.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="using-salesforce1-events.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>

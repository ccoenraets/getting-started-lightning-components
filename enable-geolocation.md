---
layout: module
title: Part 2&#58; Enabling Geolocation on the Account Object
---
Before you can display your accounts on a map, you need to be able to store their location. In this module, you add a geolocation field to the Account object and enter some sample data.

## Step 1: Add a Geolocation Field to the Account Object

1. In **Setup**, select **Build** > **Customize** > **Accounts** > **Fields**

2. In the **Account Custom Fields & Relationships** section, click **New**, and create a **Location** field defined as follows:
    - Data Type: **Geolocation**
    - Field Label: **Location**
    - Latitude and Longitude Display Notation: **Decimal**
    - Decimal Places: **7**
    - Field Name: **Location**

    Click **Next**, **Next**, **Save**

## Step 2: Enter Sample Data

1. Click the **Accounts** tab in the Sales application and enter a couple of accounts with their location information. For example, pretending your company does business with the hospitality industry, enter the following hotels:
  - Marriott Marquis (Latitude: 37.785143 Longitude: -122.403405)
  - Hilton Union Square (Latitude: 37.786164 Longitude: -122.410137)
  - Hyatt (Latitude: 37.794157 Longitude: -122.396311)

    > Make sure you include the minus sign when entering the longitude.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="setup-environment.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="create-apex-controller.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>

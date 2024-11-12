# Parceldealz Conversion Tracking Pixel

This repository provides a Google Tag Manager (GTM) custom tag template to integrate the Parceldealz tracking pixel for tracking conversions, enabling advertisers to track coupon-related conversions by sending data to the Parceldealz API. The pixel URL returns a 1x1 transparent GIF in all cases.

## Pixel Endpoint

**Endpoint**: `GET https://coupons.parceldealz.com/pixel`

### Query Parameters

- **advertiser_id**
- **order_id**
- **coupon_code**
- **order_value** (optional)

## Google Tag Manager Template Setup

### Tip before you start!

Perform a test purchase in the Google Tag Manager Preview mode. Follow the exact steps until a transaction is finished. In the Google Tag Manager Tag Assistant you will find a summary with all the steps (pages/events) from the checkout. In each of these steps you can see which variables are available and which data is available in the datalayer. This will help you with adding the correct trigger and variables during installation of the tag.

### Step 1: Add a new tag

Go to "Tags", click on "New", then click on “Tag Configuration” and select “Custom Image”.

![Add new tag](/img/add-tag.png)

### Step 2: Provide tracking pixel URL

In the Image URL field enter the following URL:

```
https://coupons.parceldealz.com/pixel?advertiser_id=XX&order_id={{order_id}}&coupon_code={{coupon_code}}&order_value={{order_value}}
```

where

- `advertiser_id`: your advertiser ID. _This value is fixed and does not need to be provided by GTM Data Layer_
- `order_id`: unique transaction or order ID. _Replace variable name inside {{}} with corresponding GTM Data Layer variable._
- `coupon_code`: coupon/discount code used in the transaction. _Replace variable name inside {{}} with corresponding GTM Data Layer variable._
- `order_value`: order amount (optional). _Replace variable name inside {{}} with corresponding GTM Data Layer variable._

![Provide pixel URL](/img/provide-url.png)

If needed variables and/or GTM Data Layer are not set up, please see [GTM documentation](https://developers.google.com/tag-platform/tag-manager/datalayer) for help with Data Layer and variable creation.

### Step 3: Set the trigger

**The trigger needs to only fire once on the order confirmation or thank you page.**

![Set trigger](/img/choose-trigger-1.png)

Select an existing trigger (if you created one previously) or build a new trigger.

Trigger Type: Page View - DOM Ready or sometimes even better; Page View - Window Loaded. Event based (purchase) triggers are also a good option in some situations. _Make sure the trigger fires at the order confirmation or thank you page at the same time the order data is available in the datalayer as well._

It's also possible to add a trigger based on a (custom) event or any other action. More information about Google Tag Manager Triggers [here](https://support.google.com/tagmanager/answer/7679316?hl=en).

![Set trigger](/img/choose-trigger-2.png)

### Step 4: Save and verify

Name Tag, for example “ParcelDealz - Conversion Tag” and click the save button.

Publish your edited workspace. After publishing, please contact your ParcelDealz manager for testing the conversion pixel.

### Extra Tip

Perform the test in the Google Tag Manager Preview mode. This way you can easily troubleshoot possible errors and also check if all (new) variables are working correctly.

## Example Pixel Call

Below is an example of the pixel request made by this GTM template:

```
https://coupons.parceldealz.com/pixel?advertiser_id=123&order_id=456789&coupon_code=SAVE20&order_value=100.00
```

## License

This repository is licensed under the Apache 2.0 License. See `LICENSE` for more information.

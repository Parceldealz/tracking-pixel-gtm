# Parceldealz Conversion Tracking Pixel

This repository provides a Google Tag Manager (GTM) custom tag template to integrate the Parceldealz tracking pixel for tracking conversions, enabling advertisers to track coupon-related conversions by sending data to the Parceldealz API. The pixel URL returns a 1x1 transparent GIF in all cases.

## Pixel Endpoint

**Endpoint**: `GET https://coupons.parceldealz.com/pixel`

### Query Parameters

- **advertiser_id**: The unique identifier for the advertiser associated with the conversion.
- **order_id**: The unique identifier for the order or transaction.
- **coupon_code**: The coupon code applied during the transaction.
- **order_value** (optional): The monetary value of the transaction.

## Google Tag Manager Template Setup

1. **Import Template**: In Google Tag Manager, go to **Templates** > **Tag Templates** and import this custom tag template.
2. **Create a New Tag**:
   - Navigate to **Tags** > **New**.
   - Choose the **Parceldealz Conversion Tracking Pixel** template.
3. **Configure the Tag Fields**:
   - Set the required fields: `advertiser_id`, `order_id`, and `coupon_code`.
   - Optionally, you may also set `order_value`.
4. **Set Triggers**: Add appropriate triggers to determine when the conversion tag should fire (e.g., a successful order or checkout completion).
5. **Preview and Publish**: Use the GTM Preview mode to test the tag. Once confirmed, publish the changes.

### Example Pixel Call

Below is an example of the pixel request made by this GTM template:

```
https://coupons.parceldealz.com/pixel?advertiser_id=123&order_id=456789&coupon_code=SAVE20&order_value=100.00
```

## Notes

- Ensure all required parameters are set and populated before firing the tag.
- Check GTM Preview mode to verify that the tag is firing correctly and that all required parameters are passed.
- If `order_value` is not applicable, it can be omitted from the request.
- This pixel is designed to return a 1x1 transparent GIF.

## License

This repository is licensed under the Apache 2.0 License. See `LICENSE` for more information.

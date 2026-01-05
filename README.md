# WooCommerce Min/Max Quantity by Stock (Custom Rules for WoodMart)

This code snippet enforces **custom minimum, maximum, and step quantities** in WooCommerce based on the **product stock**, with optional **automatic adjustment** and **WoodMart-compatible AJAX handling**.


## Features

1. **Set Min/Max Quantity by Stock**

   * Products with stock ≥ 2:

     * Minimum: 2
     * Maximum: current stock
     * Step: 2
   * Products with stock = 1:

     * Minimum = Maximum = 1
2. **Validate Cart Quantities**

   * Displays error messages if the user adds quantities outside the allowed range.
3. **Auto-Adjust Cart Quantities**

   * Adjusts quantities automatically to the closest valid number (step-based).
4. **WoodMart AJAX & Frontend Support**

   * Disables “+” buttons when quantity reaches max
   * Re-applies rules after AJAX updates (mini-cart, cart page, WooCommerce fragments)
   * Ensures the quantity input reflects the correct min/max and step


## Installation

1. Add the **PHP snippet** to your **child theme `functions.php`** or a **custom plugin**.
2. The JS for WoodMart is included in the snippet and automatically hooks to `wp_footer`.
3. No additional configuration is needed.


## How It Works (Short Overview)

* Uses `woocommerce_quantity_input_args` to define **min, max, step, and default input values**.
* Validates cart items on `woocommerce_check_cart_items` to prevent invalid quantities.
* Adjusts quantities dynamically on `woocommerce_before_calculate_totals` to match allowed steps.
* WoodMart AJAX handlers ensure buttons are disabled when the quantity reaches max stock, and quantity input is readonly if needed.


## Stock Rules Example

| Stock | Min | Max         | Step | Behavior                         |
| ----- | --- | ----------- | ---- | -------------------------------- |
| ≥ 2   | 2   | Stock value | 2    | User can only add multiples of 2 |
| 1     | 1   | 1           | 1    | Quantity fixed at 1              |


## Compatibility

* WooCommerce
* WoodMart theme (AJAX-enabled cart and mini-cart supported)
* Works with AJAX cart updates and fragments
* PHP 7.4+ recommended


## Notes

* The JS uses `setInterval` as a fallback to handle dynamic updates in case WooCommerce/WoodMart AJAX misses a refresh.
* Cart validation prevents users from bypassing quantity rules with manual input.
* Step enforcement ensures users cannot order odd quantities when only even steps are allowed.


## Author

**Md Mamun Miah / Webzlo**

* [Webzlo](https://webzlo.com)


## License

MIT — free to use, modify, and distribute.


**One-line Summary:**
Custom WooCommerce quantity rules by stock, fully compatible with WoodMart theme and AJAX carts.

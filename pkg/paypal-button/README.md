# Paypal Button
Paypal button that takes payment via PayPal gateway

[Demo](https://humble.js.org/pkg/paypal-button/demo)

## Install

```
yarn add @humblejs/paypal-button
```

## Props

| **Name** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `env`    | string (`sandbox`, `production`)      | NO | `production` |
| `client`    | shape(`sandbox`, `production`)<br><br>Client key for relevant environment | YES | |
| `amount`    | number<br><br>Amount to be charged for the payment | YES | |
| `currency`    | string (`AUD`, `USD`, `CAD`, `EUR`, `NZD`, `GBP`) | NO | `AUD` |
| `commit`    | bool<br><br> | NO | true |
| `onSuccess`    | func<br><br>Callback when payment was successful | YES | |
| `onError`    | func<br><br>Callback when payment errored | YES | |
| `onCancel`    | func<br><br>Callback when payment was cancelled | YES | |
| `shape`    | string (`pill`, `rect`)<br><br>Shape of button | NO | `pill` |
| `size`    | string (`medium`, `large`, `responsive`)<br><br>Size of button | NO | `medium` |
| `layout`    | string (`horizontal`, `vertical`)<br><br>Layout of button | NO | `vertical` |
| `color`    | string (`gold`, `blue`, `silver`, `white`, `black`)<br><br>Color of button | NO | `gold` |

## How to use

1. Create new paypal app in the [dashboard](https://developer.paypal.com/developer/applications/) and obtain Client ID and secret.
2. Pass the client ID to this component and select the correct environment (`sandbox` or `production`)
3. Store `secret` key on the server side securely
4. Implement `onSuccess` for the component and verify payment on the server side
5. Mark payment as successful only after server verification

This component has been fully tested with sandbox account.

## Server-side Verification
You will need PayPal Node.js SDK on the server

```
yarn add @paypal/checkout-server-sdk
```

```
// paypal-client.js
const checkoutSDK = require('@paypal/checkout-server-sdk');

function environment() {
   const clientId = process.env.PAYPAL_CLIENT_ID;
   const clientSecret = process.env.PAYPAL_CLIENT_SECRET;
   return new checkoutSDK.core.SandboxEnvironment(clientId, clientSecret);
}
function client() {
  return new checkoutSDK.core.PayPalHttpClient(environment());
}
```

And use this client
```
const checkoutSDK = require('@paypal/checkout-server-sdk');
const payPalClient = require('./client');

const orderID = ''; // payment ID or order ID

const request = new checkoutSDK.orders.OrdersGetRequest(orderID);

payPalClient.client().execute(request).then((order) => {
  console.log('Payment successful. Amount:', order.result.purchase_units[0].amount.value, JSON.stringify(f));
}).catch((err) => {
  console.error('error', err);
});
```

Now you may also save the order by order ID

The response look like following
```
{
	"statusCode": 200,
	"headers": {
		...
	},
	"result": {
		"id": "PAYID-LTH25ZY54J279526F323870C",
		"intent": "CAPTURE",
		"purchase_units": [{
			"amount": {
				"currency_code": "AUD",
				"value": "0.03",
				"breakdown": {
					"item_total": {
						"currency_code": "AUD",
						"value": "0.03"
					},
					"shipping": {
						"currency_code": "AUD",
						"value": "0.00"
					},
					"handling": {
						"currency_code": "AUD",
						"value": "0.00"
					},
					"insurance": {
						"currency_code": "AUD",
						"value": "0.00"
					},
					"shipping_discount": {
						"currency_code": "AUD",
						"value": "0.00"
					},
					"discount": {
						"currency_code": "AUD",
						"value": "0.00"
					}
				}
			},
			"payee": {
				"email_address": "humblejs-demo@zuhd.org",
				"merchant_id": "46T8JZE4VNF4A"
			},
			"description": "",
			"shipping": {
				"name": {
					"full_name": "test buyer"
				},
				"address": {
					"address_line_1": "1 Cheeseman Ave Brighton East",
					"admin_area_2": "Melbourne",
					"admin_area_1": "Victoria",
					"postal_code": "3001",
					"country_code": "AU"
				}
			},
			"payments": {
				"captures": [{
					"id": "0LM87903F7245960E",
					"status": "COMPLETED",
					"amount": {
						"currency_code": "AUD",
						"value": "0.03"
					},
					"final_capture": true,
					"seller_protection": {
						"status": "ELIGIBLE",
						"dispute_categories": ["ITEM_NOT_RECEIVED", "UNAUTHORIZED_TRANSACTION"]
					},
					"seller_receivable_breakdown": {
						"gross_amount": {
							"currency_code": "AUD",
							"value": "0.03"
						},
						"paypal_fee": {
							"currency_code": "AUD",
							"value": "0.03"
						},
						"net_amount": {
							"currency_code": "AUD",
							"value": "0.00"
						}
					},
					"links": [{
						"href": "https://api.sandbox.paypal.com/v2/payments/captures/0LM87903F7245960E",
						"rel": "self",
						"method": "GET"
					}, {
						"href": "https://api.sandbox.paypal.com/v2/payments/captures/0LM87903F7245960E/refund",
						"rel": "refund",
						"method": "POST"
					}, {
						"href": "https://api.sandbox.paypal.com/v2/checkout/orders/7F536828UP127432R",
						"rel": "up",
						"method": "GET"
					}],
					"create_time": "2019-05-06T03:50:21Z",
					"update_time": "2019-05-06T03:50:21Z"
				}]
			}
		}],
		"payer": {
			"name": {
				"given_name": "test",
				"surname": "buyer"
			},
			"email_address": "payments-buyer@zuhd.org",
			"payer_id": "4DDJQTGYTCLS2",
			"phone": {
				"phone_number": {
					"national_number": "0368558274"
				}
			},
			"address": {
				"country_code": "AU"
			}
		},
		"update_time": "2019-05-06T03:50:21Z",
		"links": [{
			"href": "https://api.sandbox.paypal.com/v2/checkout/orders/PAYID-LTH25ZY54J365924F323870C",
			"rel": "self",
			"method": "GET"
		}],
		"status": "COMPLETED"
	}
}
```

<p align="center">
<img src="https://www.acommerce.asia/wp-content/uploads/acommerce-logo-210x30-1.png"/>

## QA Engineer Test Challenges
There are 2 challenges included
1. Test Case Design
2. Test Automation

## SECTION 1 - Test Case Design

aCommerce provide End-to-End Ecommerce service. The first is "Gift With Purchase(GWP)" to manage promotion on the Marketplace. 
The second is "Order Fulfillment service" to processing the salesorder from Marketplace

#### Requirements
The feature indicates the promotion when sales orders arriving.
Those sales orders coming in the campaign period and buy product matching with conditions the system will be applied a gift into sales order automatically.
The promotion eligibility should be applying after discount, and before any fees. 

Let's say 11.11 Campaign is coming! There are 3 promotions on campaign day
1. Promotion A 
- Condition: Buy Product X Get Product Y Free
- Promotion Period: 00.00 - 05:59
- Product X, Final Price per 1 qty = 250B

2. Promotion B 
- Condition: Buy X with minimum purchase of 1,000B Get Y Free 
- Promotion Period: 06.00 - 11:59
- Product X, Final Price per 1 qty = 250B

3. Promotion C
- Condition: Buy X with order’s minimum product quantity of 5 items Get Y Free
- Promotion Period: 12.00 - 23:59
- Product X, Final Price per 1 qty = 250B

##### Discount
- Every Sales Orders amount >= 1,000B get 10% discount from Marketplace automatically
##### Delivery Fee
- Sales Orders amount < 500B , Charges delivery fee 50B every kilometers
- Sales Orders amount >= 500B , Excluded delivery fee

##### Example 1
```
Customer buy "Product X" with 1 quntity when 11-11-2021 02:00AM
- Product X (250B) * 1 qty = 250B
- No Discount
- Included Delivery fee (+50)
- Sale Order amount = 300B

Expected = The system will be applied “Promotion A” to sales order.
```

##### Example 2
```
Customer buy "Product X" with 5 quntity when 11-11-2021 09:30AM 
- Product X (250B) * 5 qty = 1,250
- Sales Order amount(1,250) - 10% Discount (125) = 1,125
- Excluded delivery fee

Expected = the system will be applied “Promotion C” to sales order.
```

#### CHALLENGES!
You are the QA who is testing this feature. What scenarios need to be tested. 
1. Create a test case (Prefer excel or google sheet format). You can design your own test case template.
2. Estimation resource and time to testing. (Let's say you have to implement automation testing from this test case)

## SECTION 2 - Test Automation
#### 2.1 Automation Test RESTful API

This API is for external services to retrieve the latest quantity that aCommerce allocated stock to the Marketplace.
```
Method: GET
URL: https://fulfillment.api.acommerce.asia/channel/lazada-th/allocation/merchant/334?page=1&page_size=100
Headers: 
- X-Subject-Token:{{token_id}}
```
  
Example Response
```
  Response Code: 200
  [
    {
        "qty": "0",
        "sku": "SKU0001",
        "updatedTime": "2021-08-05T10:20:12.053457Z"
    },
    {
        "qty": "0",
        "sku": "SKU0002",
        "updatedTime": "2021-08-05T10:20:12.093643Z"
    },
    {
        "qty": "0",
        "sku": "SKU0003",
        "updatedTime": "2021-08-05T10:20:12.121762Z"
    },
    {
        "qty": "0",
        "sku": "SKU0004",
        "updatedTime": "2021-08-05T10:20:12.150911Z"
    },
    {
        "qty": "0",
        "sku": "SKU0005",
        "updatedTime": "2021-08-05T10:20:12.180933Z"
    },
    ....
    ..
    .
]
```
  
#### CHALLENGES!
1. Create automation test script to testing this API Endpoint at least 10 test cases (Prefer Robot Framework tools). Otherwise, you can choose any tools that you prefer
2. After finished the quiz push the code to GitHub repository and send us a link.

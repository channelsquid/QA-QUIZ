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

#### ** CHALLENGES! **
You are the QA who is testing this feature. What scenarios need to be tested. 
1. Create a test case (Prefer excel or google sheet format). You can design your own test case template.
2. Estimation resource and time to testing. (Let's say you have to implement automation testing from this test case)

## SECTION 2 - Test Automation
#### 2.1 Automation Test RESTful API

This API is for external services to retrieving the latest quantity that aCommerce allocated stock to the Marketplace.
```
Method: GET
URL: https://fulfillment.api.acommerce.asia/channel/lazada-th/allocation/merchant/1338?page=1&page_size=100```
Headers: 
- X-Subject-Token:{{token_id}}
```
This API require headers token. The token will be generate and send to you when quiz starting.

#### ** CHALLENGES! **
1. Create automation test script that be able to execution to get the value from this API endpoint.
2. Find sku “9120160422001” from response and write the value to log file or log console as below format.
3. Write the result on log file or log console.

Example Result in Log Console
```
|sku           | qty |
|--------------|-----|
|9120160422001 | 1   |
```

### 2.2 Automation Test UI
This UI represents stock synchronization between aCommerce and Marketplace.

#### Instruction
1. Go to URL `https://portal.acommerce.asia/channel/inventories`
2. Selecting Channel `Lazada Thailand`
3. Selecting Seller `OMRON THAILAND`
4. Change "Allocation Result" from "Failed" -> "Success"
5. Copy first Product SKU that displayed on the table
6. Search that sku on Product SKU seach box
7. Click search

Example Result the final screen
<PIC>


#### ** CHALLENGES! **
1. Create automated test script that can be executed follow the instruction.

---

#### FINISHED CHALLENGES
1. Write the README file and describe how to set up your automation testing tools(Prefer Robot Framwork) and how to execute (Depends on your tools). Please describe the step seems you have to share this code to anyone who without a background.
2. Push the automation code to GitHub repository and send us a link.

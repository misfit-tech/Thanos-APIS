# Thanos-APIS
BASE_URL(sandbox) = "Please request for base url when you need",
BASE_URL(live) = "Please request for base url when you need"


Authentication API

* **URL**: `{BASE_URL}/api/v1/login/`

* **Method:** `POST`

*  **Headers:**
	 ``
*  **Request Parameters:**
```
 requires :username, type: String
 requires :password, type: String
```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 200,
   "message": "Successfully logged in.",
   "data": {
       "token": "eyJhbGciOiJIUzI1NiJ9.IiQyYSQxMiRZZFdkOTdUZ0ZXUFBLUUNuUGpvbG9PZnV3dnBhamhZMXQ3VnF4TFNjUUlEZ0ZtM2ZoSEhOZSI.zUWGkcZm-55SrECarrNHH64EApY7Iz3MHyCmHM04X5M",
       "expired_at": "2022-10-18T18:04:50.489+06:00"
   }
}
 

```


* **Error Response:**
* **Code:** `406`
  	* **If username or password not matched then:**
  	* **Content:**
```json
{
   "success": false,
   "status_code": 406,
   "message": "Invalid username or password",
   "data": []
}

```
Product Create API

* **URL**: `{BASE_URL}/api/v1/products`

* **Method:** `POST`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
{
    "product":{
        "unique_id":  "f0d2301e-4705-4d66-8a73-f73023909d63",
        "title": "Product Title",
        "description":"Product Description",
        "sku_type":1,
        "company":"ABC Company",
        "product_type": "Trending",
        "brand_unique_id":"97263fb6-5960-4eb2-aac1-f36bc2437026",
        "leaf_category_unique_id":"62d2d56b-e205-48df-ba33-4452757e3c0e",
        "attribute_set_unique_id":"46fbd572-0bee-485f-9e76-3bd7be8067b1",
        "variants_attributes":[
            {
                "unique_id":"84c2b5e5-b07e-416f-abd4-7fc4326ca5a9",
                "price_consumer":500,
                "consumer_discount":50,
                "product_attribute_value_unique_ids":["0607527a-01eb-4540-8c9b-f31b55e4841f"]
            }
            
        ]
        
    }
             
}

```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 201,
   "message": "Product Created Successfully"
}

```


* **Error Response:**
* **Code:** `422`
  	* **Unable to create product:**
  	* **Content:**
```json
{
   "success": false,
   "status_code": 406,
   "message": "Brand not found",
   "data": []
}

```

Product Update API

* **URL**: `{BASE_URL}/api/v1/products/:id`

* **Method:** `PUT`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
`{"product": {
     "title": "Nokia N97", 
     "bn_title": "Nokia N97",
     "slug": 'N01',
     "company": 'Nokia',
     "bn_company": 'নোকিয়া',
     "brand_id": '1',
     "product_type": 'Private',
     "hero_image_file": file,
     "is_emi_available": true,
     "tenures": [3, 6, 9],
     "bundle_variants": [
        {
            sku_id: 34 //
            quantity: 2 //float
        }
     ]
     "variants_attributes": [
          {
           "sku": "63", //string
           "weight": "56", //float
           "height": "85", //float
           "width": "45", //float
           "depth": "23", //float
           "weight_unit": "23", //string
           "height_unit": "23", //string
           "width_unit": "23", //string
           "depth_unit": "23", //string
           "primary": false,
           "price_consumer": 120,
           "sku_case_dimension": "12*12",
           "sku_case_width": "12*12", //float
           "sku_case_length": "12*12", //float
           "sku_case_height": "12*12", //float
           "sku_case_width_unit": "12*12", //string
           "sku_case_length_unit": "12*12", //string
           "sku_case_height_unit": "12*12", //string
           "case_weight_unit": "12*12", //string
           "case_weight": "12200", //string
           "consumer_discount": 10.0,
           "vat_tax": 100.0,
           "discount_type": "Discount",
           "moq": 100.0,
           "code_by_supplier": "kajs",
           "product_attribute_value_ids": [1, 2, 3],
       }
     ],
     "frequently_asked_questions_attributes": [
           {
            "question": "Valid quesstions?",
            "bn_question": "Valid quesstions?",
            "answer": "Valid quesstions?",
            "bn_answer": "Valid quesstions?",
           }
     ],
   "category_ids": [1, 2, 3],
   "product_type_ids": [1, 2, 3],
   "leaf_category_id": 100,
   "product_attribute_images_attributes": [
       {
        "product_attribute_value_id": 1,
        "is_default": false,
        "images_file": []
       }
     ]
 }}`

```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 201,
   "message": "Product Update Successfully"
}

```


* **Error Response:**
* **Code:** `422`
  	* **Unable to create product:**
  	* **Content:**
```json
{
   "success": false,
   "status_code": 406,
   "message": "Unable to create product due to brand must exit",
   "data": []
}

```
### Purchase Order Create
___

* **URL :** `BASE_URL + /api/v1/purchase_orders`
* **Method :** `POST`
* **Header :** `Authorization: auth-token`
* **URL Params :**

```json
{
   "purchase_order": {
      "variants":[
         {
            "variant_id": 1, //integer
            "supplier_id": 10, //integer
            "quantity": 100, //integer
	    "unique_id": fc10b881-d9a0-4ab1-a6fd-a102db188f49, //string
	    "po_id": 1
         },
         {
            "variant_id": 2, //integer
            "supplier_id": 10, //integer
            "quantity": 10 //integer
	    "unique_id": fc10b881-d9a0-4ab1-a6fd-a102db188f48, //string
	    "po_id": 2
         }
      ]
   }
}

```
* **Success Response**
 * **Code :**`201`
 * **Content :**
```json
{
   "success": true,
   "status_code": 201,
   "message": "Successfully purchase order created",
   "data": {}
}
```
* **Error Response**
 * **Code :**`422`
 * **Content :**
```json
{
   "success": false,
   "status_code": 422,
   "message": "Unable to create purchase order",
   "data": {}
}
```
### Assign Product to Supplier
___

* **URL :** `BASE_URL + /api/v1/suppliers/:id/assign_products`
* **Method :** `POST`
* **Header :** `Authorization: auth-token`
* **URL Params :**

```json
{
   "suppliers_variants":[
        {
          "variant_id": 1, //integer
          "supplier_price": 1050, //decimal
        },
        {
          "variant_id": 1234, //integer
          "supplier_price": 130, //decimal
        }
   ]
}

```
* **Success Response**
 * **Code :**`201`
 * **Content :**
```json
{
   "success": true,
   "status_code": 201,
   "message": "Successfully created supplier variant",
   "data": {}
}
```
* **Error Response**
 * **Code :**`422`
 * **Content :**
```json
{
   "success": false,
   "status_code": 422,
   "message": "Unable to create supplier variant",
   "data": {}
}
```

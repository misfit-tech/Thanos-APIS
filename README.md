# Thanos-APIS
BASE_URL(development) = "http://api-v2.shopoth.shop/3ps/thanos",
BASE_URL(sandbox) = "Please request for base url when you need",
BASE_URL(live) = "Please request for base url when you need"


Authentication API

* **URL**: `{BASE_URL}/api/v1/login/`

* **Method:** `POST`

*  **Headers:**
	 ``
*  **Request Parameters:**
```
 {
    "username": "shopoth@gmail.com",
    "password": "123456"
}
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
   "message": "Product Created Successfully",
   "data": {
        "product_id": 4051,
        "unique_id": "d965c19f-99e8-4586-aa76-d8ba1d888d8c",
        "variants": [
            {
                "variant_id": 3239,
                "unique_id": "84c2b5e5-b07e-416f-abd4-7fc4326ca5a9"
            }
        ]
    }
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

* **URL**: `{BASE_URL}/api/v1/products/:unique_id`

* **Method:** `PUT`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
{
    "product":{
        "title": "Product Title",
        "description":"Product Description",
        "company":"ABC Company",
        "product_type": "Trending",
        "brand_unique_id":"97263fb6-5960-4eb2-aac1-f36bc2437026",
        "leaf_category_unique_id":"62d2d56b-e205-48df-ba33-4452757e3c0e"
        
    }
             
}

```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 200,
   "message": "Product Update Successfully"
}

```


* **Error Response:**
* **Code:** `406`	
* **Content:**
```json
{
   "success": false,
   "status_code": 406,
   "message": "Brand not found",
   "data": {}
}
```
* **Code:** `422`	
* **Content:**
```json
{
   "success": false,
   "status_code": 422,
   "message": "Unable to update product due to, {{error_message}}",
   "data": {}
}

```

### Assign Product to Supplier
___

* **URL :** `BASE_URL + /api/v1/suppliers/assign_products`
* **Method :** `POST`
* **Header :** `Authorization: auth-token`
* **URL Params :**

```json
{
    "supplier_unique_id": "f0d2301e-4705-4d66-8a73-f73023909d63",
    "suppliers_variants": [
    {
        "variant_unique_id": "a1104fc0-f4e4-4b19-82ea-d84b2a3824ae",
        "supplier_price": 50
    },
    
    {
        "variant_unique_id": "a1104fc0-f4e4-4b19-82ea-d84b2a38",
        "supplier_price": 60
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
   "message": "Successfully assigned product",
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
   "message": "Unable to assign product to supplier_id: #{supplier.id} due to, #{error.message}",
   "data": {}
}
```


Product Delete API

* **URL**: `{BASE_URL}/api/v1/products/:unique_id`

* **Method:** `DELETE`

*  **Headers:**
	 `Authorization: token`

```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 200,
   "message": "Product Deleted Successfully"
}

```


* **Error Response:**
* **Code:** `404`	
* **Content:**
```json
{
   "success": false,
   "status_code": 404,
   "message": "Product not found",
   "data": {}
}
```
* **Code:** `422`	
* **Content:**
```json
{
   "success": false,
   "status_code": 422,
   "message": "Unable to delete product due to, {{error_message}}",
   "data": {}
}

```

Variant Add API

* **URL**: `{BASE_URL}/api/v1/variants`

* **Method:** `POST`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
{
    "variant":{
        "product_unique_id":  "f0d2301e-4705-4d66-8a73-f73023909d63",
	"variant_unique_id":"84c2b5e5-b07e-416f-abd4-7fc4326ca5a9",
	"price_consumer":500,
	"consumer_discount":50,
	"product_attribute_value_unique_ids":["0607527a-01eb-4540-8c9b-f31b55e4841f"]
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
   "message": "Variant Added Successfully",
   "data": {
        "product_id": 4051,
        "product_unique_id": "d965c19f-99e8-4586-aa76-d8ba1d888d8c",
        "variants": [
            {
                "variant_id": 3239,
                "unique_id": "84c2b5e5-b07e-416f-abd4-7fc4326ca5a9"
            }
        ]
    }
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
   "message": "Unable to add variant due to, {{error_message}}",
   "data": []
}

```

Variant Update API

* **URL**: `{BASE_URL}/api/v1/variants/{{unique_id}}`

* **Method:** `PUT`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
{
    "variant":{
	"price_consumer":500,
	"consumer_discount":50,
	"product_attribute_value_unique_ids":["0607527a-01eb-4540-8c9b-f31b55e4841f"]
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
   "message": "Variant Added Successfully",
   "data": {
         "variant_id": 3245,
        "variant_unique_id": "498f9932-0d74-401c-a5fd-fee46bdbad59",
        "product_id": 4041,
        "product_unique_id": "9742fc4e-3c41-42e6-8fe2-00ef9b50788c",
        "consumer_discount": "50.0",
        "price_consumer": "500.0"
    }
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
   "message": "Unable to update variant due to, {{error_message}}",
   "data": []
}

```

Variant Delete API

* **URL**: `{BASE_URL}/api/v1/variants/:unique_id`

* **Method:** `DELETE`

*  **Headers:**
	 `Authorization: token`

```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 200,
   "message": "Variant Deleted Successfully"
}

```


* **Error Response:**
* **Code:** `404`	
* **Content:**
```json
{
   "success": false,
   "status_code": 404,
   "message": "Variant not found",
   "data": {}
}
```
* **Code:** `422`	
* **Content:**
```json
{
   "success": false,
   "status_code": 422,
   "message": "Unable to delete variant due to, {{error_message}}",
   "data": {}
}

```

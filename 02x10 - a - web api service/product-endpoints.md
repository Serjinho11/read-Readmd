# Product Endpoints

## 1. Get All Products

### Request

```
GET /api/product
```

### Response

```
200 OK

[
	{
		"id": 1,
		"columnId": 12,
		"name": "product1"
		"price": 12.4,
		"quantity": 5
	},
	{
		"id": 2,
		"columnId": 13,
		"name": "product2"
		"price": 1.45,
		"quantity": 20
	}
]
```



## 2. Get One Product

### Request

```
GET /api/product/{id}
```

### Response

If product exists:

```
200 OK

{
	"id": 1,
	"columnId": 12,
	"name": "product1"
	"price": 12.4,
	"quantity": 5
}
```

If product does not exist:

```
404 Not Found
```



## 3. Update Product

### Request

```
PUT /api/product/{id}

{
	"columnId": 12,
	"name": "product1"
	"price": 12.4,
	"quantity": 5
}
```

### Response

If product exists:

```
200 OK
```

If product does not exist:

```
404 Not Found
```



## 4. Add Product

### Request

```
POST /api/product

{
	"columnId": 12,
	"name": "product1"
	"price": 12.4,
	"quantity": 5
}
```

### Response

If product was successfully added:

```
201 Created

{
	"id": 20
}
```



## 5. Delete Product

### Request

```
DELETE /api/product/{id}
```

### Response

```
200 OK
```


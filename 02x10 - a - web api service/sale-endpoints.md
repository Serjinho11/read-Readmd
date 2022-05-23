# Product Endpoints

## 1. Get Sales

### Request

```
GET /api/sales?startdate={start-date}&endtdate={end-date}
```

**Note**: startdate and enddate are optional. If they are not provided, return sales for the last 30 days.

### Response

```
200 OK

[
	{
		"date": 2020-05-30T16:26:49Z,
		"productName": "product1"
		"price": 12.4,
		"paymentType": "card"
	},
	{
		"date": 2020-05-30T16:30:27Z,
		"productName": "product6"
		"price": 1.5,
		"paymentType": "cash"
	}
]
```



## 2. Delete Sales

### Request

```
DELETE /api/sales?startdate={start-date}&endtdate={end-date}
```

**Note**: startdate and enddate are mandatory.

### Response

If delete action was successful:

```
200 OK
```

If mandatory parameters were not provided:

```
400 Bad Request
```

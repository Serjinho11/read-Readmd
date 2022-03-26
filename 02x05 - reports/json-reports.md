# Json Reports

## Serialization

We need the ability to generate the reports serialized in JSON format, too.

The format must be configurable from the configuration file (appSettings section).

## 1. Json Stock Report

### Formatting Styles

- Indentation: 4 spaces

- Encoding: utf-8

### Example

```json
[
    {
        "Name": "Chocolate",
        "Quantity": 20
    },
    {
        "Name": "Chips",
        "Quantity": 5
    },
    {
        "Name": "Still Water",
        "Quantity": 9
    }
]
```

### File Name

The report file name must respect the following pattern:

```
Stock Report - yyyy MM dd HHmmss.json
```



## 2. Json Sales Report

### Formatting Styles

- Indentation: 4 spaces

- Encoding: utf-8

### Example

```json
[
    {
        "Date": "2020-10-14T23:24:51.3099176",
        "Name": "Chips",
        "Price": 5.0,
        "PaymentMethod": "cash payment"
    },
    {
        "Date": "2020-10-15T08:15:08.9965213",
        "Name": "Chips",
        "Price": 5.0,
        "PaymentMethod": "cash payment"
    },
    {
        "Date": "2020-10-15T10:21:28.8286402",
        "Name": "Still Water",
        "Price": 2.0,
        "PaymentMethod": "cash payment"
    }
]
```

### File Name

The report file name must respect the following pattern:

```
Sales Report - yyyy MM dd HHmmss.json
```



## 3. Json Volume Report

### Formatting Styles

- Indentation: 4 spaces

- Encoding: utf-8

### Example

```json
{
    "StartTime": "2020-09-15T00:00:00+03:00",
    "EndTime": "2020-10-16T00:00:00+03:00",
    "Products": [
        {
            "Name": "Chips",
            "Quantity": 2
        },
        {
            "Name": "Still Water",
            "Quantity": 1
        }
    ]
}
```

### File Name

The report file name must respect the following pattern:

```
Volume Report - yyyy MM dd HHmmss.json
```
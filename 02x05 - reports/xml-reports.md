# XML Reports

## 1. XML Stock Report

In order to make an inventory of the existing products, we need to generate a report containing the following information:

- Product Name
- Quantity

### Formatting Styles

The xml file should respect the following formatting styles:

- Indentation: 1 tab

- Encoding: utf-8

**Note:** The indentation is important in this case. The client needs to import the xml in an old tool that is limited to read only xml indented with tabs.

### Example

```xml
<?xml version="1.0" encoding="utf-8"?>
<StockReport xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
	<Product>
		<Name>Chocolate</Name>
		<Quantity>20</Quantity>
	</Product>
	<Product>
		<Name>Chips</Name>
		<Quantity>5</Quantity>
	</Product>
	<Product>
		<Name>Still Water</Name>
		<Quantity>9</Quantity>
	</Product>
</StockReport>
```

### File Name

The report file name must respect the following pattern:

```
Stock Report - yyyy MM dd HHmmss.xml
```



## 2. XML Sales Report

For the monthly bookkeeping activity, we need to generate a sales report containing the following information:

- Date

- Product Name

- Price

- Payment Method

### Formatting Styles

- Indentation: 1 tab

- Encoding: utf-8

**Note:** The indentation is important in this case. The client needs to import the xml in an old tool that is limited to read only xml indented with tabs.

### Example

```xml
<?xml version="1.0" encoding="utf-8"?>
<SalesReport xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
	<Sale>
		<Date>2020-10-14T23:24:51.3099176</Date>
		<Name>Chips</Name>
		<Price>5</Price>
		<PaymentMethod>cash payment</PaymentMethod>
	</Sale>
	<Sale>
		<Date>2020-10-15T08:15:08.9965213</Date>
		<Name>Chips</Name>
		<Price>5</Price>
		<PaymentMethod>cash payment</PaymentMethod>
	</Sale>
	<Sale>
		<Date>2020-10-15T10:21:28.8286402</Date>
		<Name>Still Water</Name>
		<Price>2</Price>
		<PaymentMethod>cash payment</PaymentMethod>
	</Sale>
</SalesReport>
```

### File Name

The report file name must respect the following pattern:

```
Sales Report - yyyy MM dd HHmmss.xml
```



## 3. Xml Volume Report

In order to analyse the sales and be able to adapt to the market, we need to generate a volume sales report containing the following information:

- Start Date

- End Date

- For each sold product:
  - Product Name
  - Quantity

### Formatting Styles

- Indentation: 1 tab

- Encoding: utf-8

**Note:** The indentation is important in this case. The client needs to import the xml in an old tool that is limited to read only xml indented with tabs.

### Example

```xml
<?xml version="1.0" encoding="utf-8"?>
<VolumeReport xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
	<StartTime>2020-09-15T00:00:00+03:00</StartTime>
	<EndTime>2020-10-16T00:00:00+03:00</EndTime>
	<Sales>
		<Product>
			<Name>Chips</Name>
			<Quantity>2</Quantity>
		</Product>
		<Product>
			<Name>Still Water</Name>
			<Quantity>1</Quantity>
		</Product>
	</Sales>
</VolumeReport>
```

### File Name

The report file name must respect the following pattern:

```
Volume Report - yyyy MM dd HHmmss.xml
```



## 4. Suggestions

### Additional Entities

For each type of report, additional entities can be created to format the data according to the serialization requirements.

### Repositories

For each type of report, a repository class can be created that accepts just to add reports. These repositories will store the data into files and not into the database. 

 
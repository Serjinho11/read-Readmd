# Reports

In order to analyse the profitability of the vending machine, an admin must be able to generate different types of reports.

## Report Types

- Stock Report (product, current quantity)
- Sales Report (date, product, price, payment-method)
- Volume Report (product, total quantity)

The Sales and Volume reports must be generated for a specific range of days.

The Stock report is generated for the moment of the request.

## Report Format

The application must be able to generate XML or JSON reports.

There is no need to select the report format at runtime, but it must be configurable from the configuration file.

For details regarding the XML reports see this document:

- [XML Reports](xml-reports.md)

For details regarding the JSON reports see this document:

- [JSON Reports](json-reports.md)
# Zip the reports

In the Vending Machine application there are three use cases that generate csv reports.

Update the use cases to zip the csv reports before saving them to disk (in a zip file).

### 1.1.1    Hints

Try creating a new stream class (`ZippedReportFileStream`) that inherits from `Stream` and can be a wrapper over the zip file from the disk. Inside this new stream class, on the constructor, open the real zip stream.

Remember to implement `IDisposable` interface.
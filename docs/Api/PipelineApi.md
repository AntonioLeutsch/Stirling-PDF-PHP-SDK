# OpenAPI\Client\PipelineApi

Automated document processing workflows for complex multi-stage business operations.  This endpoint group enables organizations to create sophisticated document processing workflows that combine multiple operations into streamlined, repeatable processes.  Common use cases: • Invoice processing, legal document review, and healthcare records standardization • Government processing, educational content preparation, and publishing automation • Contract lifecycle management and approval processes  Business applications: • Automated compliance reporting, large-scale migration, and quality assurance • Archive preparation, content delivery, and document approval workflows  Operational scenarios: • Scheduled batch processing and event-driven document processing • Multi-department coordination and business system integration  Target users: Business process managers, IT automation specialists, and organizations requiring consistent, repeatable document processing workflows.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**handleData()**](PipelineApi.md#handleData) | **POST** /api/v1/pipeline/handleData | Execute automated PDF processing pipeline |


## `handleData()`

```php
handleData($file_input, $json): \SplFileObject
```

Execute automated PDF processing pipeline

This endpoint processes multiple PDF files through a configurable pipeline of operations. Users provide files and a JSON configuration defining the sequence of operations to perform. Input:PDF Output:PDF/ZIP Type:MIMO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\PipelineApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = array('/path/to/file.txt'); // \SplFileObject[] | The input files
$json = 'json_example'; // string | Pipeline configuration in JSON format containing name and operations list

try {
    $result = $apiInstance->handleData($file_input, $json);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PipelineApi->handleData: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject[]**| The input files | |
| **json** | **string**| Pipeline configuration in JSON format containing name and operations list | |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/zip`, `image/png`, `image/jpeg`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

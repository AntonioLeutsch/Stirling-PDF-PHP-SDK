# OpenAPI\Client\AnalysisApi

Document analysis and information extraction services for content intelligence and insights.  This endpoint group provides analytical capabilities to understand document structure, extract information, and generate insights from PDF content for automated processing.  Common use cases: • Document inventory management and content audit for compliance verification • Quality assurance workflows and business intelligence analytics • Migration planning, accessibility evaluation, and document forensics  Business applications: • Legal discovery, financial document review, and healthcare records analysis • Academic research, government processing, and publishing optimization  Operational scenarios: • Large-scale profiling, migration assessment, and performance optimization • Automated quality control and content strategy development  Target users: Data analysts, QA teams, administrators, and business intelligence professionals requiring detailed document insights.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getAnnotationInfo()**](AnalysisApi.md#getAnnotationInfo) | **POST** /api/v1/analysis/annotation-info | Get annotation information |
| [**getBasicInfo()**](AnalysisApi.md#getBasicInfo) | **POST** /api/v1/analysis/basic-info | Get basic PDF information |
| [**getDocumentProperties()**](AnalysisApi.md#getDocumentProperties) | **POST** /api/v1/analysis/document-properties | Get PDF document properties |
| [**getFontInfo()**](AnalysisApi.md#getFontInfo) | **POST** /api/v1/analysis/font-info | Get font information |
| [**getFormFields()**](AnalysisApi.md#getFormFields) | **POST** /api/v1/analysis/form-fields | Get form field information |
| [**getPageCount()**](AnalysisApi.md#getPageCount) | **POST** /api/v1/analysis/page-count | Get PDF page count |
| [**getPageDimensions()**](AnalysisApi.md#getPageDimensions) | **POST** /api/v1/analysis/page-dimensions | Get page dimensions for all pages |
| [**getSecurityInfo()**](AnalysisApi.md#getSecurityInfo) | **POST** /api/v1/analysis/security-info | Get security information |


## `getAnnotationInfo()`

```php
getAnnotationInfo($file_input, $file_id): object
```

Get annotation information

Returns count and types of annotations. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getAnnotationInfo($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getAnnotationInfo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getBasicInfo()`

```php
getBasicInfo($file_input, $file_id): object
```

Get basic PDF information

Returns page count, version, file size. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getBasicInfo($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getBasicInfo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDocumentProperties()`

```php
getDocumentProperties($file_input, $file_id): object
```

Get PDF document properties

Returns title, author, subject, etc. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getDocumentProperties($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getDocumentProperties: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFontInfo()`

```php
getFontInfo($file_input, $file_id): object
```

Get font information

Returns list of fonts used in the document. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getFontInfo($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getFontInfo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFormFields()`

```php
getFormFields($file_input, $file_id): object
```

Get form field information

Returns count and details of form fields. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getFormFields($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getFormFields: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPageCount()`

```php
getPageCount($file_input, $file_id): object
```

Get PDF page count

Returns total number of pages in PDF. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getPageCount($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getPageCount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPageDimensions()`

```php
getPageDimensions($file_input, $file_id): object
```

Get page dimensions for all pages

Returns width and height of each page. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getPageDimensions($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getPageDimensions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSecurityInfo()`

```php
getSecurityInfo($file_input, $file_id): object
```

Get security information

Returns encryption and permission details. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AnalysisApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getSecurityInfo($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnalysisApi->getSecurityInfo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**object**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

# OpenAPI\Client\FilterApi

Document content filtering and search operations for information discovery and organization.  This endpoint group enables intelligent content discovery and organization within document collections for content-based processing and information extraction.  Common use cases: • Legal discovery, research organization, and compliance auditing • Content moderation, academic research, and business intelligence • Quality assurance and content validation workflows  Business applications: • Contract analysis, financial review, and healthcare records organization • Government processing, educational curation, and IP protection  Workflow scenarios: • Large-scale processing, automated classification, and information extraction • Document preparation for further processing or analysis  Target users: Legal professionals, researchers, compliance officers, and organizations requiring intelligent document content discovery and organization.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**containsImage()**](FilterApi.md#containsImage) | **POST** /api/v1/filter/filter-contains-image | Checks if a PDF contains an image |
| [**containsText()**](FilterApi.md#containsText) | **POST** /api/v1/filter/filter-contains-text | Checks if a PDF contains set text, returns true if does |
| [**fileSize()**](FilterApi.md#fileSize) | **POST** /api/v1/filter/filter-file-size | Checks if a PDF is a set file size |
| [**pageCount()**](FilterApi.md#pageCount) | **POST** /api/v1/filter/filter-page-count | Checks if a PDF is greater, less or equal to a setPageCount |
| [**pageRotation()**](FilterApi.md#pageRotation) | **POST** /api/v1/filter/filter-page-rotation | Checks if a PDF is of a certain rotation |
| [**pageSize()**](FilterApi.md#pageSize) | **POST** /api/v1/filter/filter-page-size | Checks if a PDF is of a certain size |


## `containsImage()`

```php
containsImage($page_numbers, $file_input, $file_id): \SplFileObject
```

Checks if a PDF contains an image

Input:PDF Output:Boolean Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilterApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->containsImage($page_numbers, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilterApi->containsImage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `containsText()`

```php
containsText($page_numbers, $text, $file_input, $file_id): \SplFileObject
```

Checks if a PDF contains set text, returns true if does

Input:PDF Output:Boolean Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilterApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$text = 'text'; // string | The text to check for
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->containsText($page_numbers, $text, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilterApi->containsText: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **text** | **string**| The text to check for | [default to &#39;text&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `fileSize()`

```php
fileSize($comparator, $file_size, $file_input, $file_id): \SplFileObject
```

Checks if a PDF is a set file size

Input:PDF Output:Boolean Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilterApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$comparator = 'comparator_example'; // string | The comparison type, accepts Greater, Equal, Less than
$file_size = 0; // int | Size of the file in bytes
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->fileSize($comparator, $file_size, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilterApi->fileSize: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **comparator** | **string**| The comparison type, accepts Greater, Equal, Less than | |
| **file_size** | **int**| Size of the file in bytes | [default to 0] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `pageCount()`

```php
pageCount($comparator, $page_count, $file_input, $file_id): \SplFileObject
```

Checks if a PDF is greater, less or equal to a setPageCount

Input:PDF Output:Boolean Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilterApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$comparator = 'comparator_example'; // string | The comparison type, accepts Greater, Equal, Less than
$page_count = 0; // int | Count
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->pageCount($comparator, $page_count, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilterApi->pageCount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **comparator** | **string**| The comparison type, accepts Greater, Equal, Less than | |
| **page_count** | **int**| Count | [default to 0] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `pageRotation()`

```php
pageRotation($comparator, $rotation, $file_input, $file_id): \SplFileObject
```

Checks if a PDF is of a certain rotation

Input:PDF Output:Boolean Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilterApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$comparator = 'comparator_example'; // string | The comparison type, accepts Greater, Equal, Less than
$rotation = 0; // int | Rotation in degrees
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->pageRotation($comparator, $rotation, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilterApi->pageRotation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **comparator** | **string**| The comparison type, accepts Greater, Equal, Less than | |
| **rotation** | **int**| Rotation in degrees | [default to 0] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `pageSize()`

```php
pageSize($comparator, $standard_page_size, $file_input, $file_id): \SplFileObject
```

Checks if a PDF is of a certain size

Input:PDF Output:Boolean Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilterApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$comparator = 'comparator_example'; // string | The comparison type, accepts Greater, Equal, Less than
$standard_page_size = 'A4'; // string | Standard Page Size
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->pageSize($comparator, $standard_page_size, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilterApi->pageSize: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **comparator** | **string**| The comparison type, accepts Greater, Equal, Less than | |
| **standard_page_size** | **string**| Standard Page Size | [default to &#39;A4&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

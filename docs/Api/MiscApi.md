# OpenAPI\Client\MiscApi

Specialized utilities and supplementary tools for enhanced document processing workflows.  This endpoint group provides utility operations that support core document processing tasks and address specific workflow needs in real-world scenarios.  Common use cases: • Document optimization for bandwidth-limited environments and storage cost management • Document repair, content extraction, and validation for quality assurance • Accessibility improvement and custom processing for specialized needs  Business applications: • Web publishing optimization, email attachment management, and archive efficiency • Mobile compatibility, print production, and legacy document recovery  Operational scenarios: • Batch processing, quality control, and performance optimization • Troubleshooting and recovery of problematic documents  Target users: System administrators, document specialists, and organizations requiring specialized document processing and optimization tools.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addAttachments()**](MiscApi.md#addAttachments) | **POST** /api/v1/misc/add-attachments | Add attachments to PDF |
| [**addPageNumbers()**](MiscApi.md#addPageNumbers) | **POST** /api/v1/misc/add-page-numbers | Add page numbers to a PDF document |
| [**addStamp()**](MiscApi.md#addStamp) | **POST** /api/v1/misc/add-stamp | Add stamp to a PDF file |
| [**autoSplitPdf()**](MiscApi.md#autoSplitPdf) | **POST** /api/v1/misc/auto-split-pdf | Auto split PDF pages into separate documents |
| [**decompressPdf()**](MiscApi.md#decompressPdf) | **POST** /api/v1/misc/decompress-pdf | Decompress PDF streams |
| [**extractHeader()**](MiscApi.md#extractHeader) | **POST** /api/v1/misc/show-javascript | Grabs all JS from a PDF and returns a single JS file with all code |
| [**extractHeader1()**](MiscApi.md#extractHeader1) | **POST** /api/v1/misc/auto-rename | Extract header from PDF file |
| [**extractImageScans()**](MiscApi.md#extractImageScans) | **POST** /api/v1/misc/extract-image-scans | Extract image scans from an input file |
| [**extractImages()**](MiscApi.md#extractImages) | **POST** /api/v1/misc/extract-images | Extract images from a PDF file |
| [**flatten()**](MiscApi.md#flatten) | **POST** /api/v1/misc/flatten | Flatten PDF form fields or full page |
| [**metadata()**](MiscApi.md#metadata) | **POST** /api/v1/misc/update-metadata | Update metadata of a PDF file |
| [**optimizePdf()**](MiscApi.md#optimizePdf) | **POST** /api/v1/misc/compress-pdf | Optimize PDF file |
| [**overlayImage()**](MiscApi.md#overlayImage) | **POST** /api/v1/misc/add-image | Overlay image onto a PDF file |
| [**processPdfWithOCR()**](MiscApi.md#processPdfWithOCR) | **POST** /api/v1/misc/ocr-pdf | Process a PDF file with OCR |
| [**removeBlankPages()**](MiscApi.md#removeBlankPages) | **POST** /api/v1/misc/remove-blanks | Remove blank pages from a PDF file |
| [**repairPdf()**](MiscApi.md#repairPdf) | **POST** /api/v1/misc/repair | Repair a PDF file |
| [**replaceAndInvertColor()**](MiscApi.md#replaceAndInvertColor) | **POST** /api/v1/misc/replace-invert-pdf | Replace-Invert Color PDF |
| [**scannerEffect()**](MiscApi.md#scannerEffect) | **POST** /api/v1/misc/scanner-effect | Apply scanner effect to PDF |
| [**unlockPDFForms()**](MiscApi.md#unlockPDFForms) | **POST** /api/v1/misc/unlock-pdf-forms | Remove read-only property from form fields |


## `addAttachments()`

```php
addAttachments($attachments, $file_input, $file_id): \SplFileObject
```

Add attachments to PDF

This endpoint adds attachments to a PDF. Input:PDF, Output:PDF Type:MISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$attachments = array('/path/to/file.txt'); // \SplFileObject[] | The image file to be overlaid onto the PDF.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->addAttachments($attachments, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->addAttachments: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **attachments** | **\SplFileObject[]**| The image file to be overlaid onto the PDF. | |
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

## `addPageNumbers()`

```php
addPageNumbers($page_numbers, $font_size, $font_type, $position, $starting_number, $file_input, $file_id, $custom_margin, $pages_to_number, $custom_text): \SplFileObject
```

Add page numbers to a PDF document

This operation takes an input PDF file and adds page numbers to it. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$font_size = 12; // float | Font size for page numbers
$font_type = 'font_type_example'; // string | Font type for page numbers
$position = 56; // int | Position: 1-9 representing positions on the page (1=top-left, 2=top-center, 3=top-right, 4=middle-left, 5=middle-center, 6=middle-right, 7=bottom-left, 8=bottom-center, 9=bottom-right)
$starting_number = 1; // int | Starting number for page numbering
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$custom_margin = 'medium'; // string | Custom margin: small/medium/large/x-large
$pages_to_number = 'all'; // string | Which pages to number (e.g. '1,3-5,7' or 'all')
$custom_text = '{n}'; // string | Custom text pattern. Available variables: {n}=current page number, {total}=total pages, {filename}=original filename

try {
    $result = $apiInstance->addPageNumbers($page_numbers, $font_size, $font_type, $position, $starting_number, $file_input, $file_id, $custom_margin, $pages_to_number, $custom_text);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->addPageNumbers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **font_size** | **float**| Font size for page numbers | [default to 12] |
| **font_type** | **string**| Font type for page numbers | |
| **position** | **int**| Position: 1-9 representing positions on the page (1&#x3D;top-left, 2&#x3D;top-center, 3&#x3D;top-right, 4&#x3D;middle-left, 5&#x3D;middle-center, 6&#x3D;middle-right, 7&#x3D;bottom-left, 8&#x3D;bottom-center, 9&#x3D;bottom-right) | |
| **starting_number** | **int**| Starting number for page numbering | [default to 1] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **custom_margin** | **string**| Custom margin: small/medium/large/x-large | [optional] [default to &#39;medium&#39;] |
| **pages_to_number** | **string**| Which pages to number (e.g. &#39;1,3-5,7&#39; or &#39;all&#39;) | [optional] [default to &#39;all&#39;] |
| **custom_text** | **string**| Custom text pattern. Available variables: {n}&#x3D;current page number, {total}&#x3D;total pages, {filename}&#x3D;original filename | [optional] [default to &#39;{n}&#39;] |

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

## `addStamp()`

```php
addStamp($page_numbers, $stamp_type, $font_size, $rotation, $opacity, $position, $override_x, $override_y, $custom_margin, $file_input, $file_id, $stamp_text, $stamp_image, $alphabet, $custom_color): \SplFileObject
```

Add stamp to a PDF file

This endpoint adds a stamp to a given PDF file. Users can specify the stamp type (text or image), rotation, opacity, width spacer, and height spacer. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$stamp_type = 'stamp_type_example'; // string | The stamp type (text or image)
$font_size = 30; // float | The font size of the stamp text and image
$rotation = 0; // float | The rotation of the stamp in degrees
$opacity = 0.5; // float | The opacity of the stamp (0.0 - 1.0)
$position = 56; // int | Position for stamp placement based on a 1-9 grid (1: bottom-left, 2: bottom-center, 3: bottom-right, 4: middle-left, 5: middle-center, 6: middle-right, 7: top-left, 8: top-center, 9: top-right)
$override_x = -1; // float | Override X coordinate for stamp placement. If set, it will override the position-based calculation. Negative value means no override.
$override_y = -1; // float | Override Y coordinate for stamp placement. If set, it will override the position-based calculation. Negative value means no override.
$custom_margin = 'medium'; // string | Specifies the margin size for the stamp.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$stamp_text = 'Stirling Software'; // string | The stamp text
$stamp_image = '/path/to/file.txt'; // \SplFileObject
$alphabet = 'roman'; // string | The selected alphabet of the stamp text
$custom_color = '#d3d3d3'; // string | The color of the stamp text

try {
    $result = $apiInstance->addStamp($page_numbers, $stamp_type, $font_size, $rotation, $opacity, $position, $override_x, $override_y, $custom_margin, $file_input, $file_id, $stamp_text, $stamp_image, $alphabet, $custom_color);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->addStamp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **stamp_type** | **string**| The stamp type (text or image) | |
| **font_size** | **float**| The font size of the stamp text and image | [default to 30] |
| **rotation** | **float**| The rotation of the stamp in degrees | [default to 0] |
| **opacity** | **float**| The opacity of the stamp (0.0 - 1.0) | [default to 0.5] |
| **position** | **int**| Position for stamp placement based on a 1-9 grid (1: bottom-left, 2: bottom-center, 3: bottom-right, 4: middle-left, 5: middle-center, 6: middle-right, 7: top-left, 8: top-center, 9: top-right) | |
| **override_x** | **float**| Override X coordinate for stamp placement. If set, it will override the position-based calculation. Negative value means no override. | [default to -1] |
| **override_y** | **float**| Override Y coordinate for stamp placement. If set, it will override the position-based calculation. Negative value means no override. | [default to -1] |
| **custom_margin** | **string**| Specifies the margin size for the stamp. | [default to &#39;medium&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **stamp_text** | **string**| The stamp text | [optional] [default to &#39;Stirling Software&#39;] |
| **stamp_image** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **alphabet** | **string**| The selected alphabet of the stamp text | [optional] [default to &#39;roman&#39;] |
| **custom_color** | **string**| The color of the stamp text | [optional] [default to &#39;#d3d3d3&#39;] |

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

## `autoSplitPdf()`

```php
autoSplitPdf($file_input, $file_id, $duplex_mode): \SplFileObject
```

Auto split PDF pages into separate documents

This endpoint accepts a PDF file, scans each page for a specific QR code, and splits the document at the QR code boundaries. The output is a zip file containing each separate PDF document. Input:PDF Output:ZIP-PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$duplex_mode = false; // bool | Flag indicating if the duplex mode is active, where the page after the divider also gets removed.

try {
    $result = $apiInstance->autoSplitPdf($file_input, $file_id, $duplex_mode);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->autoSplitPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **duplex_mode** | **bool**| Flag indicating if the duplex mode is active, where the page after the divider also gets removed. | [optional] [default to false] |

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

## `decompressPdf()`

```php
decompressPdf($file_input, $file_id): string
```

Decompress PDF streams

Fully decompresses all PDF streams including text content

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->decompressPdf($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->decompressPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**string**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `*/*`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `extractHeader()`

```php
extractHeader($file_input, $file_id): \SplFileObject
```

Grabs all JS from a PDF and returns a single JS file with all code

desc. Input:PDF Output:JS Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->extractHeader($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->extractHeader: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `text/plain`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `extractHeader1()`

```php
extractHeader1($file_input, $file_id, $use_first_text_as_fallback): string
```

Extract header from PDF file

This endpoint accepts a PDF file and attempts to extract its title or header based on heuristics. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$use_first_text_as_fallback = false; // bool | Flag indicating whether to use the first text as a fallback if no suitable title is found. Defaults to false.

try {
    $result = $apiInstance->extractHeader1($file_input, $file_id, $use_first_text_as_fallback);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->extractHeader1: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **use_first_text_as_fallback** | **bool**| Flag indicating whether to use the first text as a fallback if no suitable title is found. Defaults to false. | [optional] [default to false] |

### Return type

**string**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `*/*`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `extractImageScans()`

```php
extractImageScans($file_input, $angle_threshold, $tolerance, $min_area, $min_contour_area, $border_size): \SplFileObject
```

Extract image scans from an input file

This endpoint extracts image scans from a given file based on certain parameters. Users can specify angle threshold, tolerance, minimum area, minimum contour area, and border size. Input:PDF Output:IMAGE/ZIP Type:SIMO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$angle_threshold = 5; // int | The angle threshold for the image scan extraction
$tolerance = 20; // int | The tolerance for the image scan extraction
$min_area = 8000; // int | The minimum area for the image scan extraction
$min_contour_area = 500; // int | The minimum contour area for the image scan extraction
$border_size = 1; // int | The border size for the image scan extraction

try {
    $result = $apiInstance->extractImageScans($file_input, $angle_threshold, $tolerance, $min_area, $min_contour_area, $border_size);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->extractImageScans: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | |
| **angle_threshold** | **int**| The angle threshold for the image scan extraction | [default to 5] |
| **tolerance** | **int**| The tolerance for the image scan extraction | [default to 20] |
| **min_area** | **int**| The minimum area for the image scan extraction | [default to 8000] |
| **min_contour_area** | **int**| The minimum contour area for the image scan extraction | [default to 500] |
| **border_size** | **int**| The border size for the image scan extraction | [default to 1] |

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

## `extractImages()`

```php
extractImages($format, $file_input, $file_id, $allow_duplicates): \SplFileObject
```

Extract images from a PDF file

This endpoint extracts images from a given PDF file and returns them in a zip file. Users can specify the output image format. Input:PDF Output:IMAGE/ZIP Type:SIMO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$format = 'png'; // string | The output image format e.g., 'png', 'jpeg', or 'gif'
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$allow_duplicates = false; // bool | Boolean to enable/disable the saving of duplicate images, true to enable duplicates

try {
    $result = $apiInstance->extractImages($format, $file_input, $file_id, $allow_duplicates);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->extractImages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **format** | **string**| The output image format e.g., &#39;png&#39;, &#39;jpeg&#39;, or &#39;gif&#39; | [default to &#39;png&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **allow_duplicates** | **bool**| Boolean to enable/disable the saving of duplicate images, true to enable duplicates | [optional] [default to false] |

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

## `flatten()`

```php
flatten($flatten_only_forms, $file_input, $file_id): \SplFileObject
```

Flatten PDF form fields or full page

Flattening just PDF form fields or converting each page to images to make text unselectable. Input:PDF, Output:PDF. Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$flatten_only_forms = false; // bool | True to flatten only the forms, false to flatten full PDF (Convert page to image)
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->flatten($flatten_only_forms, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->flatten: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **flatten_only_forms** | **bool**| True to flatten only the forms, false to flatten full PDF (Convert page to image) | [default to false] |
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

## `metadata()`

```php
metadata($delete_all, $file_input, $file_id, $author, $creation_date, $creator, $keywords, $modification_date, $producer, $subject, $title, $trapped, $all_request_params): \SplFileObject
```

Update metadata of a PDF file

This endpoint allows you to update the metadata of a given PDF file. You can add, modify, or delete standard and custom metadata fields. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$delete_all = false; // bool | Delete all metadata if set to true
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$author = 'author'; // string | The author of the document
$creation_date = '2023/10/01 12:00:00'; // string | The creation date of the document (format: yyyy/MM/dd HH:mm:ss)
$creator = 'creator'; // string | The creator of the document
$keywords = 'keywords'; // string | The keywords for the document
$modification_date = '2023/10/01 12:00:00'; // string | The modification date of the document (format: yyyy/MM/dd HH:mm:ss)
$producer = 'producer'; // string | The producer of the document
$subject = 'subject'; // string | The subject of the document
$title = 'title'; // string | The title of the document
$trapped = 'False'; // string | The trapped status of the document
$all_request_params = NULL; // array<string,string> | Map list of key and value of custom parameters. Note these must start with customKey and customValue if they are non-standard

try {
    $result = $apiInstance->metadata($delete_all, $file_input, $file_id, $author, $creation_date, $creator, $keywords, $modification_date, $producer, $subject, $title, $trapped, $all_request_params);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->metadata: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **delete_all** | **bool**| Delete all metadata if set to true | [default to false] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **author** | **string**| The author of the document | [optional] [default to &#39;author&#39;] |
| **creation_date** | **string**| The creation date of the document (format: yyyy/MM/dd HH:mm:ss) | [optional] [default to &#39;2023/10/01 12:00:00&#39;] |
| **creator** | **string**| The creator of the document | [optional] [default to &#39;creator&#39;] |
| **keywords** | **string**| The keywords for the document | [optional] [default to &#39;keywords&#39;] |
| **modification_date** | **string**| The modification date of the document (format: yyyy/MM/dd HH:mm:ss) | [optional] [default to &#39;2023/10/01 12:00:00&#39;] |
| **producer** | **string**| The producer of the document | [optional] [default to &#39;producer&#39;] |
| **subject** | **string**| The subject of the document | [optional] [default to &#39;subject&#39;] |
| **title** | **string**| The title of the document | [optional] [default to &#39;title&#39;] |
| **trapped** | **string**| The trapped status of the document | [optional] [default to &#39;False&#39;] |
| **all_request_params** | [**array<string,string>**](../Model/array.md)| Map list of key and value of custom parameters. Note these must start with customKey and customValue if they are non-standard | [optional] |

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

## `optimizePdf()`

```php
optimizePdf($optimize_level, $expected_output_size, $linearize, $normalize, $grayscale, $file_input, $file_id): \SplFileObject
```

Optimize PDF file

This endpoint accepts a PDF file and optimizes it based on the provided parameters. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$optimize_level = 56; // int | The level of optimization to apply to the PDF file. Higher values indicate greater compression but may reduce quality.
$expected_output_size = '25KB'; // string | The expected output size, e.g. '100MB', '25KB', etc.
$linearize = false; // bool | Whether to linearize the PDF for faster web viewing. Default is false.
$normalize = false; // bool | Whether to normalize the PDF content for better compatibility. Default is false.
$grayscale = false; // bool | Whether to convert the PDF to grayscale. Default is false.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->optimizePdf($optimize_level, $expected_output_size, $linearize, $normalize, $grayscale, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->optimizePdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **optimize_level** | **int**| The level of optimization to apply to the PDF file. Higher values indicate greater compression but may reduce quality. | |
| **expected_output_size** | **string**| The expected output size, e.g. &#39;100MB&#39;, &#39;25KB&#39;, etc. | [default to &#39;25KB&#39;] |
| **linearize** | **bool**| Whether to linearize the PDF for faster web viewing. Default is false. | [default to false] |
| **normalize** | **bool**| Whether to normalize the PDF content for better compatibility. Default is false. | [default to false] |
| **grayscale** | **bool**| Whether to convert the PDF to grayscale. Default is false. | [default to false] |
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

## `overlayImage()`

```php
overlayImage($image_file, $x, $y, $every_page, $file_input, $file_id): string
```

Overlay image onto a PDF file

This endpoint overlays an image onto a PDF file at the specified coordinates. The image can be overlaid on every page of the PDF if specified.  Input:PDF/IMAGE Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$image_file = '/path/to/file.txt'; // \SplFileObject
$x = 0; // float | The x-coordinate at which to place the top-left corner of the image.
$y = 0; // float | The y-coordinate at which to place the top-left corner of the image.
$every_page = false; // bool | Whether to overlay the image onto every page of the PDF.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->overlayImage($image_file, $x, $y, $every_page, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->overlayImage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **image_file** | **\SplFileObject****\SplFileObject**|  | |
| **x** | **float**| The x-coordinate at which to place the top-left corner of the image. | [default to 0] |
| **y** | **float**| The y-coordinate at which to place the top-left corner of the image. | [default to 0] |
| **every_page** | **bool**| Whether to overlay the image onto every page of the PDF. | [default to false] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**string**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `*/*`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `processPdfWithOCR()`

```php
processPdfWithOCR($languages, $ocr_type, $ocr_render_type, $file_input, $file_id, $sidecar, $deskew, $clean, $clean_final, $remove_images_after): \SplFileObject
```

Process a PDF file with OCR

This endpoint processes a PDF file using OCR (Optical Character Recognition). Users can specify languages, sidecar, deskew, clean, cleanFinal, ocrType, ocrRenderType, and removeImagesAfter options. Uses OCRmyPDF if available, falls back to Tesseract. Input:PDF Output:PDF Type:SI-Conditional

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$languages = array('[\"eng\"]'); // string[] | List of languages to use in OCR processing, e.g., 'eng', 'deu'
$ocr_type = 'ocr_type_example'; // string | Specify the OCR type, e.g., 'skip-text', 'force-ocr', or 'Normal'
$ocr_render_type = 'hocr'; // string | Specify the OCR render type, either 'hocr' or 'sandwich'
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$sidecar = True; // bool | Include OCR text in a sidecar text file if set to true
$deskew = True; // bool | Deskew the input file if set to true
$clean = True; // bool | Clean the input file if set to true
$clean_final = True; // bool | Clean the final output if set to true
$remove_images_after = True; // bool | Remove images from the output PDF if set to true

try {
    $result = $apiInstance->processPdfWithOCR($languages, $ocr_type, $ocr_render_type, $file_input, $file_id, $sidecar, $deskew, $clean, $clean_final, $remove_images_after);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->processPdfWithOCR: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **languages** | [**string[]**](../Model/string.md)| List of languages to use in OCR processing, e.g., &#39;eng&#39;, &#39;deu&#39; | [default to &#39;[&quot;eng&quot;]&#39;] |
| **ocr_type** | **string**| Specify the OCR type, e.g., &#39;skip-text&#39;, &#39;force-ocr&#39;, or &#39;Normal&#39; | |
| **ocr_render_type** | **string**| Specify the OCR render type, either &#39;hocr&#39; or &#39;sandwich&#39; | [default to &#39;hocr&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **sidecar** | **bool**| Include OCR text in a sidecar text file if set to true | [optional] |
| **deskew** | **bool**| Deskew the input file if set to true | [optional] |
| **clean** | **bool**| Clean the input file if set to true | [optional] |
| **clean_final** | **bool**| Clean the final output if set to true | [optional] |
| **remove_images_after** | **bool**| Remove images from the output PDF if set to true | [optional] |

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

## `removeBlankPages()`

```php
removeBlankPages($threshold, $white_percent, $file_input, $file_id): string
```

Remove blank pages from a PDF file

This endpoint removes blank pages from a given PDF file. Users can specify the threshold and white percentage to tune the detection of blank pages. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$threshold = 10; // int | The threshold value to determine blank pages
$white_percent = 99.9; // float | The percentage of white color on a page to consider it as blank
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->removeBlankPages($threshold, $white_percent, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->removeBlankPages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **threshold** | **int**| The threshold value to determine blank pages | [default to 10] |
| **white_percent** | **float**| The percentage of white color on a page to consider it as blank | [default to 99.9] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**string**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `*/*`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `repairPdf()`

```php
repairPdf($file_input, $file_id): \SplFileObject
```

Repair a PDF file

This endpoint repairs a given PDF file by running Ghostscript (primary), qpdf (fallback), or PDFBox (if no external tools available). The PDF is first saved to a temporary location, repaired, read back, and then returned as a response. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->repairPdf($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->repairPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
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

## `replaceAndInvertColor()`

```php
replaceAndInvertColor($replace_and_invert_option, $high_contrast_color_combination, $file_input, $file_id, $back_ground_color, $text_color): \SplFileObject
```

Replace-Invert Color PDF

This endpoint accepts a PDF file and option of invert all colors or replace text and background colors. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$replace_and_invert_option = 'HIGH_CONTRAST_COLOR'; // string | Replace and Invert color options of a pdf.
$high_contrast_color_combination = 'WHITE_TEXT_ON_BLACK'; // string | If HIGH_CONTRAST_COLOR option selected, then pick the default color option for text and background.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$back_ground_color = 'back_ground_color_example'; // string | If CUSTOM_COLOR option selected, then pick the custom color for background. Expected color value should be 24bit decimal value of a color
$text_color = 'text_color_example'; // string | If CUSTOM_COLOR option selected, then pick the custom color for text. Expected color value should be 24bit decimal value of a color

try {
    $result = $apiInstance->replaceAndInvertColor($replace_and_invert_option, $high_contrast_color_combination, $file_input, $file_id, $back_ground_color, $text_color);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->replaceAndInvertColor: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **replace_and_invert_option** | **string**| Replace and Invert color options of a pdf. | [default to &#39;HIGH_CONTRAST_COLOR&#39;] |
| **high_contrast_color_combination** | **string**| If HIGH_CONTRAST_COLOR option selected, then pick the default color option for text and background. | [default to &#39;WHITE_TEXT_ON_BLACK&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **back_ground_color** | **string**| If CUSTOM_COLOR option selected, then pick the custom color for background. Expected color value should be 24bit decimal value of a color | [optional] |
| **text_color** | **string**| If CUSTOM_COLOR option selected, then pick the custom color for text. Expected color value should be 24bit decimal value of a color | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `*/*`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `scannerEffect()`

```php
scannerEffect($file_input, $quality, $rotation, $colorspace, $border, $rotate, $rotate_variance, $brightness, $contrast, $blur, $noise, $yellowish, $resolution, $advanced_enabled, $quality_value, $rotation_value): string
```

Apply scanner effect to PDF

Applies various effects to simulate a scanned document, including rotation, noise, and edge softening. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$quality = 'quality_example'; // string | Scan quality preset
$rotation = 'rotation_example'; // string | Rotation preset
$colorspace = 'colorspace_example'; // string | Colorspace for output image
$border = 56; // int | Border thickness in pixels
$rotate = 56; // int | Base rotation in degrees
$rotate_variance = 56; // int | Random rotation variance in degrees
$brightness = 3.4; // float | Brightness multiplier (1.0 = no change)
$contrast = 3.4; // float | Contrast multiplier (1.0 = no change)
$blur = 3.4; // float | Blur amount (0 = none, higher = more blur)
$noise = 3.4; // float | Noise amount (0 = none, higher = more noise)
$yellowish = True; // bool | Simulate yellowed paper
$resolution = 56; // int | Rendering resolution in DPI
$advanced_enabled = True; // bool | Whether advanced settings are enabled
$quality_value = 56; // int
$rotation_value = 56; // int

try {
    $result = $apiInstance->scannerEffect($file_input, $quality, $rotation, $colorspace, $border, $rotate, $rotate_variance, $brightness, $contrast, $blur, $noise, $yellowish, $resolution, $advanced_enabled, $quality_value, $rotation_value);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->scannerEffect: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | |
| **quality** | **string**| Scan quality preset | |
| **rotation** | **string**| Rotation preset | |
| **colorspace** | **string**| Colorspace for output image | [optional] |
| **border** | **int**| Border thickness in pixels | [optional] |
| **rotate** | **int**| Base rotation in degrees | [optional] |
| **rotate_variance** | **int**| Random rotation variance in degrees | [optional] |
| **brightness** | **float**| Brightness multiplier (1.0 &#x3D; no change) | [optional] |
| **contrast** | **float**| Contrast multiplier (1.0 &#x3D; no change) | [optional] |
| **blur** | **float**| Blur amount (0 &#x3D; none, higher &#x3D; more blur) | [optional] |
| **noise** | **float**| Noise amount (0 &#x3D; none, higher &#x3D; more noise) | [optional] |
| **yellowish** | **bool**| Simulate yellowed paper | [optional] |
| **resolution** | **int**| Rendering resolution in DPI | [optional] |
| **advanced_enabled** | **bool**| Whether advanced settings are enabled | [optional] |
| **quality_value** | **int**|  | [optional] |
| **rotation_value** | **int**|  | [optional] |

### Return type

**string**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `*/*`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `unlockPDFForms()`

```php
unlockPDFForms($file_input, $file_id): \SplFileObject
```

Remove read-only property from form fields

Removing read-only property from form fields making them fillableInput:PDF, Output:PDF. Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MiscApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->unlockPDFForms($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MiscApi->unlockPDFForms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
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

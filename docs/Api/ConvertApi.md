# OpenAPI\Client\ConvertApi

Document format transformation services for cross-platform compatibility and workflow integration.  This endpoint group enables transformation between various formats, supporting diverse business workflows and system integrations for mixed document ecosystems.  Common use cases: • Legacy system integration, document migration, and cross-platform sharing • Archive standardization, publishing preparation, and content adaptation • Accessibility compliance and mobile-friendly document preparation  Business applications: • Enterprise content management, digital publishing, and educational platforms • Legal document processing, healthcare interoperability, and government standardization  Integration scenarios: • API-driven pipelines, automated workflow preparation, and batch conversions • Real-time format adaptation for user requests  Target users: System integrators, content managers, digital archivists, and organizations requiring flexible document format interoperability.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**convertEmlToPdf()**](ConvertApi.md#convertEmlToPdf) | **POST** /api/v1/convert/eml/pdf | Convert EML to PDF |
| [**convertToImage()**](ConvertApi.md#convertToImage) | **POST** /api/v1/convert/pdf/img | Convert PDF to image(s) |
| [**convertToPdf()**](ConvertApi.md#convertToPdf) | **POST** /api/v1/convert/img/pdf | Convert images to a PDF file |
| [**htmlToPdf()**](ConvertApi.md#htmlToPdf) | **POST** /api/v1/convert/html/pdf | Convert an HTML or ZIP (containing HTML and CSS) to PDF |
| [**markdownToPdf()**](ConvertApi.md#markdownToPdf) | **POST** /api/v1/convert/markdown/pdf | Convert a Markdown file to PDF |
| [**pdfToCsv()**](ConvertApi.md#pdfToCsv) | **POST** /api/v1/convert/pdf/csv | Extracts a CSV document from a PDF |
| [**pdfToPdfA()**](ConvertApi.md#pdfToPdfA) | **POST** /api/v1/convert/pdf/pdfa | Convert a PDF to a PDF/A |
| [**processFileToPDF()**](ConvertApi.md#processFileToPDF) | **POST** /api/v1/convert/file/pdf | Convert a file to a PDF using LibreOffice |
| [**processPdfToHTML()**](ConvertApi.md#processPdfToHTML) | **POST** /api/v1/convert/pdf/html | Convert PDF to HTML |
| [**processPdfToMarkdown()**](ConvertApi.md#processPdfToMarkdown) | **POST** /api/v1/convert/pdf/markdown | Convert PDF to Markdown |
| [**processPdfToPresentation()**](ConvertApi.md#processPdfToPresentation) | **POST** /api/v1/convert/pdf/presentation | Convert PDF to Presentation format |
| [**processPdfToRTForTXT()**](ConvertApi.md#processPdfToRTForTXT) | **POST** /api/v1/convert/pdf/text | Convert PDF to Text or RTF format |
| [**processPdfToWord()**](ConvertApi.md#processPdfToWord) | **POST** /api/v1/convert/pdf/word | Convert PDF to Word document |
| [**processPdfToXML()**](ConvertApi.md#processPdfToXML) | **POST** /api/v1/convert/pdf/xml | Convert PDF to XML |
| [**urlToPdf()**](ConvertApi.md#urlToPdf) | **POST** /api/v1/convert/url/pdf | Convert a URL to a PDF |


## `convertEmlToPdf()`

```php
convertEmlToPdf($file_input, $file_id, $include_attachments, $max_attachment_size_mb, $download_html, $include_all_recipients): \SplFileObject
```

Convert EML to PDF

This endpoint converts EML (email) files to PDF format with extensive customization options. Features include font settings, image constraints, display modes, attachment handling, and HTML debug output. Input: EML file, Output: PDF or HTML file. Type: SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$include_attachments = True; // bool | Include email attachments in the PDF output
$max_attachment_size_mb = 56; // int | Maximum attachment size in MB to include (default 10MB, range: 1-100)
$download_html = True; // bool | Download HTML intermediate file instead of PDF
$include_all_recipients = True; // bool | Include CC and BCC recipients in header (if available)

try {
    $result = $apiInstance->convertEmlToPdf($file_input, $file_id, $include_attachments, $max_attachment_size_mb, $download_html, $include_all_recipients);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertEmlToPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **include_attachments** | **bool**| Include email attachments in the PDF output | [optional] |
| **max_attachment_size_mb** | **int**| Maximum attachment size in MB to include (default 10MB, range: 1-100) | [optional] |
| **download_html** | **bool**| Download HTML intermediate file instead of PDF | [optional] |
| **include_all_recipients** | **bool**| Include CC and BCC recipients in header (if available) | [optional] |

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

## `convertToImage()`

```php
convertToImage($page_numbers, $image_format, $single_or_multiple, $color_type, $dpi, $file_input, $file_id): \SplFileObject
```

Convert PDF to image(s)

This endpoint converts a PDF file to image(s) with the specified image format, color type, and DPI. Users can choose to get a single image or multiple images.  Input:PDF Output:Image Type:SI-Conditional

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$image_format = 'png'; // string | The output image format
$single_or_multiple = 'multiple'; // string | Choose between a single image containing all pages or separate images for each page
$color_type = 'color'; // string | The color type of the output image(s)
$dpi = 300; // int | The DPI (dots per inch) for the output image(s)
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->convertToImage($page_numbers, $image_format, $single_or_multiple, $color_type, $dpi, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertToImage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **image_format** | **string**| The output image format | [default to &#39;png&#39;] |
| **single_or_multiple** | **string**| Choose between a single image containing all pages or separate images for each page | [default to &#39;multiple&#39;] |
| **color_type** | **string**| The color type of the output image(s) | [default to &#39;color&#39;] |
| **dpi** | **int**| The DPI (dots per inch) for the output image(s) | [default to 300] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

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

## `convertToPdf()`

```php
convertToPdf($file_input, $fit_option, $color_type, $auto_rotate): \SplFileObject
```

Convert images to a PDF file

This endpoint converts one or more images to a PDF file. Users can specify whether to stretch the images to fit the PDF page, and whether to automatically rotate the images. Input:Image Output:PDF Type:MISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = array('/path/to/file.txt'); // \SplFileObject[] | The input images to be converted to a PDF file
$fit_option = 'fillPage'; // string | Option to determine how the image will fit onto the page
$color_type = 'color'; // string | The color type of the output image(s)
$auto_rotate = false; // bool | Whether to automatically rotate the images to better fit the PDF page

try {
    $result = $apiInstance->convertToPdf($file_input, $fit_option, $color_type, $auto_rotate);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertToPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject[]**| The input images to be converted to a PDF file | |
| **fit_option** | **string**| Option to determine how the image will fit onto the page | [default to &#39;fillPage&#39;] |
| **color_type** | **string**| The color type of the output image(s) | [default to &#39;color&#39;] |
| **auto_rotate** | **bool**| Whether to automatically rotate the images to better fit the PDF page | [default to false] |

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

## `htmlToPdf()`

```php
htmlToPdf($zoom, $file_input, $file_id): \SplFileObject
```

Convert an HTML or ZIP (containing HTML and CSS) to PDF

This endpoint takes an HTML or ZIP file input and converts it to a PDF format. Input:HTML Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$zoom = 1; // float | Zoom level for displaying the website. Default is '1'.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->htmlToPdf($zoom, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->htmlToPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **zoom** | **float**| Zoom level for displaying the website. Default is &#39;1&#39;. | [default to 1] |
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

## `markdownToPdf()`

```php
markdownToPdf($file_input): \SplFileObject
```

Convert a Markdown file to PDF

This endpoint takes a Markdown file input, converts it to HTML, and then to PDF format. Input:MARKDOWN Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject

try {
    $result = $apiInstance->markdownToPdf($file_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->markdownToPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | |

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

## `pdfToCsv()`

```php
pdfToCsv($page_numbers, $file_input, $file_id): \SplFileObject
```

Extracts a CSV document from a PDF

This operation takes an input PDF file and returns CSV file of whole page. Input:PDF Output:CSV Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->pdfToCsv($page_numbers, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->pdfToCsv: ', $e->getMessage(), PHP_EOL;
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
- **Accept**: `text/csv`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `pdfToPdfA()`

```php
pdfToPdfA($output_format, $file_input, $file_id): \SplFileObject
```

Convert a PDF to a PDF/A

This endpoint converts a PDF file to a PDF/A file using LibreOffice. PDF/A is a format designed for long-term archiving of digital documents. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$output_format = 'output_format_example'; // string | The output PDF/A type
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->pdfToPdfA($output_format, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->pdfToPdfA: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **output_format** | **string**| The output PDF/A type | |
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

## `processFileToPDF()`

```php
processFileToPDF($file_input): string
```

Convert a file to a PDF using LibreOffice

This endpoint converts a given file to a PDF using LibreOffice API  Input:ANY Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject

try {
    $result = $apiInstance->processFileToPDF($file_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processFileToPDF: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | |

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

## `processPdfToHTML()`

```php
processPdfToHTML($file_input, $file_id): \SplFileObject
```

Convert PDF to HTML

This endpoint converts a PDF file to HTML format. Input:PDF Output:HTML Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->processPdfToHTML($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processPdfToHTML: ', $e->getMessage(), PHP_EOL;
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
- **Accept**: `text/html`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `processPdfToMarkdown()`

```php
processPdfToMarkdown($file_input, $file_id): \SplFileObject
```

Convert PDF to Markdown

This endpoint converts a PDF file to Markdown format. Input:PDF Output:Markdown Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->processPdfToMarkdown($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processPdfToMarkdown: ', $e->getMessage(), PHP_EOL;
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
- **Accept**: `text/markdown`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `processPdfToPresentation()`

```php
processPdfToPresentation($output_format, $file_input, $file_id): \SplFileObject
```

Convert PDF to Presentation format

This endpoint converts a given PDF file to a Presentation format. Input:PDF Output:PPT Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$output_format = 'output_format_example'; // string | The output Presentation format
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->processPdfToPresentation($output_format, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processPdfToPresentation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **output_format** | **string**| The output Presentation format | |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/vnd.openxmlformats-officedocument.presentationml.presentation`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `processPdfToRTForTXT()`

```php
processPdfToRTForTXT($output_format, $file_input, $file_id): string
```

Convert PDF to Text or RTF format

This endpoint converts a given PDF file to Text or RTF format. Input:PDF Output:TXT Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$output_format = 'output_format_example'; // string | The output Text or RTF format
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->processPdfToRTForTXT($output_format, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processPdfToRTForTXT: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **output_format** | **string**| The output Text or RTF format | |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**string**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `text/plain`, `application/rtf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `processPdfToWord()`

```php
processPdfToWord($output_format, $file_input, $file_id): \SplFileObject
```

Convert PDF to Word document

This endpoint converts a given PDF file to a Word document format. Input:PDF Output:WORD Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$output_format = 'output_format_example'; // string | The output Word document format
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->processPdfToWord($output_format, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processPdfToWord: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **output_format** | **string**| The output Word document format | |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/vnd.openxmlformats-officedocument.wordprocessingml.document`, `application/msword`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `processPdfToXML()`

```php
processPdfToXML($file_input, $file_id): \SplFileObject
```

Convert PDF to XML

This endpoint converts a PDF file to an XML file. Input:PDF Output:XML Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->processPdfToXML($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->processPdfToXML: ', $e->getMessage(), PHP_EOL;
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
- **Accept**: `application/xml`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `urlToPdf()`

```php
urlToPdf($url_input): \SplFileObject
```

Convert a URL to a PDF

This endpoint fetches content from a URL and converts it to a PDF format. Input:N/A Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$url_input = 'url_input_example'; // string | The input URL to be converted to a PDF file

try {
    $result = $apiInstance->urlToPdf($url_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->urlToPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **url_input** | **string**| The input URL to be converted to a PDF file | |

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

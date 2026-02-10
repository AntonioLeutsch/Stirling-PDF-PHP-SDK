# OpenAPI\Client\GeneralApi

Core PDF processing operations for fundamental document manipulation workflows.  This endpoint group provides essential PDF functionality that forms the foundation of most document processing workflows across various industries.  Common use cases: • Document preparation for archival systems and content organization • File preparation for distribution, accessibility compliance, and batch processing • Document consolidation for reporting and legal compliance workflows  Typical applications: • Content management, publishing workflows, and educational content distribution • Business process automation and archive management  Target users: Content managers, document processors, and organizations requiring reliable foundational PDF manipulation capabilities.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**autoSplitPdf1()**](GeneralApi.md#autoSplitPdf1) | **POST** /api/v1/general/split-by-size-or-count | Auto split PDF pages into separate documents based on size or count |
| [**createBookletImposition()**](GeneralApi.md#createBookletImposition) | **POST** /api/v1/general/booklet-imposition | Create a booklet with proper page imposition |
| [**cropPdf()**](GeneralApi.md#cropPdf) | **POST** /api/v1/general/crop | Crops a PDF document |
| [**deletePages()**](GeneralApi.md#deletePages) | **POST** /api/v1/general/remove-pages | Remove pages from a PDF file |
| [**editTableOfContents()**](GeneralApi.md#editTableOfContents) | **POST** /api/v1/general/edit-table-of-contents | Edit Table of Contents |
| [**extractBookmarks()**](GeneralApi.md#extractBookmarks) | **POST** /api/v1/general/extract-bookmarks | Extract PDF Bookmarks |
| [**mergeMultiplePagesIntoOne()**](GeneralApi.md#mergeMultiplePagesIntoOne) | **POST** /api/v1/general/multi-page-layout | Merge multiple pages of a PDF document into a single page |
| [**mergePdfs()**](GeneralApi.md#mergePdfs) | **POST** /api/v1/general/merge-pdfs | Merge multiple PDF files into one |
| [**overlayPdfs()**](GeneralApi.md#overlayPdfs) | **POST** /api/v1/general/overlay-pdfs | Overlay PDF files in various modes |
| [**pdfToSinglePage()**](GeneralApi.md#pdfToSinglePage) | **POST** /api/v1/general/pdf-to-single-page | Convert a multi-page PDF into a single long page PDF |
| [**rearrangePages()**](GeneralApi.md#rearrangePages) | **POST** /api/v1/general/rearrange-pages | Rearrange pages in a PDF file |
| [**removeImages()**](GeneralApi.md#removeImages) | **POST** /api/v1/general/remove-image-pdf | Remove images from file to reduce the file size. |
| [**rotatePDF()**](GeneralApi.md#rotatePDF) | **POST** /api/v1/general/rotate-pdf | Rotate a PDF file |
| [**scalePages()**](GeneralApi.md#scalePages) | **POST** /api/v1/general/scale-pages | Change the size of a PDF page/document |
| [**splitPdf()**](GeneralApi.md#splitPdf) | **POST** /api/v1/general/split-pdf-by-sections | Split PDF pages into smaller sections |
| [**splitPdf1()**](GeneralApi.md#splitPdf1) | **POST** /api/v1/general/split-pdf-by-chapters | Split PDFs by Chapters |
| [**splitPdf2()**](GeneralApi.md#splitPdf2) | **POST** /api/v1/general/split-pages | Split a PDF file into separate documents |


## `autoSplitPdf1()`

```php
autoSplitPdf1($file_input, $file_id, $split_type, $split_value): \SplFileObject
```

Auto split PDF pages into separate documents based on size or count

split PDF into multiple paged documents based on size/count, ie if 20 pages and split into 5, it does 5 documents each 4 pages   if 10MB and each page is 1MB and you enter 2MB then 5 docs each 2MB (rounded so that it accepts 1.9MB but not 2.1MB) Input:PDF Output:ZIP-PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$split_type = 0; // int | Determines the type of split: 0 for size, 1 for page count, 2 for document count
$split_value = '10MB'; // string | Value for split: size in MB (e.g., '10MB') or number of pages (e.g., '5')

try {
    $result = $apiInstance->autoSplitPdf1($file_input, $file_id, $split_type, $split_value);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->autoSplitPdf1: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **split_type** | **int**| Determines the type of split: 0 for size, 1 for page count, 2 for document count | [optional] [default to 0] |
| **split_value** | **string**| Value for split: size in MB (e.g., &#39;10MB&#39;) or number of pages (e.g., &#39;5&#39;) | [optional] [default to &#39;10MB&#39;] |

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

## `createBookletImposition()`

```php
createBookletImposition($booklet_type, $pages_per_sheet, $page_orientation, $file_input, $file_id, $add_border): \SplFileObject
```

Create a booklet with proper page imposition

This operation combines page reordering for booklet printing with multi-page layout. It rearranges pages in the correct order for booklet printing and places multiple pages on each sheet for proper folding and binding. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$booklet_type = 'BOOKLET'; // string | The booklet type to create.
$pages_per_sheet = 56; // int | The number of pages to fit onto a single sheet in the output PDF.
$page_orientation = 'LANDSCAPE'; // string | The page orientation for the output booklet sheets.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$add_border = True; // bool | Boolean for if you wish to add border around the pages

try {
    $result = $apiInstance->createBookletImposition($booklet_type, $pages_per_sheet, $page_orientation, $file_input, $file_id, $add_border);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->createBookletImposition: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **booklet_type** | **string**| The booklet type to create. | [default to &#39;BOOKLET&#39;] |
| **pages_per_sheet** | **int**| The number of pages to fit onto a single sheet in the output PDF. | |
| **page_orientation** | **string**| The page orientation for the output booklet sheets. | [default to &#39;LANDSCAPE&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **add_border** | **bool**| Boolean for if you wish to add border around the pages | [optional] |

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

## `cropPdf()`

```php
cropPdf($file_input, $file_id, $x, $y, $width, $height): \SplFileObject
```

Crops a PDF document

This operation takes an input PDF file and crops it according to the given coordinates. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$x = 3.4; // float | The x-coordinate of the top-left corner of the crop area
$y = 3.4; // float | The y-coordinate of the top-left corner of the crop area
$width = 3.4; // float | The width of the crop area
$height = 3.4; // float | The height of the crop area

try {
    $result = $apiInstance->cropPdf($file_input, $file_id, $x, $y, $width, $height);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->cropPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **x** | **float**| The x-coordinate of the top-left corner of the crop area | [optional] |
| **y** | **float**| The y-coordinate of the top-left corner of the crop area | [optional] |
| **width** | **float**| The width of the crop area | [optional] |
| **height** | **float**| The height of the crop area | [optional] |

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

## `deletePages()`

```php
deletePages($page_numbers, $file_input, $file_id): \SplFileObject
```

Remove pages from a PDF file

This endpoint removes specified pages from a given PDF file. Users can provide a comma-separated list of page numbers or ranges to delete. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->deletePages($page_numbers, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->deletePages: ', $e->getMessage(), PHP_EOL;
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

## `editTableOfContents()`

```php
editTableOfContents($file_input, $file_id, $bookmark_data, $replace_existing): \SplFileObject
```

Edit Table of Contents

Add or edit bookmarks/table of contents in a PDF document.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$bookmark_data = 'bookmark_data_example'; // string | Bookmark structure in JSON format
$replace_existing = True; // bool | Whether to replace existing bookmarks or append to them

try {
    $result = $apiInstance->editTableOfContents($file_input, $file_id, $bookmark_data, $replace_existing);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->editTableOfContents: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **bookmark_data** | **string**| Bookmark structure in JSON format | [optional] |
| **replace_existing** | **bool**| Whether to replace existing bookmarks or append to them | [optional] |

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

## `extractBookmarks()`

```php
extractBookmarks($file): object
```

Extract PDF Bookmarks

Extracts bookmarks/table of contents from a PDF document as JSON.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file = '/path/to/file.txt'; // \SplFileObject

try {
    $result = $apiInstance->extractBookmarks($file);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->extractBookmarks: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file** | **\SplFileObject****\SplFileObject**|  | |

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

## `mergeMultiplePagesIntoOne()`

```php
mergeMultiplePagesIntoOne($pages_per_sheet, $file_input, $file_id, $add_border): \SplFileObject
```

Merge multiple pages of a PDF document into a single page

This operation takes an input PDF file and the number of pages to merge into a single sheet in the output PDF file. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$pages_per_sheet = 56; // int | The number of pages to fit onto a single sheet in the output PDF.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$add_border = True; // bool | Boolean for if you wish to add border around the pages

try {
    $result = $apiInstance->mergeMultiplePagesIntoOne($pages_per_sheet, $file_input, $file_id, $add_border);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->mergeMultiplePagesIntoOne: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **pages_per_sheet** | **int**| The number of pages to fit onto a single sheet in the output PDF. | |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **add_border** | **bool**| Boolean for if you wish to add border around the pages | [optional] |

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

## `mergePdfs()`

```php
mergePdfs($file_input, $sort_type, $remove_cert_sign, $generate_toc): \SplFileObject
```

Merge multiple PDF files into one

This endpoint merges multiple PDF files into a single PDF file. The merged file will contain all pages from the input files in the order they were provided. Input:PDF Output:PDF Type:MISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = array('/path/to/file.txt'); // \SplFileObject[] | The input PDF files
$sort_type = 'orderProvided'; // string | The type of sorting to be applied on the input files before merging.
$remove_cert_sign = true; // bool | Flag indicating whether to remove certification signatures from the merged PDF. If true, all certification signatures will be removed from the final merged document.
$generate_toc = false; // bool | Flag indicating whether to generate a table of contents for the merged PDF. If true, a table of contents will be created using the input filenames as chapter names.

try {
    $result = $apiInstance->mergePdfs($file_input, $sort_type, $remove_cert_sign, $generate_toc);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->mergePdfs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject[]**| The input PDF files | |
| **sort_type** | **string**| The type of sorting to be applied on the input files before merging. | [default to &#39;orderProvided&#39;] |
| **remove_cert_sign** | **bool**| Flag indicating whether to remove certification signatures from the merged PDF. If true, all certification signatures will be removed from the final merged document. | [default to true] |
| **generate_toc** | **bool**| Flag indicating whether to generate a table of contents for the merged PDF. If true, a table of contents will be created using the input filenames as chapter names. | [optional] [default to false] |

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

## `overlayPdfs()`

```php
overlayPdfs($overlay_files, $overlay_mode, $overlay_position, $file_input, $file_id, $counts): \SplFileObject
```

Overlay PDF files in various modes

Overlay PDF files onto a base PDF with different modes: Sequential, Interleaved, or Fixed Repeat. Input:PDF Output:PDF Type:MIMO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$overlay_files = array('/path/to/file.txt'); // \SplFileObject[] | An array of PDF files to be used as overlays on the base PDF. The order in these files is applied based on the selected mode.
$overlay_mode = 'overlay_mode_example'; // string | The mode of overlaying: 'SequentialOverlay' for sequential application, 'InterleavedOverlay' for round-robin application, 'FixedRepeatOverlay' for fixed repetition based on provided counts
$overlay_position = 3.4; // float | Overlay position 0 is Foregound, 1 is Background
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$counts = array(56); // int[] | An array of integers specifying the number of times each corresponding overlay file should be applied in the 'FixedRepeatOverlay' mode. This should match the length of the overlayFiles array.

try {
    $result = $apiInstance->overlayPdfs($overlay_files, $overlay_mode, $overlay_position, $file_input, $file_id, $counts);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->overlayPdfs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **overlay_files** | **\SplFileObject[]**| An array of PDF files to be used as overlays on the base PDF. The order in these files is applied based on the selected mode. | |
| **overlay_mode** | **string**| The mode of overlaying: &#39;SequentialOverlay&#39; for sequential application, &#39;InterleavedOverlay&#39; for round-robin application, &#39;FixedRepeatOverlay&#39; for fixed repetition based on provided counts | |
| **overlay_position** | **float**| Overlay position 0 is Foregound, 1 is Background | |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **counts** | [**int[]**](../Model/int.md)| An array of integers specifying the number of times each corresponding overlay file should be applied in the &#39;FixedRepeatOverlay&#39; mode. This should match the length of the overlayFiles array. | [optional] |

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

## `pdfToSinglePage()`

```php
pdfToSinglePage($file_input, $file_id): \SplFileObject
```

Convert a multi-page PDF into a single long page PDF

This endpoint converts a multi-page PDF document into a single paged PDF document. The width of the single page will be same as the input's width, but the height will be the sum of all the pages' heights. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->pdfToSinglePage($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->pdfToSinglePage: ', $e->getMessage(), PHP_EOL;
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

## `rearrangePages()`

```php
rearrangePages($page_numbers, $file_input, $file_id, $custom_mode): \SplFileObject
```

Rearrange pages in a PDF file

This endpoint rearranges pages in a given PDF file based on the specified page order or custom mode. Users can provide a page order as a comma-separated list of page numbers or page ranges, or a custom mode. Input:PDF Output:PDF

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$custom_mode = 'custom_mode_example'; // string | The custom mode for page rearrangement. Valid values are: CUSTOM: Uses order defined in PageNums DUPLICATE: Duplicate pages n times (if Page order defined as 4, then duplicates each page 4 times)REVERSE_ORDER: Reverses the order of all pages. DUPLEX_SORT: Sorts pages as if all fronts were scanned then all backs in reverse (1, n, 2, n-1, ...). BOOKLET_SORT: Arranges pages for booklet printing (last, first, second, second last, ...). ODD_EVEN_SPLIT: Splits and arranges pages into odd and even numbered pages. ODD_EVEN_MERGE: Merges pages and organises them alternately into odd and even pages. REMOVE_FIRST: Removes the first page. REMOVE_LAST: Removes the last page. REMOVE_FIRST_AND_LAST: Removes both the first and the last pages.

try {
    $result = $apiInstance->rearrangePages($page_numbers, $file_input, $file_id, $custom_mode);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->rearrangePages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **custom_mode** | **string**| The custom mode for page rearrangement. Valid values are: CUSTOM: Uses order defined in PageNums DUPLICATE: Duplicate pages n times (if Page order defined as 4, then duplicates each page 4 times)REVERSE_ORDER: Reverses the order of all pages. DUPLEX_SORT: Sorts pages as if all fronts were scanned then all backs in reverse (1, n, 2, n-1, ...). BOOKLET_SORT: Arranges pages for booklet printing (last, first, second, second last, ...). ODD_EVEN_SPLIT: Splits and arranges pages into odd and even numbered pages. ODD_EVEN_MERGE: Merges pages and organises them alternately into odd and even pages. REMOVE_FIRST: Removes the first page. REMOVE_LAST: Removes the last page. REMOVE_FIRST_AND_LAST: Removes both the first and the last pages. | [optional] |

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

## `removeImages()`

```php
removeImages($file_input, $file_id): \SplFileObject
```

Remove images from file to reduce the file size.

This endpoint remove images from file to reduce the file size.Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->removeImages($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->removeImages: ', $e->getMessage(), PHP_EOL;
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

## `rotatePDF()`

```php
rotatePDF($angle, $file_input, $file_id): \SplFileObject
```

Rotate a PDF file

This endpoint rotates a given PDF file by a specified angle. The angle must be a multiple of 90. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$angle = 56; // int | The angle by which to rotate the PDF file. This should be a multiple of 90.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->rotatePDF($angle, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->rotatePDF: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **angle** | **int**| The angle by which to rotate the PDF file. This should be a multiple of 90. | |
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

## `scalePages()`

```php
scalePages($page_size, $scale_factor, $file_input, $file_id): \SplFileObject
```

Change the size of a PDF page/document

This operation takes an input PDF file and the size to scale the pages to in the output PDF file. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_size = 'page_size_example'; // string | The scale of pages in the output PDF. Acceptable values are A0-A6, LETTER, LEGAL, KEEP.
$scale_factor = 1; // float | The scale of the content on the pages of the output PDF. Acceptable values are floats.
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->scalePages($page_size, $scale_factor, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->scalePages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_size** | **string**| The scale of pages in the output PDF. Acceptable values are A0-A6, LETTER, LEGAL, KEEP. | |
| **scale_factor** | **float**| The scale of the content on the pages of the output PDF. Acceptable values are floats. | [default to 1] |
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

## `splitPdf()`

```php
splitPdf($horizontal_divisions, $vertical_divisions, $merge, $file_input, $file_id): \SplFileObject
```

Split PDF pages into smaller sections

Split each page of a PDF into smaller sections based on the user's choice (halves, thirds, quarters, etc.), both vertically and horizontally. Input:PDF Output:ZIP-PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$horizontal_divisions = 0; // int | Number of horizontal divisions for each PDF page
$vertical_divisions = 1; // int | Number of vertical divisions for each PDF page
$merge = true; // bool | Merge the split documents into a single PDF
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->splitPdf($horizontal_divisions, $vertical_divisions, $merge, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->splitPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **horizontal_divisions** | **int**| Number of horizontal divisions for each PDF page | [default to 0] |
| **vertical_divisions** | **int**| Number of vertical divisions for each PDF page | [default to 1] |
| **merge** | **bool**| Merge the split documents into a single PDF | [default to true] |
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

## `splitPdf1()`

```php
splitPdf1($include_metadata, $allow_duplicates, $bookmark_level, $file_input, $file_id): \SplFileObject
```

Split PDFs by Chapters

Splits a PDF into chapters and returns a ZIP file.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$include_metadata = true; // bool | Whether to include Metadata or not
$allow_duplicates = true; // bool | Whether to allow duplicates or not
$bookmark_level = 2; // int | Maximum bookmark level required
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->splitPdf1($include_metadata, $allow_duplicates, $bookmark_level, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->splitPdf1: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **include_metadata** | **bool**| Whether to include Metadata or not | [default to true] |
| **allow_duplicates** | **bool**| Whether to allow duplicates or not | [default to true] |
| **bookmark_level** | **int**| Maximum bookmark level required | [default to 2] |
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

## `splitPdf2()`

```php
splitPdf2($page_numbers, $file_input, $file_id): \SplFileObject
```

Split a PDF file into separate documents

This endpoint splits a given PDF file into separate documents based on the specified page numbers or ranges. Users can specify pages using individual numbers, ranges, or 'all' for every page. Input:PDF Output:PDF Type:SIMO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\GeneralApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->splitPdf2($page_numbers, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling GeneralApi->splitPdf2: ', $e->getMessage(), PHP_EOL;
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
- **Accept**: `application/pdf`, `application/zip`, `image/png`, `image/jpeg`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

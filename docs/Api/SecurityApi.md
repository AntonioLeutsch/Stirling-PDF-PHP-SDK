# OpenAPI\Client\SecurityApi

Document security and protection services for confidential and sensitive content.  This endpoint group provides essential security operations for organizations handling sensitive documents and materials requiring controlled access.  Common use cases: • Legal confidentiality, healthcare privacy (HIPAA), and financial regulatory compliance • Government classified handling, corporate IP protection, and educational privacy (FERPA) • Contract security for business transactions  Business applications: • Document authentication, confidential sharing, and secure archiving • Content watermarking, access control, and privacy protection through redaction  Industry scenarios: • Legal discovery, medical records exchange, financial audit documentation • Enterprise policy enforcement and data governance  Target users: Legal professionals, healthcare administrators, compliance officers, government agencies, and enterprises handling sensitive content.

All URIs are relative to https://api.stirling.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addPassword()**](SecurityApi.md#addPassword) | **POST** /api/v1/security/add-password | Add password to a PDF file |
| [**addWatermark()**](SecurityApi.md#addWatermark) | **POST** /api/v1/security/add-watermark | Add watermark to a PDF file |
| [**getPdfInfo()**](SecurityApi.md#getPdfInfo) | **POST** /api/v1/security/get-info-on-pdf | Summary here |
| [**redactPdfAuto()**](SecurityApi.md#redactPdfAuto) | **POST** /api/v1/security/auto-redact | Redacts listOfText in a PDF document |
| [**redactPdfManual()**](SecurityApi.md#redactPdfManual) | **POST** /api/v1/security/redact | Redacts areas and pages in a PDF document |
| [**removeCertSignPDF()**](SecurityApi.md#removeCertSignPDF) | **POST** /api/v1/security/remove-cert-sign | Remove digital signature from PDF |
| [**removePassword()**](SecurityApi.md#removePassword) | **POST** /api/v1/security/remove-password | Remove password from a PDF file |
| [**sanitizePDF()**](SecurityApi.md#sanitizePDF) | **POST** /api/v1/security/sanitize-pdf | Sanitize a PDF file |
| [**signPDFWithCert()**](SecurityApi.md#signPDFWithCert) | **POST** /api/v1/security/cert-sign | Sign PDF with a Digital Certificate |
| [**validateSignature()**](SecurityApi.md#validateSignature) | **POST** /api/v1/security/validate-signature | Validate PDF Digital Signature |


## `addPassword()`

```php
addPassword($key_length, $file_input, $file_id, $owner_password, $password, $prevent_assembly, $prevent_extract_content, $prevent_extract_for_accessibility, $prevent_fill_in_form, $prevent_modify, $prevent_modify_annotations, $prevent_printing, $prevent_printing_faithful): \SplFileObject
```

Add password to a PDF file

This endpoint adds password protection to a PDF file. Users can specify a set of permissions that should be applied to the file. Input:PDF Output:PDF

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$key_length = 56; // int | The length of the encryption key
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$owner_password = 'owner_password_example'; // string | The owner password to be added to the PDF file (Restricts what can be done with the document once it is opened)
$password = 'password_example'; // string | The password to be added to the PDF file (Restricts the opening of the document itself.)
$prevent_assembly = false; // bool | Whether document assembly is prevented
$prevent_extract_content = false; // bool | Whether content extraction is prevented
$prevent_extract_for_accessibility = false; // bool | Whether content extraction for accessibility is prevented
$prevent_fill_in_form = false; // bool | Whether form filling is prevented
$prevent_modify = false; // bool | Whether document modification is prevented
$prevent_modify_annotations = false; // bool | Whether modification of annotations is prevented
$prevent_printing = false; // bool | Whether printing of the document is prevented
$prevent_printing_faithful = false; // bool | Whether faithful printing is prevented

try {
    $result = $apiInstance->addPassword($key_length, $file_input, $file_id, $owner_password, $password, $prevent_assembly, $prevent_extract_content, $prevent_extract_for_accessibility, $prevent_fill_in_form, $prevent_modify, $prevent_modify_annotations, $prevent_printing, $prevent_printing_faithful);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->addPassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key_length** | **int**| The length of the encryption key | |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **owner_password** | **string**| The owner password to be added to the PDF file (Restricts what can be done with the document once it is opened) | [optional] |
| **password** | **string**| The password to be added to the PDF file (Restricts the opening of the document itself.) | [optional] |
| **prevent_assembly** | **bool**| Whether document assembly is prevented | [optional] [default to false] |
| **prevent_extract_content** | **bool**| Whether content extraction is prevented | [optional] [default to false] |
| **prevent_extract_for_accessibility** | **bool**| Whether content extraction for accessibility is prevented | [optional] [default to false] |
| **prevent_fill_in_form** | **bool**| Whether form filling is prevented | [optional] [default to false] |
| **prevent_modify** | **bool**| Whether document modification is prevented | [optional] [default to false] |
| **prevent_modify_annotations** | **bool**| Whether modification of annotations is prevented | [optional] [default to false] |
| **prevent_printing** | **bool**| Whether printing of the document is prevented | [optional] [default to false] |
| **prevent_printing_faithful** | **bool**| Whether faithful printing is prevented | [optional] [default to false] |

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

## `addWatermark()`

```php
addWatermark($watermark_type, $convert_pdfto_image, $file_input, $file_id, $watermark_text, $watermark_image, $alphabet, $font_size, $rotation, $opacity, $width_spacer, $height_spacer, $custom_color): \SplFileObject
```

Add watermark to a PDF file

This endpoint adds a watermark to a given PDF file. Users can specify the watermark type (text or image), rotation, opacity, width spacer, and height spacer. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$watermark_type = 'watermark_type_example'; // string | The watermark type (text or image)
$convert_pdfto_image = false; // bool | Convert the redacted PDF to an image
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$watermark_text = 'Stirling Software'; // string | The watermark text
$watermark_image = '/path/to/file.txt'; // \SplFileObject
$alphabet = 'roman'; // string | The selected alphabet
$font_size = 30; // float | The font size of the watermark text
$rotation = 0; // float | The rotation of the watermark in degrees
$opacity = 0.5; // float | The opacity of the watermark (0.0 - 1.0)
$width_spacer = 50; // int | The width spacer between watermark elements
$height_spacer = 50; // int | The height spacer between watermark elements
$custom_color = '#d3d3d3'; // string | The color for watermark

try {
    $result = $apiInstance->addWatermark($watermark_type, $convert_pdfto_image, $file_input, $file_id, $watermark_text, $watermark_image, $alphabet, $font_size, $rotation, $opacity, $width_spacer, $height_spacer, $custom_color);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->addWatermark: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **watermark_type** | **string**| The watermark type (text or image) | |
| **convert_pdfto_image** | **bool**| Convert the redacted PDF to an image | [default to false] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **watermark_text** | **string**| The watermark text | [optional] [default to &#39;Stirling Software&#39;] |
| **watermark_image** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **alphabet** | **string**| The selected alphabet | [optional] [default to &#39;roman&#39;] |
| **font_size** | **float**| The font size of the watermark text | [optional] [default to 30] |
| **rotation** | **float**| The rotation of the watermark in degrees | [optional] [default to 0] |
| **opacity** | **float**| The opacity of the watermark (0.0 - 1.0) | [optional] [default to 0.5] |
| **width_spacer** | **int**| The width spacer between watermark elements | [optional] [default to 50] |
| **height_spacer** | **int**| The height spacer between watermark elements | [optional] [default to 50] |
| **custom_color** | **string**| The color for watermark | [optional] [default to &#39;#d3d3d3&#39;] |

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

## `getPdfInfo()`

```php
getPdfInfo($file_input, $file_id): object
```

Summary here

desc. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->getPdfInfo($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->getPdfInfo: ', $e->getMessage(), PHP_EOL;
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

## `redactPdfAuto()`

```php
redactPdfAuto($list_of_text, $use_regex, $whole_word_search, $redact_color, $custom_padding, $convert_pdfto_image, $file_input, $file_id): \SplFileObject
```

Redacts listOfText in a PDF document

This operation takes an input PDF file and redacts the provided listOfText. Input:PDF, Output:PDF, Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$list_of_text = 'text,text2'; // string | List of text to redact from the PDF
$use_regex = false; // bool | Whether to use regex for the listOfText
$whole_word_search = false; // bool | Whether to use whole word search
$redact_color = '#000000'; // string | The color for redaction
$custom_padding = 3.4; // float | Custom padding for redaction
$convert_pdfto_image = false; // bool | Convert the redacted PDF to an image
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->redactPdfAuto($list_of_text, $use_regex, $whole_word_search, $redact_color, $custom_padding, $convert_pdfto_image, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->redactPdfAuto: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **list_of_text** | **string**| List of text to redact from the PDF | [default to &#39;text,text2&#39;] |
| **use_regex** | **bool**| Whether to use regex for the listOfText | [default to false] |
| **whole_word_search** | **bool**| Whether to use whole word search | [default to false] |
| **redact_color** | **string**| The color for redaction | [default to &#39;#000000&#39;] |
| **custom_padding** | **float**| Custom padding for redaction | |
| **convert_pdfto_image** | **bool**| Convert the redacted PDF to an image | [default to false] |
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

## `redactPdfManual()`

```php
redactPdfManual($page_numbers, $redactions, $convert_pdfto_image, $page_redaction_color, $file_input, $file_id): \SplFileObject
```

Redacts areas and pages in a PDF document

This operation takes an input PDF file with a list of areas, page number(s)/range(s)/function(s) to redact. Input:PDF, Output:PDF, Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$page_numbers = 'all'; // string | The pages to select, Supports ranges (e.g., '1,3,5-9'), or 'all' or functions in the format 'an+b' where 'a' is the multiplier of the page number 'n', and 'b' is a constant (e.g., '2n+1', '3n', '6n-5')
$redactions = array(new \OpenAPI\Client\Model\\OpenAPI\Client\Model\RedactionArea()); // \OpenAPI\Client\Model\RedactionArea[] | A list of areas that should be redacted
$convert_pdfto_image = false; // bool | Convert the redacted PDF to an image
$page_redaction_color = '#000000'; // string | The color used to fully redact certain pages
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->redactPdfManual($page_numbers, $redactions, $convert_pdfto_image, $page_redaction_color, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->redactPdfManual: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page_numbers** | **string**| The pages to select, Supports ranges (e.g., &#39;1,3,5-9&#39;), or &#39;all&#39; or functions in the format &#39;an+b&#39; where &#39;a&#39; is the multiplier of the page number &#39;n&#39;, and &#39;b&#39; is a constant (e.g., &#39;2n+1&#39;, &#39;3n&#39;, &#39;6n-5&#39;) | [default to &#39;all&#39;] |
| **redactions** | [**\OpenAPI\Client\Model\RedactionArea[]**](../Model/\OpenAPI\Client\Model\RedactionArea.md)| A list of areas that should be redacted | |
| **convert_pdfto_image** | **bool**| Convert the redacted PDF to an image | [default to false] |
| **page_redaction_color** | **string**| The color used to fully redact certain pages | [default to &#39;#000000&#39;] |
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

## `removeCertSignPDF()`

```php
removeCertSignPDF($file_input, $file_id): \SplFileObject
```

Remove digital signature from PDF

This endpoint accepts a PDF file and returns the PDF file without the digital signature. Input:PDF, Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->removeCertSignPDF($file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->removeCertSignPDF: ', $e->getMessage(), PHP_EOL;
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

## `removePassword()`

```php
removePassword($file_input, $file_id, $password): \SplFileObject
```

Remove password from a PDF file

This endpoint removes the password from a protected PDF file. Users need to provide the existing password. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$password = 'password_example'; // string | The password of the PDF file

try {
    $result = $apiInstance->removePassword($file_input, $file_id, $password);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->removePassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **password** | **string**| The password of the PDF file | [optional] |

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

## `sanitizePDF()`

```php
sanitizePDF($remove_java_script, $remove_embedded_files, $remove_xmp_metadata, $remove_metadata, $remove_links, $remove_fonts, $file_input, $file_id): \SplFileObject
```

Sanitize a PDF file

This endpoint processes a PDF file and removes specific elements based on the provided options. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$remove_java_script = true; // bool | Remove JavaScript actions from the PDF
$remove_embedded_files = true; // bool | Remove embedded files from the PDF
$remove_xmp_metadata = false; // bool | Remove XMP metadata from the PDF
$remove_metadata = false; // bool | Remove document info metadata from the PDF
$remove_links = false; // bool | Remove links from the PDF
$remove_fonts = false; // bool | Remove fonts from the PDF
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)

try {
    $result = $apiInstance->sanitizePDF($remove_java_script, $remove_embedded_files, $remove_xmp_metadata, $remove_metadata, $remove_links, $remove_fonts, $file_input, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->sanitizePDF: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **remove_java_script** | **bool**| Remove JavaScript actions from the PDF | [default to true] |
| **remove_embedded_files** | **bool**| Remove embedded files from the PDF | [default to true] |
| **remove_xmp_metadata** | **bool**| Remove XMP metadata from the PDF | [default to false] |
| **remove_metadata** | **bool**| Remove document info metadata from the PDF | [default to false] |
| **remove_links** | **bool**| Remove links from the PDF | [default to false] |
| **remove_fonts** | **bool**| Remove fonts from the PDF | [default to false] |
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

## `signPDFWithCert()`

```php
signPDFWithCert($cert_type, $show_signature, $show_logo, $file_input, $file_id, $private_key_file, $cert_file, $p12_file, $jks_file, $password, $reason, $location, $name, $page_number): \SplFileObject
```

Sign PDF with a Digital Certificate

This endpoint accepts a PDF file, a digital certificate and related information to sign the PDF. It then returns the digitally signed PDF file. Input:PDF Output:PDF Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$cert_type = 'cert_type_example'; // string | The type of the digital certificate
$show_signature = false; // bool | Whether to visually show the signature in the PDF file
$show_logo = true; // bool | Whether to visually show a signature logo along with the signature
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$private_key_file = '/path/to/file.txt'; // \SplFileObject
$cert_file = '/path/to/file.txt'; // \SplFileObject
$p12_file = '/path/to/file.txt'; // \SplFileObject
$jks_file = '/path/to/file.txt'; // \SplFileObject
$password = 'password_example'; // string | The password for the keystore or the private key
$reason = 'Signed by SPDF'; // string | The reason for signing the PDF
$location = 'SPDF'; // string | The location where the PDF is signed
$name = 'SPDF'; // string | The name of the signer
$page_number = 1; // int | The page number where the signature should be visible. This is required if showSignature is set to true

try {
    $result = $apiInstance->signPDFWithCert($cert_type, $show_signature, $show_logo, $file_input, $file_id, $private_key_file, $cert_file, $p12_file, $jks_file, $password, $reason, $location, $name, $page_number);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->signPDFWithCert: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **cert_type** | **string**| The type of the digital certificate | |
| **show_signature** | **bool**| Whether to visually show the signature in the PDF file | [default to false] |
| **show_logo** | **bool**| Whether to visually show a signature logo along with the signature | [default to true] |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **private_key_file** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **cert_file** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **p12_file** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **jks_file** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **password** | **string**| The password for the keystore or the private key | [optional] |
| **reason** | **string**| The reason for signing the PDF | [optional] [default to &#39;Signed by SPDF&#39;] |
| **location** | **string**| The location where the PDF is signed | [optional] [default to &#39;SPDF&#39;] |
| **name** | **string**| The name of the signer | [optional] [default to &#39;SPDF&#39;] |
| **page_number** | **int**| The page number where the signature should be visible. This is required if showSignature is set to true | [optional] [default to 1] |

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

## `validateSignature()`

```php
validateSignature($file_input, $file_id, $cert_file): object
```

Validate PDF Digital Signature

Validates the digital signatures in a PDF file against default or custom certificates. Input:PDF Output:JSON Type:SISO

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\SecurityApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_input = '/path/to/file.txt'; // \SplFileObject
$file_id = 'file_id_example'; // string | File ID for server-side files (can be used instead of fileInput)
$cert_file = '/path/to/file.txt'; // \SplFileObject

try {
    $result = $apiInstance->validateSignature($file_input, $file_id, $cert_file);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecurityApi->validateSignature: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_input** | **\SplFileObject****\SplFileObject**|  | [optional] |
| **file_id** | **string**| File ID for server-side files (can be used instead of fileInput) | [optional] |
| **cert_file** | **\SplFileObject****\SplFileObject**|  | [optional] |

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

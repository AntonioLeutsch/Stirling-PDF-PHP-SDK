# Stirling PDF PHP SDK

PHP SDK for the [Stirling PDF](https://www.stirlingpdf.com) API - PDF processing, conversion, manipulation, security and more.

## Installation

### Requirements

- PHP 8.1 or later
- PHP extensions: `curl`, `json`, `mbstring`

### Composer

```bash
composer require antonioleutsch/stirling-pdf-sdk
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

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

## API Endpoints

All URIs are relative to *https://api.stirling.com*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AnalysisApi* | [**getAnnotationInfo**](docs/Api/AnalysisApi.md#getannotationinfo) | **POST** /api/v1/analysis/annotation-info | Get annotation information
*AnalysisApi* | [**getBasicInfo**](docs/Api/AnalysisApi.md#getbasicinfo) | **POST** /api/v1/analysis/basic-info | Get basic PDF information
*AnalysisApi* | [**getDocumentProperties**](docs/Api/AnalysisApi.md#getdocumentproperties) | **POST** /api/v1/analysis/document-properties | Get PDF document properties
*AnalysisApi* | [**getFontInfo**](docs/Api/AnalysisApi.md#getfontinfo) | **POST** /api/v1/analysis/font-info | Get font information
*AnalysisApi* | [**getFormFields**](docs/Api/AnalysisApi.md#getformfields) | **POST** /api/v1/analysis/form-fields | Get form field information
*AnalysisApi* | [**getPageCount**](docs/Api/AnalysisApi.md#getpagecount) | **POST** /api/v1/analysis/page-count | Get PDF page count
*AnalysisApi* | [**getPageDimensions**](docs/Api/AnalysisApi.md#getpagedimensions) | **POST** /api/v1/analysis/page-dimensions | Get page dimensions for all pages
*AnalysisApi* | [**getSecurityInfo**](docs/Api/AnalysisApi.md#getsecurityinfo) | **POST** /api/v1/analysis/security-info | Get security information
*ConvertApi* | [**convertEmlToPdf**](docs/Api/ConvertApi.md#convertemltopdf) | **POST** /api/v1/convert/eml/pdf | Convert EML to PDF
*ConvertApi* | [**convertToImage**](docs/Api/ConvertApi.md#converttoimage) | **POST** /api/v1/convert/pdf/img | Convert PDF to image(s)
*ConvertApi* | [**convertToPdf**](docs/Api/ConvertApi.md#converttopdf) | **POST** /api/v1/convert/img/pdf | Convert images to a PDF file
*ConvertApi* | [**htmlToPdf**](docs/Api/ConvertApi.md#htmltopdf) | **POST** /api/v1/convert/html/pdf | Convert an HTML or ZIP (containing HTML and CSS) to PDF
*ConvertApi* | [**markdownToPdf**](docs/Api/ConvertApi.md#markdowntopdf) | **POST** /api/v1/convert/markdown/pdf | Convert a Markdown file to PDF
*ConvertApi* | [**pdfToCsv**](docs/Api/ConvertApi.md#pdftocsv) | **POST** /api/v1/convert/pdf/csv | Extracts a CSV document from a PDF
*ConvertApi* | [**pdfToPdfA**](docs/Api/ConvertApi.md#pdftopdfa) | **POST** /api/v1/convert/pdf/pdfa | Convert a PDF to a PDF/A
*ConvertApi* | [**processFileToPDF**](docs/Api/ConvertApi.md#processfiletopdf) | **POST** /api/v1/convert/file/pdf | Convert a file to a PDF using LibreOffice
*ConvertApi* | [**processPdfToHTML**](docs/Api/ConvertApi.md#processpdftohtml) | **POST** /api/v1/convert/pdf/html | Convert PDF to HTML
*ConvertApi* | [**processPdfToMarkdown**](docs/Api/ConvertApi.md#processpdftomarkdown) | **POST** /api/v1/convert/pdf/markdown | Convert PDF to Markdown
*ConvertApi* | [**processPdfToPresentation**](docs/Api/ConvertApi.md#processpdftopresentation) | **POST** /api/v1/convert/pdf/presentation | Convert PDF to Presentation format
*ConvertApi* | [**processPdfToRTForTXT**](docs/Api/ConvertApi.md#processpdftortfortxt) | **POST** /api/v1/convert/pdf/text | Convert PDF to Text or RTF format
*ConvertApi* | [**processPdfToWord**](docs/Api/ConvertApi.md#processpdftoword) | **POST** /api/v1/convert/pdf/word | Convert PDF to Word document
*ConvertApi* | [**processPdfToXML**](docs/Api/ConvertApi.md#processpdftoxml) | **POST** /api/v1/convert/pdf/xml | Convert PDF to XML
*ConvertApi* | [**urlToPdf**](docs/Api/ConvertApi.md#urltopdf) | **POST** /api/v1/convert/url/pdf | Convert a URL to a PDF
*FilterApi* | [**containsImage**](docs/Api/FilterApi.md#containsimage) | **POST** /api/v1/filter/filter-contains-image | Checks if a PDF contains an image
*FilterApi* | [**containsText**](docs/Api/FilterApi.md#containstext) | **POST** /api/v1/filter/filter-contains-text | Checks if a PDF contains set text, returns true if does
*FilterApi* | [**fileSize**](docs/Api/FilterApi.md#filesize) | **POST** /api/v1/filter/filter-file-size | Checks if a PDF is a set file size
*FilterApi* | [**pageCount**](docs/Api/FilterApi.md#pagecount) | **POST** /api/v1/filter/filter-page-count | Checks if a PDF is greater, less or equal to a setPageCount
*FilterApi* | [**pageRotation**](docs/Api/FilterApi.md#pagerotation) | **POST** /api/v1/filter/filter-page-rotation | Checks if a PDF is of a certain rotation
*FilterApi* | [**pageSize**](docs/Api/FilterApi.md#pagesize) | **POST** /api/v1/filter/filter-page-size | Checks if a PDF is of a certain size
*GeneralApi* | [**autoSplitPdf1**](docs/Api/GeneralApi.md#autosplitpdf1) | **POST** /api/v1/general/split-by-size-or-count | Auto split PDF pages into separate documents based on size or count
*GeneralApi* | [**createBookletImposition**](docs/Api/GeneralApi.md#createbookletimposition) | **POST** /api/v1/general/booklet-imposition | Create a booklet with proper page imposition
*GeneralApi* | [**cropPdf**](docs/Api/GeneralApi.md#croppdf) | **POST** /api/v1/general/crop | Crops a PDF document
*GeneralApi* | [**deletePages**](docs/Api/GeneralApi.md#deletepages) | **POST** /api/v1/general/remove-pages | Remove pages from a PDF file
*GeneralApi* | [**editTableOfContents**](docs/Api/GeneralApi.md#edittableofcontents) | **POST** /api/v1/general/edit-table-of-contents | Edit Table of Contents
*GeneralApi* | [**extractBookmarks**](docs/Api/GeneralApi.md#extractbookmarks) | **POST** /api/v1/general/extract-bookmarks | Extract PDF Bookmarks
*GeneralApi* | [**mergeMultiplePagesIntoOne**](docs/Api/GeneralApi.md#mergemultiplepagesintoone) | **POST** /api/v1/general/multi-page-layout | Merge multiple pages of a PDF document into a single page
*GeneralApi* | [**mergePdfs**](docs/Api/GeneralApi.md#mergepdfs) | **POST** /api/v1/general/merge-pdfs | Merge multiple PDF files into one
*GeneralApi* | [**overlayPdfs**](docs/Api/GeneralApi.md#overlaypdfs) | **POST** /api/v1/general/overlay-pdfs | Overlay PDF files in various modes
*GeneralApi* | [**pdfToSinglePage**](docs/Api/GeneralApi.md#pdftosinglepage) | **POST** /api/v1/general/pdf-to-single-page | Convert a multi-page PDF into a single long page PDF
*GeneralApi* | [**rearrangePages**](docs/Api/GeneralApi.md#rearrangepages) | **POST** /api/v1/general/rearrange-pages | Rearrange pages in a PDF file
*GeneralApi* | [**removeImages**](docs/Api/GeneralApi.md#removeimages) | **POST** /api/v1/general/remove-image-pdf | Remove images from file to reduce the file size.
*GeneralApi* | [**rotatePDF**](docs/Api/GeneralApi.md#rotatepdf) | **POST** /api/v1/general/rotate-pdf | Rotate a PDF file
*GeneralApi* | [**scalePages**](docs/Api/GeneralApi.md#scalepages) | **POST** /api/v1/general/scale-pages | Change the size of a PDF page/document
*GeneralApi* | [**splitPdf**](docs/Api/GeneralApi.md#splitpdf) | **POST** /api/v1/general/split-pdf-by-sections | Split PDF pages into smaller sections
*GeneralApi* | [**splitPdf1**](docs/Api/GeneralApi.md#splitpdf1) | **POST** /api/v1/general/split-pdf-by-chapters | Split PDFs by Chapters
*GeneralApi* | [**splitPdf2**](docs/Api/GeneralApi.md#splitpdf2) | **POST** /api/v1/general/split-pages | Split a PDF file into separate documents
*MiscApi* | [**addAttachments**](docs/Api/MiscApi.md#addattachments) | **POST** /api/v1/misc/add-attachments | Add attachments to PDF
*MiscApi* | [**addPageNumbers**](docs/Api/MiscApi.md#addpagenumbers) | **POST** /api/v1/misc/add-page-numbers | Add page numbers to a PDF document
*MiscApi* | [**addStamp**](docs/Api/MiscApi.md#addstamp) | **POST** /api/v1/misc/add-stamp | Add stamp to a PDF file
*MiscApi* | [**autoSplitPdf**](docs/Api/MiscApi.md#autosplitpdf) | **POST** /api/v1/misc/auto-split-pdf | Auto split PDF pages into separate documents
*MiscApi* | [**decompressPdf**](docs/Api/MiscApi.md#decompresspdf) | **POST** /api/v1/misc/decompress-pdf | Decompress PDF streams
*MiscApi* | [**extractHeader**](docs/Api/MiscApi.md#extractheader) | **POST** /api/v1/misc/show-javascript | Grabs all JS from a PDF and returns a single JS file with all code
*MiscApi* | [**extractHeader1**](docs/Api/MiscApi.md#extractheader1) | **POST** /api/v1/misc/auto-rename | Extract header from PDF file
*MiscApi* | [**extractImageScans**](docs/Api/MiscApi.md#extractimagescans) | **POST** /api/v1/misc/extract-image-scans | Extract image scans from an input file
*MiscApi* | [**extractImages**](docs/Api/MiscApi.md#extractimages) | **POST** /api/v1/misc/extract-images | Extract images from a PDF file
*MiscApi* | [**flatten**](docs/Api/MiscApi.md#flatten) | **POST** /api/v1/misc/flatten | Flatten PDF form fields or full page
*MiscApi* | [**metadata**](docs/Api/MiscApi.md#metadata) | **POST** /api/v1/misc/update-metadata | Update metadata of a PDF file
*MiscApi* | [**optimizePdf**](docs/Api/MiscApi.md#optimizepdf) | **POST** /api/v1/misc/compress-pdf | Optimize PDF file
*MiscApi* | [**overlayImage**](docs/Api/MiscApi.md#overlayimage) | **POST** /api/v1/misc/add-image | Overlay image onto a PDF file
*MiscApi* | [**processPdfWithOCR**](docs/Api/MiscApi.md#processpdfwithocr) | **POST** /api/v1/misc/ocr-pdf | Process a PDF file with OCR
*MiscApi* | [**removeBlankPages**](docs/Api/MiscApi.md#removeblankpages) | **POST** /api/v1/misc/remove-blanks | Remove blank pages from a PDF file
*MiscApi* | [**repairPdf**](docs/Api/MiscApi.md#repairpdf) | **POST** /api/v1/misc/repair | Repair a PDF file
*MiscApi* | [**replaceAndInvertColor**](docs/Api/MiscApi.md#replaceandinvertcolor) | **POST** /api/v1/misc/replace-invert-pdf | Replace-Invert Color PDF
*MiscApi* | [**scannerEffect**](docs/Api/MiscApi.md#scannereffect) | **POST** /api/v1/misc/scanner-effect | Apply scanner effect to PDF
*MiscApi* | [**unlockPDFForms**](docs/Api/MiscApi.md#unlockpdfforms) | **POST** /api/v1/misc/unlock-pdf-forms | Remove read-only property from form fields
*PipelineApi* | [**handleData**](docs/Api/PipelineApi.md#handledata) | **POST** /api/v1/pipeline/handleData | Execute automated PDF processing pipeline
*SecurityApi* | [**addPassword**](docs/Api/SecurityApi.md#addpassword) | **POST** /api/v1/security/add-password | Add password to a PDF file
*SecurityApi* | [**addWatermark**](docs/Api/SecurityApi.md#addwatermark) | **POST** /api/v1/security/add-watermark | Add watermark to a PDF file
*SecurityApi* | [**getPdfInfo**](docs/Api/SecurityApi.md#getpdfinfo) | **POST** /api/v1/security/get-info-on-pdf | Summary here
*SecurityApi* | [**redactPdfAuto**](docs/Api/SecurityApi.md#redactpdfauto) | **POST** /api/v1/security/auto-redact | Redacts listOfText in a PDF document
*SecurityApi* | [**redactPdfManual**](docs/Api/SecurityApi.md#redactpdfmanual) | **POST** /api/v1/security/redact | Redacts areas and pages in a PDF document
*SecurityApi* | [**removeCertSignPDF**](docs/Api/SecurityApi.md#removecertsignpdf) | **POST** /api/v1/security/remove-cert-sign | Remove digital signature from PDF
*SecurityApi* | [**removePassword**](docs/Api/SecurityApi.md#removepassword) | **POST** /api/v1/security/remove-password | Remove password from a PDF file
*SecurityApi* | [**sanitizePDF**](docs/Api/SecurityApi.md#sanitizepdf) | **POST** /api/v1/security/sanitize-pdf | Sanitize a PDF file
*SecurityApi* | [**signPDFWithCert**](docs/Api/SecurityApi.md#signpdfwithcert) | **POST** /api/v1/security/cert-sign | Sign PDF with a Digital Certificate
*SecurityApi* | [**validateSignature**](docs/Api/SecurityApi.md#validatesignature) | **POST** /api/v1/security/validate-signature | Validate PDF Digital Signature

## Models

- [ErrorResponse](docs/Model/ErrorResponse.md)
- [RedactionArea](docs/Model/RedactionArea.md)
- [ValidateSignature400Response](docs/Model/ValidateSignature400Response.md)
- [ValidateSignature413Response](docs/Model/ValidateSignature413Response.md)
- [ValidateSignature422Response](docs/Model/ValidateSignature422Response.md)
- [ValidateSignature500Response](docs/Model/ValidateSignature500Response.md)

## Authorization
Endpoints do not require authorization.

## Tests

To run the tests, use:

```bash
composer install
vendor/bin/phpunit
```

## Author

contact@stirlingpdf.com

## License

MIT - see [LICENSE](LICENSE) for details.

## Credits

This PHP package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project.

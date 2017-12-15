# Getting started

# APIMATIC CodeGen as a Service

[APIMATIC](https://apimatic.io) is an automatic code generator for RESTful APIs. This API exposes the access to its underlying code
generation engine. We currently support the following format for API descriptions, `API Blueprint`, `RAML`,
`Google API Discovery`, `IODocs`, `WADL`, and  `Swagger`. Although most API descriptions can be used, not all API
decsriptions are written well-enough for automatic code generation and may fail the code generation process.
For this purpose, we have provided a verbose validation API, which can be used to improve your API description.

> **Looking for a way to convert between API description formats like Swagger and API Blueprint?** Try [APIMATIC's Transformer API](http://docs.apimatictransformerapi.apiary.io/#) or it's web version at [Transformer](https://apimatic.io/transformer).

[APIMATIC](https://apimatic.io) works in two modes i.e., perform operations on **pre-configured** API descriptions, and perform 
operations on API descriptions sent **on the fly** with requests. The later mode of operations has its
limitations with respect to the customization of the generated code through our *codegen settings*.

See [this article](https://docs.apimatic.io/api-editor/codegen-settings/)
for more information about customization of the output code.

## Working with pre-configured API descriptions

This mode of operation is useful where APIs are stable and therefore can be pre-configured in [APIMATIC](https://apimatic.io).
You can always update an API description in [APIMATIC](https://apimatic.io) using the API Editor by clicking on the *Edit* button.
When working with stored API descriptions, pre-configured *codegen settings* are used that allow customization
of the generated output. In order to uniquely identify the API to perform operations on, an *API Key* is used,
which can be retrieved using the API context menu. This *API Key* is a secret value and therefore operations
on pre-configured API descriptions do not require authentication.

See [this article](https://docs.apimatic.io/getting-started/manage-apis/#view-api-integration-key)
on how to get your API Key from [APIMATIC](https://apimatic.io).

## Working with API descriptions documents

This mode of operation is useful in cases where API descriptions are automatically generated from a process
or external source and cannot be pre-configured in [APIMATIC](https://apimatic.io). In this case code generation uses the default
*codegen settings*. However, if custom *codegen settings* are desired you may use the [APIMATIC](https://apimatic.io) format for
generating your API descriptions, which contains nested *codegen settings*. For getting the full benefit
of our advanced features in our code generator, you must either pre-configure your API, or use [APIMATIC](https://apimatic.io)
format for API description.

# APIMATIC API Transformer

[APIMATIC](https://www.apimatic.io) Transformer allows its users to convert between different API description formats e.g. `Swagger`, `RAML`, etc. This enables the user to benefit from a wide range of tools available associated with any format, not just one. 
The complete list of supported formats of [Transformer](https://apimatic.io/transformer) are: 

Inputs  			| Outputs
------------------  | -------------------
API Blueprint		| API Blueprint
Swagger v.1.2		| Swagger 1.2
Swagger 2.0 (JSON and YAML)	| Swagger 2.0 (JSON, YAML)
Open API v.3.0 	| Open API 3.0
WADL 2009 (W3C)	| WADL 2009 (W3C)
WSDL (W3C)		| WSDL (W3C)
Google Discovery    | RAML 0.8 - 1.0	
RAML 0.8 - 1.0	    | Postman Collection 1.0 - 2.0
I/O Docs - Mashery	| APIMATIC Format	
HAR 1.2		|
Postman Collection 1.0 - 2.0	|
APIMATIC Format		|
Mashape		|

## How to Build

The generated code has dependencies over external libraries like UniRest. These dependencies are defined in the ```composer.json``` file that comes with the SDK. 
To resolve these dependencies, we use the Composer package manager which requires PHP greater than 5.3.2 installed in your system. 
Visit [https://getcomposer.org/download/](https://getcomposer.org/download/) to download the installer file for Composer and run it in your system. 
Open command prompt and type ```composer --version```. This should display the current version of the Composer installed if the installation was successful.

* Using command line, navigate to the directory containing the generated files (including ```composer.json```) for the SDK. 
* Run the command ```composer install```. This should install all the required dependencies and create the ```vendor``` directory in your project directory.

![Building SDK - Step 1](https://apidocs.io/illustration/php?step=installDependencies&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

### [For Windows Users Only] Configuring CURL Certificate Path in php.ini

CURL used to include a list of accepted CAs, but no longer bundles ANY CA certs. So by default it will reject all SSL certificates as unverifiable. You will have to get your CA's cert and point curl at it. The steps are as follows:

1. Download the certificate bundle (.pem file) from [https://curl.haxx.se/docs/caextract.html](https://curl.haxx.se/docs/caextract.html) on to your system.
2. Add curl.cainfo = "PATH_TO/cacert.pem" to your php.ini file located in your php installation. “PATH_TO” must be an absolute path containing the .pem file.

```ini
[curl]
; A default value for the CURLOPT_CAINFO option. This is required to be an
; absolute path.
;curl.cainfo =
```

## How to Use

The following section explains how to use the CodeGenAndTransformerAPI library in a new project.

### 1. Open Project in an IDE

Open an IDE for PHP like PhpStorm. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

![Open project in PHPStorm - Step 1](https://apidocs.io/illustration/php?step=openIDE&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Click on ```Open``` in PhpStorm to browse to your generated SDK directory and then click ```OK```.

![Open project in PHPStorm - Step 2](https://apidocs.io/illustration/php?step=openProject0&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)     

### 2. Add a new Test Project

Create a new directory by right clicking on the solution name as shown below:

![Add a new project in PHPStorm - Step 1](https://apidocs.io/illustration/php?step=createDirectory&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Name the directory as "test"

![Add a new project in PHPStorm - Step 2](https://apidocs.io/illustration/php?step=nameDirectory&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)
   
Add a PHP file to this project

![Add a new project in PHPStorm - Step 3](https://apidocs.io/illustration/php?step=createFile&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Name it "testSDK"

![Add a new project in PHPStorm - Step 4](https://apidocs.io/illustration/php?step=nameFile&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Depending on your project setup, you might need to include composer's autoloader in your PHP code to enable auto loading of classes.

```PHP
require_once "../vendor/autoload.php";
```

It is important that the path inside require_once correctly points to the file ```autoload.php``` inside the vendor directory created during dependency installations.

![Add a new project in PHPStorm - Step 4](https://apidocs.io/illustration/php?step=projectFiles&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

After this you can add code to initialize the client library and acquire the instance of a Controller class. Sample code to initialize the client library and using controller methods is given in the subsequent sections.

### 3. Run the Test Project

To run your project you must set the Interpreter for your project. Interpreter is the PHP engine installed on your computer.

Open ```Settings``` from ```File``` menu.

![Run Test Project - Step 1](https://apidocs.io/illustration/php?step=openSettings&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Select ```PHP``` from within ```Languages & Frameworks```

![Run Test Project - Step 2](https://apidocs.io/illustration/php?step=setInterpreter0&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Browse for Interpreters near the ```Interpreter``` option and choose your interpreter.

![Run Test Project - Step 3](https://apidocs.io/illustration/php?step=setInterpreter1&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

Once the interpreter is selected, click ```OK```

![Run Test Project - Step 4](https://apidocs.io/illustration/php?step=setInterpreter2&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

To run your project, right click on your PHP file inside your Test project and click on ```Run```

![Run Test Project - Step 5](https://apidocs.io/illustration/php?step=runProject&workspaceFolder=CodeGen%20and%20Transformer%20API-PHP)

## How to Test

Unit tests in this SDK can be run using PHPUnit. 

1. First install the dependencies using composer including the `require-dev` dependencies.
2. Run `vendor\bin\phpunit --verbose` from commandline to execute tests. If you have 
   installed PHPUnit globally, run tests using `phpunit --verbose` instead.

You can change the PHPUnit test configuration in the `phpunit.xml` file.

## Initialization

### Authentication
In order to setup authentication and initialization of the API client, you need the following information.

| Parameter | Description |
|-----------|-------------|
| basicAuthUserName | The username to use with basic authentication |
| basicAuthPassword | The password to use with basic authentication |



API client can be initialized as following.

```php
$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new CodeGenAndTransformerAPILib\CodeGenAndTransformerAPIClient($basicAuthUserName, $basicAuthPassword);
```


# Class Reference

## <a name="list_of_controllers"></a>List of Controllers

* [CodeGenerationController](#code_generation_controller)
* [APIDescriptionValidationController](#api_description_validation_controller)
* [APITransformerController](#api_transformer_controller)

## <a name="code_generation_controller"></a>![Class: ](https://apidocs.io/img/class.png ".CodeGenerationController") CodeGenerationController

### Get singleton instance

The singleton instance of the ``` CodeGenerationController ``` class can be accessed from the API Client.

```php
$codeGeneration = $client->getCodeGeneration();
```

### <a name="using_file_as_string"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.usingFileAsString") usingFileAsString

> The code generation endpoint. The response is a path to the generated zip file relative to https://apimatic.io/


```php
function usingFileAsString(
        $name,
        $format,
        $template,
        $body,
        $dl = 0)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| name |  ``` Required ```  | The name of the API being used for code generation |
| format |  ``` Required ```  | The format of the API description to use for code generation |
| template |  ``` Required ```  | The template to use for code generation |
| body |  ``` Required ```  | The input file to use for code generation |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |



#### Example Usage

```php
$name = 'name';
$format = string::ENUM_API BLUEPRINT;
$template = string::CS_PORTABLE_NET_LIB;
$body = "PathToFile";
$dl = 0;

$result = $codeGeneration->usingFileAsString($name, $format, $template, $body, $dl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_url_as_string"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.usingUrlAsString") usingUrlAsString

> The code generation endpoint. The response is a path to the generated zip file relative to https://apimatic.io/


```php
function usingUrlAsString(
        $template,
        $format,
        $name,
        $descriptionUrl,
        $dl = 0)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| template |  ``` Required ```  | The template to use for code generation |
| format |  ``` Required ```  | The format of the API description to use for code generation |
| name |  ``` Required ```  | The name of the API being used for code generation |
| descriptionUrl |  ``` Required ```  | The absolute public Uri for an API description doucment |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |



#### Example Usage

```php
$template = string::CS_PORTABLE_NET_LIB;
$format = string::ENUM_API BLUEPRINT;
$name = 'name';
$descriptionUrl = 'descriptionUrl';
$dl = 0;

$result = $codeGeneration->usingUrlAsString($template, $format, $name, $descriptionUrl, $dl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_file_as_binary"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.usingFileAsBinary") usingFileAsBinary

> The code generation endpoint! Upload a file and convert it to the given format. The API description format of uploaded file will be detected automatically. The response is generated zip file as per selected template.


```php
function usingFileAsBinary(
        $name,
        $format,
        $template,
        $body,
        $dl = 1)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| name |  ``` Required ```  | The name of the API being used for code generation |
| format |  ``` Required ```  | The format of the API description to use for code generation |
| template |  ``` Required ```  | The template to use for code generation |
| body |  ``` Required ```  | The input file to use for code generation |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |



#### Example Usage

```php
$name = 'name';
$format = string::ENUM_API BLUEPRINT;
$template = string::CS_PORTABLE_NET_LIB;
$body = "PathToFile";
$dl = 1;

$result = $codeGeneration->usingFileAsBinary($name, $format, $template, $body, $dl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_url_as_binary"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.usingUrlAsBinary") usingUrlAsBinary

> Download API description from the given URL and convert it to the given format. The API description format of the provided file will be detected automatically. The response is generated zip file as per selected template.


```php
function usingUrlAsBinary(
        $template,
        $format,
        $name,
        $descriptionUrl,
        $dl = 1)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| template |  ``` Required ```  | The template to use for code generation |
| format |  ``` Required ```  | The format of the API description to use for code generation |
| name |  ``` Required ```  | The name of the API being used for code generation |
| descriptionUrl |  ``` Required ```  | The absolute public Uri for an API description doucment |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |



#### Example Usage

```php
$template = string::CS_PORTABLE_NET_LIB;
$format = string::ENUM_API BLUEPRINT;
$name = 'name';
$descriptionUrl = 'descriptionUrl';
$dl = 1;

$result = $codeGeneration->usingUrlAsBinary($template, $format, $name, $descriptionUrl, $dl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_apikey_as_binary"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.usingApikeyAsBinary") usingApikeyAsBinary

> Convert an API from the user's account using the API's [API Integration Key](https://docs.apimatic.io/getting-started/manage-apis/#view-api-integration-key). The response is generated zip file as per selected template.
> > Note: This endpoint does not require Basic Authentication.


```php
function usingApikeyAsBinary(
        $apikey,
        $template,
        $dl = 1)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| apikey |  ``` Required ```  | The API Key of the pre-configured API |
| template |  ``` Required ```  | The template to use for code generation |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |



#### Example Usage

```php
$apikey = 'apikey';
$template = string::CS_PORTABLE_NET_LIB;
$dl = 1;

$result = $codeGeneration->usingApikeyAsBinary($apikey, $template, $dl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_apikey_as_string"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.usingApikeyAsString") usingApikeyAsString

> The code generation endpoint. The response is a path to the generated zip file relative to https://apimatic.io/
> > Note: This endpoint does not require Basic Authentication.


```php
function usingApikeyAsString(
        $apikey,
        $template,
        $dl = 0)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| apikey |  ``` Required ```  | The API Key of the pre-configured API |
| template |  ``` Required ```  | The template to use for code generation |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |



#### Example Usage

```php
$apikey = 'apikey';
$template = string::CS_PORTABLE_NET_LIB;
$dl = 0;

$result = $codeGeneration->usingApikeyAsString($apikey, $template, $dl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



[Back to List of Controllers](#list_of_controllers)

## <a name="api_description_validation_controller"></a>![Class: ](https://apidocs.io/img/class.png ".APIDescriptionValidationController") APIDescriptionValidationController

### Get singleton instance

The singleton instance of the ``` APIDescriptionValidationController ``` class can be accessed from the API Client.

```php
$aPIDescriptionValidation = $client->getAPIDescriptionValidation();
```

### <a name="using_file"></a>![Method: ](https://apidocs.io/img/method.png ".APIDescriptionValidationController.usingFile") usingFile

> This endpoint can be used to validate an API description document *on the fly* and see detailed error messages along with any warnings or useful information.


```php
function usingFile($body)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| body |  ``` Required ```  | The input file to use for validation |



#### Example Usage

```php
$body = "PathToFile";

$result = $aPIDescriptionValidation->usingFile($body);

```


### <a name="using_url"></a>![Method: ](https://apidocs.io/img/method.png ".APIDescriptionValidationController.usingUrl") usingUrl

> This endpoint can be used to validate an API description document *on the fly* from its public Uri, and see detailed error messages along with any warnings or useful information. This endpoint is useful for API descriptions with relative links e.g., includes (RAML) and paths (swagger).


```php
function usingUrl($descriptionUrl)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| descriptionUrl |  ``` Required ```  | The absolute public Uri for an API description doucment |



#### Example Usage

```php
$descriptionUrl = 'descriptionUrl';

$result = $aPIDescriptionValidation->usingUrl($descriptionUrl);

```


### <a name="using_apikey"></a>![Method: ](https://apidocs.io/img/method.png ".APIDescriptionValidationController.usingApikey") usingApikey

> This endpoint can be used to validate a *pre-configured* API description and see detailed error messages along with any warnings or useful information.


```php
function usingApikey($apikey)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| apikey |  ``` Required ```  | The API Key of a pre-configured API description from APIMATIC |



#### Example Usage

```php
$apikey = 'apikey';

$result = $aPIDescriptionValidation->usingApikey($apikey);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="api_transformer_controller"></a>![Class: ](https://apidocs.io/img/class.png ".APITransformerController") APITransformerController

### Get singleton instance

The singleton instance of the ``` APITransformerController ``` class can be accessed from the API Client.

```php
$aPITransformer = $client->getAPITransformer();
```

### <a name="using_apikey"></a>![Method: ](https://apidocs.io/img/method.png ".APITransformerController.usingApikey") usingApikey

> Convert an API from the user's account using the API's [Api Integration Key](https://docs.apimatic.io/getting-started/manage-apis/#view-api-integration-key). The converted file is returned as the response.
> > Note: This endpoint does not require Basic Authentication.


```php
function usingApikey(
        $format,
        $apikey)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  | The API format to convert to |
| apikey |  ``` Required ```  | Apikey of an already uploaded API Description on APIMATIC |



#### Example Usage

```php
$format = string::APIMATIC;
$apikey = 'apikey';

$result = $aPITransformer->usingApikey($format, $apikey);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |



### <a name="using_url"></a>![Method: ](https://apidocs.io/img/method.png ".APITransformerController.usingUrl") usingUrl

> Download API description from the given URL and convert it to the given format. The API description format of the provided file will be detected automatically. The converted file is returned as the response.


```php
function usingUrl(
        $format,
        $descriptionUrl)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  | The API format to convert to |
| descriptionUrl |  ``` Required ```  | The URL where the API description will be downloaded from |



#### Example Usage

```php
$format = string::APIMATIC;
$descriptionUrl = 'descriptionUrl';

$result = $aPITransformer->usingUrl($format, $descriptionUrl);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |



### <a name="using_file"></a>![Method: ](https://apidocs.io/img/method.png ".APITransformerController.usingFile") usingFile

> Upload a file and convert it to the given format. The API description format of the uploaded file will be detected automatically. The converted file is returned as the response.


```php
function usingFile(
        $format,
        $file)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  | The API format to convert to |
| file |  ``` Required ```  | The input file to convert |



#### Example Usage

```php
$format = string::APIMATIC;
$file = "PathToFile";

$result = $aPITransformer->usingFile($format, $file);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |



[Back to List of Controllers](#list_of_controllers)




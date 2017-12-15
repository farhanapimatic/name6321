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

This client library is a Ruby gem which can be compiled and used in your Ruby and Ruby on Rails project. This library requires a few gems from the RubyGems repository.

1. Open the command line interface or the terminal and navigate to the folder containing the source code.
2. Run ``` gem build code_gen_and_transformer_api.gemspec ``` to build the gem.
3. Once built, the gem can be installed on the current work environment using ``` gem install code_gen_and_transformer_api-1.0.0.gem ```

![Building Gem](https://apidocs.io/illustration/ruby?step=buildSDK&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGen%20and%20Transformer%20API-Ruby&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

## How to Use

The following section explains how to use the CodeGenAndTransformerApi Ruby Gem in a new Rails project using RubyMine&trade;. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

### 1. Starting a new project

Close any existing projects in RubyMine&trade; by selecting ``` File -> Close Project ```. Next, click on ``` Create New Project ``` to create a new project from scratch.

![Create a new project in RubyMine](https://apidocs.io/illustration/ruby?step=createNewProject0&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

Next, provide ``` TestApp ``` as the project name, choose ``` Rails Application ``` as the project type, and click ``` OK ```.

![Create a new Rails Application in RubyMine - step 1](https://apidocs.io/illustration/ruby?step=createNewProject1&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

In the next dialog make sure that correct *Ruby SDK* is being used (minimum 2.0.0) and click ``` OK ```.

![Create a new Rails Application in RubyMine - step 2](https://apidocs.io/illustration/ruby?step=createNewProject2&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

This will create a new Rails Application project with an existing set of files and folder.

### 2. Add reference of the gem

In order to use the CodeGenAndTransformerApi gem in the new project we must add a gem reference. Locate the ```Gemfile``` in the *Project Explorer* window under the ``` TestApp ``` project node. The file contains references to all gems being used in the project. Here, add the reference to the library gem by adding the following line: ``` gem 'code_gen_and_transformer_api', '~> 1.0.0' ```

![Add references of the Gemfile](https://apidocs.io/illustration/ruby?step=addReference&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

### 3. Adding a new Rails Controller

Once the ``` TestApp ``` project is created, a folder named ``` controllers ``` will be visible in the *Project Explorer* under the following path: ``` TestApp > app > controllers ```. Right click on this folder and select ``` New -> Run Rails Generator... ```.

![Run Rails Generator on Controllers Folder](https://apidocs.io/illustration/ruby?step=addCode0&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

Selecting the said option will popup a small window where the generator names are displayed. Here, select the ``` controller ``` template.

![Create a new Controller](https://apidocs.io/illustration/ruby?step=addCode1&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

Next, a popup window will ask you for a Controller name and included Actions. For controller name provide ``` Hello ``` and include an action named ``` Index ``` and click ``` OK ```.

![Add a new Controller](https://apidocs.io/illustration/ruby?step=addCode2&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

A new controller class anmed ``` HelloController ``` will be created in a file named ``` hello_controller.rb ``` containing a method named ``` Index ```. In this method, add code for initialization and a sample for its usage.

![Initialize the library](https://apidocs.io/illustration/ruby?step=addCode3&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0)

## How to Test

You can test the generated SDK and the server with automatically generated test
cases as follows:

  1. From terminal/cmd navigate to the root directory of the SDK.
  2. Invoke: `bundle exec rake`

## Initialization

### Authentication
In order to setup authentication and initialization of the API client, you need the following information.

| Parameter | Description |
|-----------|-------------|
| basic_auth_user_name | The username to use with basic authentication |
| basic_auth_password | The password to use with basic authentication |



API client can be initialized as following.

```ruby
# Configuration parameters and credentials
basic_auth_user_name = 'basic_auth_user_name' # The username to use with basic authentication
basic_auth_password = 'basic_auth_password' # The password to use with basic authentication

client = CodeGenAndTransformerApi::CodeGenAndTransformerApiClient.new(
  basic_auth_user_name: basic_auth_user_name,
  basic_auth_password: basic_auth_password
)
```

The added initlization code can be debugged by putting a breakpoint in the ``` Index ``` method and running the project in debug mode by selecting ``` Run -> Debug 'Development: TestApp' ```.

![Debug the TestApp](https://apidocs.io/illustration/ruby?step=addCode4&workspaceFolder=CodeGen%20and%20Transformer%20API-Ruby&workspaceName=CodeGenAndTransformerApi&projectName=code_gen_and_transformer_api&gemName=code_gen_and_transformer_api&gemVer=1.0.0&initLine=client%2520%253D%2520CodeGenAndTransformerApiClient.new%2528%2527basic_auth_user_name%2527%252C%2520%2527basic_auth_password%2527%2529)



# Class Reference

## <a name="list_of_controllers"></a>List of Controllers

* [CodeGenerationController](#code_generation_controller)
* [APIDescriptionValidationController](#api_description_validation_controller)
* [APITransformerController](#api_transformer_controller)

## <a name="code_generation_controller"></a>![Class: ](https://apidocs.io/img/class.png ".CodeGenerationController") CodeGenerationController

### Get singleton instance

The singleton instance of the ``` CodeGenerationController ``` class can be accessed from the API Client.

```ruby
codeGeneration_controller = client.code_generation
```

### <a name="using_file_as_string"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.using_file_as_string") using_file_as_string

> The code generation endpoint. The response is a path to the generated zip file relative to https://apimatic.io/


```ruby
def using_file_as_string(name,
                             format,
                             template,
                             body,
                             dl = 0); end
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

```ruby
name = 'name'
format = CodeGenAndTransformerApi::Format::ENUM_API BLUEPRINT
template = CodeGenAndTransformerApi::Template::CS_PORTABLE_NET_LIB
body = Faraday::UploadIO.new('PathToFile', 'application/octet-stream')
dl = 0

result = codeGeneration_controller.using_file_as_string(name, format, template, body, dl)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_url_as_string"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.using_url_as_string") using_url_as_string

> The code generation endpoint. The response is a path to the generated zip file relative to https://apimatic.io/


```ruby
def using_url_as_string(template,
                            format,
                            name,
                            description_url,
                            dl = 0); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| template |  ``` Required ```  | The template to use for code generation |
| format |  ``` Required ```  | The format of the API description to use for code generation |
| name |  ``` Required ```  | The name of the API being used for code generation |
| description_url |  ``` Required ```  | The absolute public Uri for an API description doucment |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |


#### Example Usage

```ruby
template = CodeGenAndTransformerApi::Template::CS_PORTABLE_NET_LIB
format = CodeGenAndTransformerApi::Format::ENUM_API BLUEPRINT
name = 'name'
description_url = 'descriptionUrl'
dl = 0

result = codeGeneration_controller.using_url_as_string(template, format, name, description_url, dl)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_file_as_binary"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.using_file_as_binary") using_file_as_binary

> The code generation endpoint! Upload a file and convert it to the given format. The API description format of uploaded file will be detected automatically. The response is generated zip file as per selected template.


```ruby
def using_file_as_binary(name,
                             format,
                             template,
                             body,
                             dl = 1); end
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

```ruby
name = 'name'
format = CodeGenAndTransformerApi::Format::ENUM_API BLUEPRINT
template = CodeGenAndTransformerApi::Template::CS_PORTABLE_NET_LIB
body = Faraday::UploadIO.new('PathToFile', 'application/octet-stream')
dl = 1

result = codeGeneration_controller.using_file_as_binary(name, format, template, body, dl)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_url_as_binary"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.using_url_as_binary") using_url_as_binary

> Download API description from the given URL and convert it to the given format. The API description format of the provided file will be detected automatically. The response is generated zip file as per selected template.


```ruby
def using_url_as_binary(template,
                            format,
                            name,
                            description_url,
                            dl = 1); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| template |  ``` Required ```  | The template to use for code generation |
| format |  ``` Required ```  | The format of the API description to use for code generation |
| name |  ``` Required ```  | The name of the API being used for code generation |
| description_url |  ``` Required ```  | The absolute public Uri for an API description doucment |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |


#### Example Usage

```ruby
template = CodeGenAndTransformerApi::Template::CS_PORTABLE_NET_LIB
format = CodeGenAndTransformerApi::Format::ENUM_API BLUEPRINT
name = 'name'
description_url = 'descriptionUrl'
dl = 1

result = codeGeneration_controller.using_url_as_binary(template, format, name, description_url, dl)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_apikey_as_binary"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.using_apikey_as_binary") using_apikey_as_binary

> Convert an API from the user's account using the API's [API Integration Key](https://docs.apimatic.io/getting-started/manage-apis/#view-api-integration-key). The response is generated zip file as per selected template.
> > Note: This endpoint does not require Basic Authentication.


```ruby
def using_apikey_as_binary(apikey,
                               template,
                               dl = 1); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| apikey |  ``` Required ```  | The API Key of the pre-configured API |
| template |  ``` Required ```  | The template to use for code generation |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |


#### Example Usage

```ruby
apikey = 'apikey'
template = CodeGenAndTransformerApi::Template::CS_PORTABLE_NET_LIB
dl = 1

result = codeGeneration_controller.using_apikey_as_binary(apikey, template, dl)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 401 | Unauthorized: Access is denied due to invalid credentials. |
| 412 | Precondition Failed |



### <a name="using_apikey_as_string"></a>![Method: ](https://apidocs.io/img/method.png ".CodeGenerationController.using_apikey_as_string") using_apikey_as_string

> The code generation endpoint. The response is a path to the generated zip file relative to https://apimatic.io/
> > Note: This endpoint does not require Basic Authentication.


```ruby
def using_apikey_as_string(apikey,
                               template,
                               dl = 0); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| apikey |  ``` Required ```  | The API Key of the pre-configured API |
| template |  ``` Required ```  | The template to use for code generation |
| dl |  ``` Optional ```  ``` DefaultValue ```  | Optional |


#### Example Usage

```ruby
apikey = 'apikey'
template = CodeGenAndTransformerApi::Template::CS_PORTABLE_NET_LIB
dl = 0

result = codeGeneration_controller.using_apikey_as_string(apikey, template, dl)

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

```ruby
aPIDescriptionValidation_controller = client.api_description_validation
```

### <a name="using_file"></a>![Method: ](https://apidocs.io/img/method.png ".APIDescriptionValidationController.using_file") using_file

> This endpoint can be used to validate an API description document *on the fly* and see detailed error messages along with any warnings or useful information.


```ruby
def using_file(body); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| body |  ``` Required ```  | The input file to use for validation |


#### Example Usage

```ruby
body = Faraday::UploadIO.new('PathToFile', 'application/octet-stream')

result = aPIDescriptionValidation_controller.using_file(body)

```


### <a name="using_url"></a>![Method: ](https://apidocs.io/img/method.png ".APIDescriptionValidationController.using_url") using_url

> This endpoint can be used to validate an API description document *on the fly* from its public Uri, and see detailed error messages along with any warnings or useful information. This endpoint is useful for API descriptions with relative links e.g., includes (RAML) and paths (swagger).


```ruby
def using_url(description_url); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| description_url |  ``` Required ```  | The absolute public Uri for an API description doucment |


#### Example Usage

```ruby
description_url = 'descriptionUrl'

result = aPIDescriptionValidation_controller.using_url(description_url)

```


### <a name="using_apikey"></a>![Method: ](https://apidocs.io/img/method.png ".APIDescriptionValidationController.using_apikey") using_apikey

> This endpoint can be used to validate a *pre-configured* API description and see detailed error messages along with any warnings or useful information.


```ruby
def using_apikey(apikey); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| apikey |  ``` Required ```  | The API Key of a pre-configured API description from APIMATIC |


#### Example Usage

```ruby
apikey = 'apikey'

result = aPIDescriptionValidation_controller.using_apikey(apikey)

```


[Back to List of Controllers](#list_of_controllers)

## <a name="api_transformer_controller"></a>![Class: ](https://apidocs.io/img/class.png ".APITransformerController") APITransformerController

### Get singleton instance

The singleton instance of the ``` APITransformerController ``` class can be accessed from the API Client.

```ruby
aPITransformer_controller = client.api_transformer
```

### <a name="using_apikey"></a>![Method: ](https://apidocs.io/img/method.png ".APITransformerController.using_apikey") using_apikey

> Convert an API from the user's account using the API's [Api Integration Key](https://docs.apimatic.io/getting-started/manage-apis/#view-api-integration-key). The converted file is returned as the response.
> > Note: This endpoint does not require Basic Authentication.


```ruby
def using_apikey(format,
                     apikey); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  | The API format to convert to |
| apikey |  ``` Required ```  | Apikey of an already uploaded API Description on APIMATIC |


#### Example Usage

```ruby
format = CodeGenAndTransformerApi::FormatTransformer::APIMATIC
apikey = 'apikey'

result = aPITransformer_controller.using_apikey(format, apikey)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |



### <a name="using_url"></a>![Method: ](https://apidocs.io/img/method.png ".APITransformerController.using_url") using_url

> Download API description from the given URL and convert it to the given format. The API description format of the provided file will be detected automatically. The converted file is returned as the response.


```ruby
def using_url(format,
                  description_url); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  | The API format to convert to |
| description_url |  ``` Required ```  | The URL where the API description will be downloaded from |


#### Example Usage

```ruby
format = CodeGenAndTransformerApi::FormatTransformer::APIMATIC
description_url = 'descriptionUrl'

result = aPITransformer_controller.using_url(format, description_url)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |



### <a name="using_file"></a>![Method: ](https://apidocs.io/img/method.png ".APITransformerController.using_file") using_file

> Upload a file and convert it to the given format. The API description format of the uploaded file will be detected automatically. The converted file is returned as the response.


```ruby
def using_file(format,
                   file); end
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  | The API format to convert to |
| file |  ``` Required ```  | The input file to convert |


#### Example Usage

```ruby
format = CodeGenAndTransformerApi::FormatTransformer::APIMATIC
file = Faraday::UploadIO.new('PathToFile', 'application/octet-stream')

result = aPITransformer_controller.using_file(format, file)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |



[Back to List of Controllers](#list_of_controllers)




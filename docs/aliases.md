# Working with Aliases in Amazon Lambda
[[  Overview ]](#overview)  [[ Operation details ]](#operation-details)  [[  Sample configuration  ]](#sample-configuration)

### Overview
The following operations allow you to work with Aliases in Amazon Lambda. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with Aliases, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createAlias](#creating-an-alias)    | Creates an alias for a Lambda function version. |
| [deleteAlias](#deleting-an-alias)    | Deletes a Lambda function alias. |
| [getAlias](#getting-details-about-lambda-function-alias)      | Returns details about a Lambda function alias.  |
| [updateAlias](#updating-an-alias-configuration)     | Updates the configuration of a Lambda function alias.  |

## Operation details
This section provides details on each of the operations.

## Creating an alias
The createAlias implementation of the POST operation creates an alias for a Lambda function version. Use aliases to provide clients with a function identifier that you can update to invoke a different version. You can also map an alias to split invocation requests between two versions. Use the RoutingConfig parameter to specify a second version and the percentage of invocation requests that it receives.

**createAlias**
```xml
<amazonlambda.createAlias>
    <functionName>{$ctx:functionName}</functionName>
    <createAliasDescription>{$ctx:createAliasDescription}</createAliasDescription>
    <functionVersion>{$ctx:functionVersion}</functionVersion>
    <aliasName>{$ctx:aliasName}</aliasName>
    <aliasAdditionalVersionWeights>{$ctx:aliasAdditionalVersionWeights}</aliasAdditionalVersionWeights>
    <apiVersionCreateAlias>{$ctx:apiVersionCreateAlias}</apiVersionCreateAlias>
</amazonlambda.createAlias>
```

**Properties**
* apiVersionCreateAlias : API version for CreateAlias method.
* functionName : The name of the Lambda function that the alias invokes.
* createAliasDescription : The description of the alias.
* functionVersion : The function version that the alias invokes.
* aliasName : The name of the alias.
* aliasAdditionalVersionWeights : The name of second alias, and the percentage of traffic that's routed to it.

**Sample request**

Following is a sample REST request that can be handled by the createAlias operation.
```json
{
    "secretAccessKey":"0b+fcboKq87Nf7mH6M**********************",
    "accessKeyId":"AKIAJHJ*************",
    "region":"us-east-2",
    "blocking":"false",
    "functionName":"test",
    "functionVersion":"$LATEST",
    "aliasName":"alias2",
    "apiVersionCreateAlias":"2015-03-31"
}
```

**Sample response**

Given below is a sample response for the createAlias operation.

```json
{
    "AliasArn": "arn:aws:lambda:us-east-2:********:function:test:alias2",
    "Description": "",
    "FunctionVersion": "$LATEST",
    "Name": "alias2",
    "RevisionId": "be8925ae-a634-4303-92e2-5364d0724406",
    "RoutingConfig": null
}
```

**Related Amazon Lambda documentation**
[https://docs.aws.amazon.com/lambda/latest/dg/API_CreateAlias.html](https://docs.aws.amazon.com/lambda/latest/dg/API_CreateAlias.html)

## Deleting an alias
The deleteAlias implementation deletes a Lambda function alias.

**deleteAlias**
```xml
<amazonlambda.deleteAlias>
    <functionName>{$ctx:functionName}</functionName>
    <aliasName>{$ctx:aliasName}</aliasName>
    <apiVersionDeleteAlias>{$ctx:apiVersionDeleteAlias}</apiVersionDeleteAlias>
</amazonlambda.deleteAlias>
```

**Properties**
* apiVersionDeleteAlias : API version for DeleteAlias method.
* functionName : The name of the Lambda function that the alias invokes.
* aliasName : The name of the alias.

**Sample request**

Following is a sample REST request that can be handled by the deleteAlias operation.
```json
{
  "secretAccessKey":"0b+fcboKq87Nf7mH6M**********************",
  "accessKeyId":"AKIAJHJ*************",
  "region":"us-east-2",
  "blocking":"false",
  "functionName":"test",
  "aliasName":"alias2",
  "apiVersionDeleteAlias":"2015-03-31"
}
```

**Sample response**

Given below is a sample response for the deleteAlias operation.

    Status: 204 No Content
    
**Related Amazon Lambda documentation**
[https://docs.aws.amazon.com/lambda/latest/dg/API_DeleteAlias.html](https://docs.aws.amazon.com/lambda/latest/dg/API_DeleteAlias.html)

## Getting details about Lambda function alias
The getAlias implementation of the GET operation returns details about a Lambda function alias.

**getAlias**
```xml
<amazonlambda.getAlias>
    <functionName>{$ctx:functionName}</functionName>
    <aliasName>{$ctx:aliasName}</aliasName>
    <apiVersionGetAlias>{$ctx:apiVersionGetAlias}</apiVersionGetAlias>    
</amazonlambda.getAlias>
```

**Properties**
* functionName : The name of the Lambda function that the alias invokes.
* aliasName : The name of the alias.
* apiVersionGetAlias : API version for GetAlias method.

**Sample request**

Following is a sample REST request that can be handled by the getAlias operation.
```json
{
  "secretAccessKey":"0b+fcboKq87Nf7mH6M**********************",
  "accessKeyId":"AKIAJHJ*************",
  "region":"us-east-2",
  "blocking":"false",
  "functionName":"test",
  "aliasName":"alias2",
  "apiVersionGetAlias":"2015-03-31"
}
```

**Sample response**

Given below is a sample response for the getAlias operation.

    Status: 200 OK
```json
{
    "AliasArn": "arn:aws:lambda:us-east-2:********:function:test:alias2",
    "Description": "",
    "FunctionVersion": "$LATEST",
    "Name": "alias2",
    "RevisionId": "be8925ae-a634-4303-92e2-5364d0724406",
    "RoutingConfig": null
}
```

**Related Amazon Lambda documentation**
[https://docs.aws.amazon.com/lambda/latest/dg/API_GetAlias.html](https://docs.aws.amazon.com/lambda/latest/dg/API_GetAlias.html)

## Updating an alias configuration
The updateAlias method implementation updates the configuration of a Lambda function alias.

**updateAlias**
```xml
<amazonlambda.updateAlias>
    <functionName>{$ctx:functionName}</functionName>
    <updatedAliasDescription>{$ctx:updatedAliasDescription}</updatedAliasDescription>
    <functionVersion>{$ctx:functionVersion}</functionVersion>
    <aliasName>{$ctx:aliasName}</aliasName>
    <updatedAliasAdditionalVersionWeight>{$ctx:updatedAliasAdditionalVersionWeight}</updatedAliasAdditionalVersionWeight>
    <apiVersionUpdateAlias>{$ctx:apiVersionUpdateAlias}</apiVersionUpdateAlias>
</amazonlambda.updateAlias>
```

**Properties**
* functionName : The name of the Lambda function that the alias invokes.
* updatedAliasDescription : The description of the alias.
* functionVersion : The function version that the alias invokes.
* aliasName : The name of the alias.
* updatedAliasAdditionalVersionWeight : The name of second alias, and the percentage of traffic that's routed to it.
* apiVersionUpdateAlias : API version for UpdateAlias method.

**Sample request**

Following is a sample REST request that can be handled by the updateAlias operation.
```json
{
  "secretAccessKey":"0b+fcboKq87Nf7mH6M**********************",
  "accessKeyId":"AKIAJHJ*************",
  "region":"us-east-1",
  "blocking":"false",
  "functionName":"test",
  "aliasName":"alias2",
  "functionVersion":"$LATEST",
  "apiVersionUpdateAlias":"2015-03-31"
}
```

**Sample response**

Given below is a sample response for the updateAlias operation.

    Status: 200 OK
```json
{
    "AliasArn": "arn:aws:lambda:us-east-2:*********:function:test:alias2",
    "Description": "",
    "FunctionVersion": "$LATEST",
    "Name": "alias2",
    "RevisionId": "6d8d089b-c632-4a4b-91ba-ee1ce706c50a",
    "RoutingConfig": null
}
```

**Related Amazon Lambda documentation**
[https://docs.aws.amazon.com/lambda/latest/dg/API_UpdateAlias.html](https://docs.aws.amazon.com/lambda/latest/dg/API_UpdateAlias.html)

## Sample configuration
Following is a sample proxy service that illustrates how to connect to Amazon Lambda with init operation and use the createAlias operation. The sample request for this proxy can be found in createAlias sample request. You can use this sample as a template for using other operations in this category.

1. Create a sample proxy as below
    
**Sample Proxy**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="amazonlambda_createAlias"       
       startOnLoad="true"
       statistics="disable"
       trace="disable"
       transports="https, http">
   <target>
      <inSequence>
         <property expression="json-eval($.secretAccessKey)" name="secretAccessKey"/>
         <property expression="json-eval($.accessKeyId)" name="accessKeyId"/>
         <property expression="json-eval($.region)" name="region"/>
         <property expression="json-eval($.blocking)" name="blocking"/>
         <property expression="json-eval($.functionName)" name="functionName"/>
         <property expression="json-eval($.createAliasDescription)" name="createAliasDescription"/>
         <property expression="json-eval($.functionVersion)" name="functionVersion"/>
         <property expression="json-eval($.aliasName)" name="aliasName"/>
         <property expression="json-eval($.aliasAdditionalVersionWeights)" name="aliasAdditionalVersionWeights"/>
         <property expression="json-eval($.apiVersionCreateAlias)" name="apiVersionCreateAlias"/>
         <amazonlambda.init>
            <secretAccessKey>{$ctx:secretAccessKey}</secretAccessKey>
            <accessKeyId>{$ctx:accessKeyId}</accessKeyId>
            <region>{$ctx:region}</region>
            <blocking>{$ctx:blocking}</blocking>
         </amazonlambda.init>
         <amazonlambda.createAlias>
            <functionName>{$ctx:functionName}</functionName>	   
            <createAliasDescription>{$ctx:createAliasDescription}</createAliasDescription>
            <functionVersion>{$ctx:functionVersion}</functionVersion>
            <aliasName>{$ctx:aliasName}</aliasName>
            <aliasAdditionalVersionWeights>{$ctx:aliasAdditionalVersionWeights}</aliasAdditionalVersionWeights>
            <apiVersionCreateAlias>{$ctx:apiVersionCreateAlias}</apiVersionCreateAlias>
         </amazonlambda.createAlias>           
         <respond/>
      </inSequence>
   </target>
   <description/>
</proxy>
```
2. Create a json file named createAlias.json and copy the configurations given below to it:
```json
{
    "accessKeyId":"AKIAxxxxxxxxxxxx",
    "secretAccessKey":"id4qxxxxxxxx",
    "region":"us-east-1",
    "blocking":"false",
    "functionName":"createdFuncLast",
    "functionVersion":"$LATEST",
    "aliasName":"aliasJ7",
    "apiVersionCreateAlias":"2015-03-31"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/amazonlambda_createAlias -H "Content-Type: application/json" -d @createAlias.json
```
5. Amazon Lambda returns a json response similar to the one shown below:
 
```json
{
    "AliasArn": "arn:aws:lambda:us-east-2:*******:function:createdFuncLast:aliasJ7",
    "Description": "",
    "FunctionVersion": "$LATEST",
    "Name": "aliasJ7",
    "RevisionId": "f1e5fc6e-752d-408d-9e1e-367bef0cd681",
    "RoutingConfig": null
}

```

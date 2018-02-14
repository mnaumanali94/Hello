# Getting started

API to automatically deploy packages to repos

## How to Build

The generated code uses the Newtonsoft Json.NET NuGet Package. If the automatic NuGet package restore
is enabled, these dependencies will be installed automatically. Therefore,
you will need internet access for build.

"This library requires Visual Studio 2017 for compilation."
1. Open the solution (PackageDeployment.sln) file.
2. Invoke the build process using `Ctrl+Shift+B` shortcut key or using the `Build` menu as shown below.

![Building SDK using Visual Studio](https://apidocs.io/illustration/cs?step=buildSDK&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

## How to Use

The build process generates a portable class library, which can be used like a normal class library. The generated library is compatible with Windows Forms, Windows RT, Windows Phone 8,
Silverlight 5, Xamarin iOS, Xamarin Android and Mono. More information on how to use can be found at the [MSDN Portable Class Libraries documentation](http://msdn.microsoft.com/en-us/library/vstudio/gg597391%28v=vs.100%29.aspx).

The following section explains how to use the PackageDeployment library in a new console project.

### 1. Starting a new project

For starting a new project, right click on the current solution from the *solution explorer* and choose  ``` Add -> New Project ```.

![Add a new project in the existing solution using Visual Studio](https://apidocs.io/illustration/cs?step=addProject&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

Next, choose "Console Application", provide a ``` TestConsoleProject ``` as the project name and click ``` OK ```.

![Create a new console project using Visual Studio](https://apidocs.io/illustration/cs?step=createProject&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

### 2. Set as startup project

The new console project is the entry point for the eventual execution. This requires us to set the ``` TestConsoleProject ``` as the start-up project. To do this, right-click on the  ``` TestConsoleProject ``` and choose  ``` Set as StartUp Project ``` form the context menu.

![Set the new cosole project as the start up project](https://apidocs.io/illustration/cs?step=setStartup&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

### 3. Add reference of the library project

In order to use the PackageDeployment library in the new project, first we must add a projet reference to the ``` TestConsoleProject ```. First, right click on the ``` References ``` node in the *solution explorer* and click ``` Add Reference... ```.

![Open references of the TestConsoleProject](https://apidocs.io/illustration/cs?step=addReference&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

Next, a window will be displayed where we must set the ``` checkbox ``` on ``` PackageDeployment.Standard ``` and click ``` OK ```. By doing this, we have added a reference of the ```PackageDeployment.Standard``` project into the new ``` TestConsoleProject ```.

![Add a reference to the TestConsoleProject](https://apidocs.io/illustration/cs?step=createReference&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

### 4. Write sample code

Once the ``` TestConsoleProject ``` is created, a file named ``` Program.cs ``` will be visible in the *solution explorer* with an empty ``` Main ``` method. This is the entry point for the execution of the entire solution.
Here, you can add code to initialize the client library and acquire the instance of a *Controller* class. Sample code to initialize the client library and using controller methods is given in the subsequent sections.

![Add a reference to the TestConsoleProject](https://apidocs.io/illustration/cs?step=addCode&workspaceFolder=PackageDeployment-CSharp&workspaceName=PackageDeployment&projectName=PackageDeployment.Standard)

## How to Test

The generated SDK also contain one or more Tests, which are contained in the Tests project.
In order to invoke these test cases, you will need *NUnit 3.0 Test Adapter Extension for Visual Studio*.
Once the SDK is complied, the test cases should appear in the Test Explorer window.
Here, you can click *Run All* to execute these test cases.

## Initialization

### 

API client can be initialized as following.

```csharp

PackageDeploymentClient client = new PackageDeploymentClient();
```



# Class Reference

## <a name="list_of_controllers"></a>List of Controllers

* [APIController](#api_controller)

## <a name="api_controller"></a>![Class: ](https://apidocs.io/img/class.png "PackageDeployment.Standard.Controllers.APIController") APIController

### Get singleton instance

The singleton instance of the ``` APIController ``` class can be accessed from the API Client.

```csharp
APIController client = client.Client;
```

### <a name="create_publish_package"></a>![Method: ](https://apidocs.io/img/method.png "PackageDeployment.Standard.Controllers.APIController.CreatePublishPackage") CreatePublishPackage

> Used to publish package for supported languages


```csharp
Task<string> CreatePublishPackage(
        string language,
        FileStreamInfo apiDescription,
        string password,
        string email = null,
        string username = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| language |  ``` Required ```  | Language whose SDK is to be published |
| apiDescription |  ``` Required ```  | API description for the SDK that needs to be  published |
| password |  ``` Required ```  | password of the  deployment account |
| email |  ``` Optional ```  | Email of the deployment account |
| username |  ``` Optional ```  | Username of Deployment account |


#### Example Usage

```csharp
string language = "language";
FileStreamInfo apiDescription = new FileStreamInfo(new FileStream(@"pathToFile",FileMode.Open));
string password = "password";
string email = "email";
string username = "username";

string result = await client.CreatePublishPackage(language, apiDescription, password, email, username);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Bad Request |


[Back to List of Controllers](#list_of_controllers)




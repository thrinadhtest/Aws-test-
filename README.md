<div id="top"></div>
<!-- PROJECT LOGO -->
<br />
<div align="center">
  <h2 align="center">LMS Module</h2>
</div>

<!-- TABLE OF CONTENTS -->
<br />
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a></li>
    <li>
        <a href="#built-with">Built With</a>
        <ul>
            <li><a href="#back-end">Back-End</a></li>
            <li><a href="#infrastructure">Infrastructure</a></li>
        </ul>
        <a href="#architecture">Architecture</a>
    </li>
    <li>
        <a href="#getting-started">Getting Started</a>
        <ul>
            <li><a href="#prerequisites">Prerequisites</a></li>
            <li><a href="#installation">Installation</a></li>
        </ul>
    </li>
    <li><a href="#contributing">Contributing</a></li> 
  </ol>
</details>

<!-- ABOUT THE Project -->
<br />

## About The Project

The <b>LMS</b> system allows users to manage third party Learning content. It does so by providing services like content recommendation, progress tracking, and periodic content updates.

### Built With
Libraries, technologies, and Azure Services were used to build this Module.

#### Back-End
* [C# - Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/).
* [C# - Net 6.0](https://docs.microsoft.com/en-us/dotnet/core/whats-new/dotnet-6).
* [C# - Azure Durable Functions](https://docs.microsoft.com/en-us/azure/azure-functions/durable/durable-functions-overview?tabs=csharp).

#### Dependencies
* [ElasticSearch](https://www.elastic.co/)
* Core API
* [Go1 API](https://www.go1.com/developers/api/reference/v2)

#### Infrastructure
* [Azure App Service](https://azure.microsoft.com/es-es/services/app-service/).
* [Azure API Management](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts).
* [Azure Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview).
* [Azure Database for PostgreSQL](https://learn.microsoft.com/en-us/azure/postgresql/single-server/overview-single-server)
* [Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/overview).

### Architecture
![image](https://user-images.githubusercontent.com/21251321/196698167-867aa0d2-6fbc-4dce-8de4-151733c3cb4a.png)

<!-- GETTING STARTED -->
## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites
- Access to KFDEV-CONNECT VPN
- [NET 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)
- Preferred IDE (Recommended [Visual Studio 2022](https://visualstudio.microsoft.com/vs/))
- SQL Client Application with PostgreSQL support (Recommended [DBeaver](https://dbeaver.io/) / [PGAdmin](https://www.pgadmin.org/))

### Installation

Backend 

 - Create a `local.settings.json` file in the project's root directory         
 - Add the following values:
 
 ```
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "FUNCTIONS_WORKER_RUNTIME": "dotnet",
    "AZURE_TENANT_ID": "<Azure Tenant Id>",
    "AZURE_CLIENT_ID": "<Azure Client Id>",
    "AZURE_CLIENT_SECRET": "<Azure Client Secret>",
    "AppConfigurationEndpoint": "<App Config url>"
  },
  "Host": {
    "LocalHttpPort": 7071,
    "CORS": "*",
    "CORSCredentials": false
  },
}
```
- To use your local Postgres DB, follow the [DB setup README file](src\KornFerry.IntelligenceCloud.LMS\KornFerry.IntelligenceCloud.LMS.DataAccess\README.md)
- Restore NuGet packages (you have to be connected to the VPN)
- Build and run the project

> **_NOTE:_**  To fill the azure variables in the local.settings.json file, you will need an Azure Service Principal with access to the App Configuration resource and all other resources used by the module.

<!-- CONTRIBUTING -->
## Contributing

### Feature branches
Used to develop new features for the upcoming or a distant future release.
Exists as long as the feature is in development. \
Will branch off `develop`, must merge into `develop` by creating a pull request and squashing the commit once approved.\
Naming convention: `feature/ID-feature-name` where ID is the corresponding task number. E.g IC20-NNN.

### Releases

#### QA Releases
- From `develop` create a branch with the format `release/qa-{year}.{month}.{day}.{number}`
- Create a Pull Request from the new branch pointing to `integrate`
- Merge the Pull Request. In case of conflicts you will need to merge `integrate` to the new branch

#### Higher environment releases
- create a branch from the lower environment with the format `release/{env prefix e.g. sq}-{version-number}`
- Create a PR from the new branch to the higher environment branch
- Merge the Pull Request. In case of conflicts you will need to merge the higher environment branch back into to the new branch

<p align="right">(<a href="#top">back to top</a>)</p>

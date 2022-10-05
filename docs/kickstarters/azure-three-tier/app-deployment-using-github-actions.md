# Configuration of the CI/CD Pipeline for ASP .NET application to an App Service

### Generate deployment credentials

After the ASP .NET application is initialized and after the deployment of the Azure app service is done, a service principal must be created to authenticate with the Azure App Service for Github Actions. The service principal can be created from the Azure Cloud Shell using the following command,

**az ad sp create-for-rbac --name "myApp" --role contributor --scopes /subscriptions/<subscription-id>/     resourceGroups/<group-name>/providers/Microsoft.Web/sites/<app-name> --sdk-auth**

The placeholders for subscription ID, resource group name and app name must be replaced with the values from the app service you are using.

When the above command is executed in the Azure Cloud Shell, a JSON object will the following structure will be displayed.

```
{
    "clientId": "<GUID>",
    "clientSecret": "<GUID>",
    "subscriptionId": "<GUID>",
    "tenantId": "<GUID>",
    (...)
}
```

This JSON object must be copied and saved for later use.

### Configure the Github Secret

In Github, browse your repository, navigate to **Settings -> Secrets -> Add a new secret**. Then the JSON output from the Azure CLI command must be pasted. Name the secret as **Azure_CREDENTIALS** 

As we have configured the Github secret to authenticate to the Azure App service, the YAML file to build and develop the ASP .NET application can be created now.

### Creating the app deployment YAML file

Clone the ASP .NET application repository from Github and open it using your favorite text editor. In the root folder, create **.github/workflows** folder and create a new YAML file inside the folder.

Initially, a name must be defined for the YAML file. Then, environment variables that will be used in the YAML file can be defined under **env:** section. The names of the Azure WebApp, .NET runtime version can be defined as environment variables.

Then we must setup the trigger on which this Github workflow must be triggered. This can be done under the **on:** section. Following code snippet demonstrates how it is done in the Azure Webapp Template used for the Todo application.

![on section](https://github.com/dilshan3/architecture.99x.io/blob/master/docs/kickstarters/azure-three-tier/on-app-service-deployment.png)

Then we can set up the environment to build the application. We set up the .NET environment for the deployment of the Todo application using the **actions/setup-dotnet** action. The .NET version also can be defined.

After setting up the environment, we build the Todo application using the following set of commands

```
name: dotnet build and publish
  run: |
    dotnet restore
    dotnet build --configuration Release
    dotnet publish -c Release -o '${{ env.AZURE_WEBAPP_PACKAGE_PATH }}/myapp' 
```

Then the built application can be deployed to the App Service using the **azure/webapps-deploy@v2** action. 

**Before deploying the Todo application to the Azure Web App you must authenticate to your Azure account using the following command and the service principal**

```
name: Signing in to Azure
        uses: azure/login@v1
        with:
          creds: ${{ secrets.AZURE_CREDENTIALS }}
```

The following commands can be used to deploy the Todo application

```
name: 'Run Azure webapp deploy action using service principal credentials'
        uses: azure/webapps-deploy@v2
        with: 
          app-name: ${{ env.AZURE_WEBAPP_NAME }} # Replace with your app name
          package: '${{ env.AZURE_WEBAPP_PACKAGE_PATH }}/myapp' # Replace with the path to your artifacts 
```

**After setting up the YAML file, check-in, push your code to Github and see the Deployment workflow in action....**
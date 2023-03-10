# aks-my-first-cluster

Using GitHub workflows to ;

- create an Azure Kubernetes Service infrastructure environment.
- deploy a Web Application to Kubernetes

`100 level content`

## Pre-req's

- GitHub CLI
- Azure CLI

## Step 1 - Bootstrap

Using [AKS Construction](https://azure.github.io/AKS-Construction/?deploy.clusterName=firstcluster&deploy.rg=aks&ops=none&secure=low&cluster.agentCount=1&cluster.enable_aad=true&addons.registry=Basic&addons.monitor=aci&net.vnet_opt=custom&net.nsg=true) I can configure a simple AKS cluster integrated with the right supporting Azure services.

The AKS Construction Accelerator provides a GitHub reusable workflow that we can reference from our own GitHub workflow. For ease, it'll provide all the scripts you'll need to create the Azure AD Identity, and coresponding GitHub secrets to allow GitHub to create Azure resources. To do this, we'll just need to provide the GitHub repository that you'll be using in order to put the correct values in the script.
![image](https://user-images.githubusercontent.com/17914476/217792218-ae7c9e53-e358-4c29-87a4-c746cabe3eb2.png)

### Identity and Secrets

Use the [Azure Cloud Shell](shell.azure.com) to run the script, as it contains the GitHub CLI and the Azure CLI both required by the script.

![image](https://user-images.githubusercontent.com/17914476/217796726-0ad773cb-9b30-49fc-b9dd-8570474bf1e5.png)

#### Azure CLI Output

![image](https://user-images.githubusercontent.com/17914476/217797367-bd284a3e-b9d0-4a42-9ef9-3572f8b988c4.png)

#### Verifying GitHub secret creation

![image](https://user-images.githubusercontent.com/17914476/217797726-cbc8cbac-25dd-4d51-a52b-eb718dcae91f.png)

## Step 2 - Creating the AKS infrastructure

The AKS Construction tool also provides the yaml workflow you'll need to create in your own repository in order to create the Azure Infrastructure.

![image](https://user-images.githubusercontent.com/17914476/217866462-5a32e51b-a01e-4cb7-ab58-53d9abc1bfd9.png)

Create the file in your repo

![image](https://user-images.githubusercontent.com/17914476/217866842-31c8cbbd-d3b3-4646-a86e-64ac9cfeacf2.png)

Now run the GitHub action workflow from the `Actions` tab.

![image](https://user-images.githubusercontent.com/17914476/217798926-9ff34b97-ff0d-4da3-b277-86488f897b35.png)

### Verify the infrastructure creation

You should find that the following Azure infrastructure is created in ~9 minutes.

![image](https://user-images.githubusercontent.com/17914476/217800848-433d9024-2209-4efd-8e83-1b84d4f9dc2a.png)

## Step 3 - Deploying the Azure Vote App

In the first instance, lets leverage a public container image to run a 2 tier web app in the cluster.

### Creating the workflow






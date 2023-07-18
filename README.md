
# **Deploying .NET Core Applications using Azure DevOps CI/CD Pipelines and Azure App Services**

We will use Azure DevOps Project to set up continuous delivery (CD) and continuous integration (CI) pipelines in this project. The purpose is to quickly deploy an app to a Azure services, in this case App Service

In this project, we will build an sample ASP.NET core sample code, explore the CI/CD pipelines, commit code changes and run CI/CD.

## **1. Setting up a sample .NET core project:**

We wil first create a directory

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.001.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.002.png)

After installing the .net SDK in the system, we will run the command:

`dotnet new sln -o HelloWorldApp`

This will create a solution file

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.003.png)

We wil go inside the the file and create the new mvc project:

`dotnet new mvc -n HelloWorldApp.Web`

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.004.png)

Now we will add the project to the solution:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.005.png)

Now we will build in local machine to test

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.006.png)

We can see it has built without any error:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.007.png)

Now we will check out dll from our project folder

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.008.png)

We see we can host it locally

Going to the <http://localhost:5000> we can see our sameple .net core web all

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.009.png)

## **2. Add the Code to the github:**

As it works, we will create a new repository in github and push these there. 

We will add this to Azure repo later.

First we will initialize the repo using git init in git bash

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.010.png)

Then we will add a gitignore file

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.011.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.012.png)

Now we will add and commit

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.013.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.014.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.015.png)

In github I have created new repository:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.016.png)

Now we will add this as origin our git repo

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.017.png)

Now we will rename and push all the files:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.018.png)

Now we see that all files are in github

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.019.png)

## **3. Import the project to Azure Repo:**

Go to Repos section of Azure DevOps and click on _Import a repository_:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.020.png)

Now paste your github link and import.

You can also push from your local repo is you want:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.021.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.022.png)

Once its imported you should be able to see your files

## **4. Creating a pipeline**

Go to pipline section of the Azure DevOps and click _create pipeline_

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.023.png)

For the code chose Azure Repos Git:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.024.png)

And chose your repo:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.025.png)

In the template configuraion we will chose ASP.NET core

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.026.png)

You will see an yaml, we will edit this code to add restore,build,publish steps:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.027.png)![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.028.png)![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.029.png)


We will also add publish build artifact task :

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.030.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.031.png)

Finally we will have the whole code:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.032.png)

It will be saved in the Azure repo, but i will also add it in the github repo for future reference.

Now you can save:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.033.png)

Now you can see a pipeline created:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.034.png)

Lets run the pipeline:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.035.png)

We can see the job is running:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.036.png)

We got an error because in the free Azure we have setup we do not yet have access to run parallel job in Microsoft hosted machine.

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.037.png)

So we can run the build in the local machine:

We will first add our local machine as an agent:

In project settings go to agent pools:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.038.png)

Here go to default and click New agent:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.039.png)

Steps are given in detail:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.040.png)

We will follow the same step in windows local machine:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.041.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.042.png)

(Personal access token required for this can be created from User setting-> personal access tokens)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.043.png)

Now we can see one new agent is added.

Now to change the our build to run in localhost we will have to change the code:

In the YAML under pool, delete the vmImage line and replace it with the following:
```
pool:

name: Default
```
![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.044.png)

Once you save and run it will ask for permission to use the default pool, you can confirm.

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.045.png)

Now if you see the build has completed

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.046.png)

You can go to the artifact created:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.047.png)

You will see the zip created and if you download and open you will see all the required files:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.048.png)

## **5. Create an app service:**

If we want to deploy our app to an app service we need to create an app service

We will go to Azure portal now and navigate to app service:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.049.png)

Click create,

Then we will add new resource group

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.050.png)

Then give a name and .net runtime stack

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.051.png)

Then you can review and create:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.052.png)

Simiarly we wil also create web app for dev and test environment.

You should finally have three web app like below:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.053.png)

## **6. Connect Azure DevOps with Azure Portal subscription using Azure AD:**

We will go to project settings in Azure DevOps and Service connections:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.054.png)

We will select service principal:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.055.png)

As we need some details in the next page to be filled, we will open Azure AD(soon will be renamed to Entra ID)

Add an app registration:

We will name it AzureDevOps and register

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.056.png)

We will also go to clients and secrets and create a secret:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.057.png)

We will also go to subscription and add a new role assignment to the app registration we just created.

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.058.png)

Now using all the info we will fill the Azure DevOps service connection fields:

First we will give subscription id and name

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.059.png)

Then we will give Service Principal Id(client ID) Service principal key(secret value), Tenant ID.

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.060.png)

Then when we verify it should be successful otherwise it may be missing something.

When we verify and save a new service connection should be added:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.061.png)

This will help you to find the web app created in Azure portal in Azure DevOps portal.

## **7. Create a release pipeline:**

In the Azure DevOps go to pipeline and then releases and then click new pipeline:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.062.png)

In template chose Azure _App Service Deployment_:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.063.png)

Name it and  got to tasks:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.064.png)

Here chose your subscription and the webapp:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.065.png)

Save it.

Now go to the pipeline and add artifact:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.066.png)

You can select your project where build is done and click add

You can also enable continuous deployment using the trigger:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.067.png)

Now we have pipeline till Dev.

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.068.png)

Either we can run this manually, but as there is automated CI/CD lets just change small code and it should build and deploy automatically:

We are editing _HelloWorldApp.Web/Views/Home/Index.cshtml_ 

(This is the index page of our web app)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.069.png)

We will commit this.

First we will see pipeline running:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.070.png)

Once its successfull we will see release running:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.071.png)

Then you can see successful release pipline:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.072.png)

Then you can check its log and go to the url mentioned:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.073.png)

We see that it is successfully deployed and available in the web app url:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.074.png)

## **8. Deploy till Production:**

Till now we deployed till dev environment. Lets add test environment and also production environment.

First let us just clone DEV  step and rename it to TEST and change the web app:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.075.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.076.png)

We will also add the post deployment condition to require approval between the stages:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.077.png)

Now before we add production let us add a deployment slot in production web app so we can use the swap between two slots.

(we have to upgrade webapp which provides staging slots)

Now go to the app service and then _Deploment slots_ and click _Add slot_:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.078.png)

We will name it as staging and add it :

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.079.png)

Now you will be abe to see two deployment slots:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.080.png)

Now lets add new stage for production in release pipeline:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.081.png)

In the task change deployment to staging slot:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.082.png)

Then add the new step to swap the slots(Azure App Service Manage):

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.083.png)

Now fill the required details:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.084.png)

Also make sure you have post deployment conditon for approval in every step.

Now your pipeline stages is complete:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.085.png)

## **9. Make final changes and trigger CI/CD:**

Now lets make changes in the index file as we did before:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.086.png)

When we commit it it will trigger the CI/CD pipeline:

First build pipeline will run:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.087.png)

Then release will begin:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.088.png)

Once DEV stage is complete it will wait for approval to proceed to next stage:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.089.png)

When we check the dev app service link we should see our changes reflected:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.090.png)

Now let us approve:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.091.png)

Now test stage will start:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.092.png)

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.093.png)

Similarly we will check the test link:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.094.png)

Now after approving again it will deploy to staging slot:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.095.png)    ![ref1]

We will now check the staging link:

![ref2]

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.098.png)

Finally we approve the swapping:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.099.png)          ![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.100.png)

Now let us go to our final production link:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.101.png)

We see that it is successfully deployed.

We can see the whole pipeline completed:

![](/readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.102.png)

That completes this detailed deployment of our application through Azure DevOps.

[ref1]: /readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.096.png
[ref2]: /readmeimages/Aspose.Words.90fd5c1b-757c-4a76-a5f6-38650d269967.097.png

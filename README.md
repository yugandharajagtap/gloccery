<h1>Grocery Shop Management System</h1>

<h2>Project Title:</h2>
Dockerization and Deployment of a Static Website on Azure Container Instances

<h2>Documentation:</h2>
Creating and Deploying a Docker Image for a Static Website on Azure Container Registry and Container Instances
Primary Azure Technology:
Azure Virtual Machine
Azure Container Registry
Azure Container Instances

<h2>Project Description:</h2>

<h3>Objective:</h3>
The primary objective of this project is to demonstrate the process of creating a Docker image from an Azure Virtual Machine (VM) containing a static website, pushing the Docker image to Azure Container Registry (ACR), and deploying a container instance using the image stored in ACR.

<h3>Prerequisites:</h3>
Azure subscription with access to Azure Portal.</br></br>
<img src = "https://github.com/yugandharajagtap/grocery-shop-management-system/blob/main/subscription.png"></img> </br></br>
Azure Virtual Machine with a static website deployed and docker installed on the Azure Virtual Machine.</br></br>
<img src = "https://github.com/yugandharajagtap/grocery-shop-management-system/blob/main/virtual%20machine.png"></img>

<h3>Step 1: Create a Dockerfile</h3>
Create a Dockerfile in the root directory of your static website on the Azure Virtual Machine. The Dockerfile specifies the steps to build the Docker image.

<h4>Example Dockerfile:</h4>

<b>Dockerfile</b></br>
<b># Use an official Nginx image as the base image</b></br>
FROM nginx:latest

<b># Copy the static website files to the Nginx default directory</b></br>
COPY /path/to/your/static/website /usr/share/nginx/html

<b># Expose port 80 for web traffic</b></br>
EXPOSE 80

<b># Command to run when the container starts</b></br>
CMD ["nginx", "-g", "daemon off;"]

<h3>Step 2: Build the Docker Image</h3>
Open a terminal on the Azure Virtual Machine and navigate to the directory containing the Dockerfile. Run the following command to build the Docker image:

<h4>bash</h4>
docker build -t your-image-name:tag .</br>
Replace your-image-name with a meaningful name for your image, and tag with a version or label for the image.

<h3>Step 3: Azure Container Registry Setup</h3>
Navigate to the Azure Portal.
Create a new Azure Container Registry.
Note the ACR login server URL, username, and password.</br></br>
<img src = "https://github.com/yugandharajagtap/grocery-shop-management-system/blob/main/container%20registries.png"></img>

<h3>Step 4: Login to Azure Container Registry</h3>
Run the following command on the Azure Virtual Machine to log in to the ACR using the credentials obtained in Step 3:

<h4>bash</h4>
docker login <acr-login-server> -u <username> -p <password>
Replace <acr-login-server>, <username>, and <password> with your ACR details.

<h3>Step 5: Tag and Push the Docker Image</h3>
Tag the Docker image with the ACR login server and push it to the ACR:

<h4>bash</h4>
docker tag your-image-name:tag <acr-login-server>/your-image-name:tag
docker push <acr-login-server>/your-image-name:tag

<h3>Step 6: Deploy Container Instance from ACR</h3>
Navigate to the Azure Portal.</br>
Create a new Azure Container Install</br></br>
<img src = "https://github.com/yugandharajagtap/grocery-shop-management-system/blob/main/container%20instance.png"></img>

## Create Docker repository on Nexus and push to it

### Technologies used:
Docker, Nexus, DigitalOcean, Linux
### Project Description:
Create Docker hosted repository on Nexus
Create Docker repository role on Nexus
Configure Nexus, DigitalOcean Droplet and Docker to be able to push to Docker repository
Build and Push Docker image to Docker repository on Nexus

Below are step-by-step guide to creating a Docker repository on Nexus and pushing a Docker image to it:

Step 1: Create Docker hosted repository on Nexus

Log in to your Nexus instance and go to the Administration section
Click on Repositories and then click on the Create Repository button
Select the Docker (hosted) recipe and click Next
Enter a name for example:- docker-hosted for your repository and click Create Repository
Your Docker repository is now created on Nexus

Step 2: Create Docker repository role on Nexus

Go to the Security section in Nexus and click on Roles
Click on the Create Role button
Enter a name for your role and click Create Role
Click on the newly created role and then click on the Privileges tab
Click on Add Privilege and select Repository View from the dropdown
Select your Docker repository from the list of repositories and click Add Selected
Click on Add Privilege again and select Repository Admin from the dropdown
Select your Docker repository from the list of repositories and click Add Selected
Your Docker repository role is now created on Nexus

Step 3: Configure Nexus, DigitalOcean Droplet and Docker to be able to push to Docker repository

Log in to your DigitalOcean Droplet via SSH
Create a Docker login file by running the command: touch ~/.docker/config.json
Open the Docker login file by running the command: nano ~/.docker/config.json
Add the following code to the file and replace the placeholders with your Nexus credentials and Docker repository URL:

        {
        "auths": {
            "YOUR-DOCKER-REPO-URL": {
                "auth": "YOUR-NEXUS-USERNAME:YOUR-NEXUS-PASSWORD"
            }
        }
    }

Save and close the file
Log in to your Nexus instance and go to the Docker repository you created earlier
Click on the Info button and copy the Repository URL
Go back to your DigitalOcean Droplet and run the command: docker login YOUR-DOCKER-REPO-URL
Enter your Nexus username and password when prompted
Your Docker client is now authenticated to push to your Docker repository on Nexus

Step 4: Build and Push Docker image to Docker repository on Nexus

Create a Dockerfile in your project directory and write the instructions to build your Docker image
Build your Docker image by running the command: docker build -t YOUR-DOCKER-REPO-URL/YOUR-IMAGE-NAME:TAG .
Push your Docker image to your Docker repository on Nexus by running the command: docker push YOUR-DOCKER-REPO-URL/YOUR-IMAGE-NAME:TAG
Your Docker image is now pushed to your Docker repository on Nexus
That's it! You have successfully created a Docker repository on Nexus and pushed a Docker image to it.



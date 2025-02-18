## This file expounds on how the objectives of the project were implemented.
# ANSIBLE SECTION
Steps taken to meet objectives of the project;
1. Initialized vagrant using the vagrant up command in the project's root directory
2. Added a virtual box 'generic/centos7 (v4.2.14)
3. Vagrant up command. This command creates and configures guest machines according to what is in the vagrant file.
4. Created ansible playbook
Role of commands on the playbook
* ---
The three dashes represent the start of the file
* Name
This specifies the play name
* Tasks
This specifies the actions to be performed in the playbook
* Become
This line tells Ansible to use sudo for all the tasks in the playbook (you’re telling Ansible to ‘become’ the root user with sudo, or an equivalent).
* Host
This line tells Ansible to which hosts this playbook applies
* apt
To download and install
* Git
The git module is used to specify the github link to the yolo project
* Repo
The github repository to be cloned
* Dest
This defines the destination for the cloned repository. This is a local directory in the remote machine.
* Clone
You set the attribute clone to yes to clone the repository and update it using the update attribute.
* Update
This command updates the repository
* State

 5. 


# DOCKER COMPOSE SECTION
## Choice of the base image on which to build each container.
The first thumb rule when choosing a docker base image is that the size of the image should be smaller. This factor led me to to choose the base image to use for this project.
The base Image used is a node base image since the project is built using Node.js

## Dockerfile directives used in the creation and running of each container.
Client service 
FROM node:13.12.0-slim
This command specifies the base image to be used in the docker file.
WORKDIR /app
This command sets the working directory for the application.

COPY package*.json ./
This command copies the package.json and package-lock.json files from the local directory to the dockerfile.

RUN npm install
This command runs the npm install command which install the dependencies need to run the application.

COPY . .
This command enables one to copy files from docker host to the file system of the new image.

EXPOSE 3000
This command indicates to docker that the container will have a process listening on a given port or ports.

CMD [ "npm", "run", "start" ]
This command runs the given instructions when the container is started.

Same explanation applies to the backend Dockerfile

## Docker-compose Networking (Application port allocation and a bridge network implementation) where necessary.

-Used a bridge network driver to enable my containers communicate to each other.

## Docker-compose volume definition and usage (where necessary).

## Git workflow used to achieve the task.
Steps taken:

* Forked and cloned the yoloapp repository into my local machine

* Installed the dependencies needed to run the app in my local machine. I was able to run the app

* Created Dockerfiles for each microservice. Build and tested the images on my local machine and pushed the changes to git

* Created a docker-compose file


## Successful running of the applications and if not, debugging measures applied.

- Getting the errors below and working to solve them;
    
    *yolo-client-1 exited with code 0

     - Managed to debug this error by adding tty: true on my docker-compose file.
     - Yolo app managed to compile successfully on my network on http://172.21.0.3:3000
     
    *yolo-backend-1  | MongooseServerSelectionError: connect ECONNREFUSED 127.0.0.1:27017
    

## Good practices such as Docker image tag naming standards for ease of identification of images and containers. 

* Descriptive commits to track my progress on github

* Good practices used in naming of Docker images;

        -use of lowercase only 

        -Use of semantic version i.e harold7/yolo-backendapp:1.0.0 and harold7/yolo-clientapp:1.0.0

        -Use of Kebab-case for multi-word names eg harold7/yolo-backendapp:1.0.0

        -Use of short image names that are meaningful

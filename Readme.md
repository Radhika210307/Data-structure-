# Data Structure
# OOPS[object-oriented programming system]--> C + OOPS=C++.
# OOPS contain-- 
  a.class 
  b.object 
  c.reference 
  d.construction
Screenshot_2024_0911_141703

# TYPES OF OOPS
  1.Encapsulation (or OOP Encapsulation) refers to the bundling of data, along with the methods that operate on that data, into a single unit.Encapsulation is a way to achieve “information hiding” so, you don’t “need to know the internal workings of the mobile phone to operate” with it.

  2.Abstruction-
    Abstraction on the other side can be explained as the capability to use the same interface for different objects. Different implementations of the same interface can exist. Details are hidden by encapsulation.

  3.Polymorphism-
    Polymorphism is a concept, which allows us to redefine the way something works, by either changing how it is done or by changing the parts used to get it done.

  4.Inheritance-
    Inheritance is a feature of object-oriented programming that allows code reusability when a class includes property of another class. Considering HumanBeing a class, that has properties like hands, legs, eyes, mouth, etc, and functions like walk, talk, eat, see, etc.

# CRYPTOGRAPHY-
Cryptography is a method of protecting information and communications through the use of codes, so that only those for whom the information is intended can read and process. IMAGE


# TYPES OF CRYPTOGRAPHY-
There are two types of cryptography
1.symmetric
2.asymmetric

# Python -
Python is a high-level, interpreted, and general-purpose programming language known for its readability, simplicity, and versatility. Developed by Guido van Rossum and first released in 1991, Python emphasizes code readability and allows developers to express concepts in fewer lines of code compared to other languages. It supports multiple programming paradigms, including procedural, object-oriented, and functional programming.

# Database Management System :-
It is a software or technology used to manage data from a database. Some popular databases are MySQL, Oracle, MongoDB, etc. DBMS provides many operations e.g. creating a database, Storing in the database, updating an existing database, delete from the database. DBMS is a system that enables you to store, modify, and retrieve data in an organized way. It also provides security to the database


# GitHub:-
A popular platform for hosting and managing Git repositories. Features: Collaboration tools, including issues, pull requests, and code reviews. Project management features, such as milestones and wikis. Integration with other development tools and services. GitLab A comprehensive DevOps platform that includes Git repository hosting, continuous integration/continuous delivery (CI/CD), and other DevOps tools. Features: All the features of GitHub, plus additional tools for planning, building, testing, and deploying software. Integrated CI/CD pipelines for automating the software development process. Built-in container registry and package management. GitOps A set of practices and tools for managing infrastructure and applications using Git as the single source of truth. Key principles: Declaring the desired state of the infrastructure and applications in Git repositories. Using automated tools to reconcile the current state with the desired state. Continuous deployment of changes to production. In summary:

# GitHub is primarily a platform for hosting and managing Git repositories. GitLab is a more comprehensive DevOps platform that includes Git repository hosting, CI/CD, and other tools. GitOps is a set of practices and tools for managing infrastructure and applications using Git. The choice between GitHub,

1. using EC2 in aws
First open aws search EC2 then Launch Instance and there select keypair in putty then download it

after that Launch it and run putty and paste public id on HOST NAME and open that downloaded key pair for putty in SSH then Auth then Credentials and open there

after that run it and write username as ubuntu as selected os and then type following commands

sudo apt update

sudo apt install apache2
# to install a web server on ip then

sudo su
# for convert $ into # for getting admin role then

cd /var/www/html/
# then

ls
# for list of html file in it

# then copy that html file name and write

rm index.html
# rm means remove command

vi index.html
# this will open a notepad like and write html code there like (vi is editor) -



# then press ctrl+c then shift+colon then write wq and enter

# now copy your public ip and paste it on browser you will see the texts written by you (by using html above)

2. USING CONTAINER IN VM and adding nginx server by Docker
First open aws search EC2 then Launch Instance and there select keypair in putty then download it

# after that edit network setting and click on add security group rule and select TCP,UDP,ALL TRAFFIC AND SELECT EVERYWHERE SOURCE TYPE IN THEM then Launch it and run putty and paste public id on HOST NAME and open that downloaded key pair for putty in SSH then Auth then Credentials and open there

# after that run it and write username as ubuntu as selected os and then type following commands

curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
# this will install and run docker in your vm

newgrp docker
# this command will help us to use docker

docker ps
# this will list docker

docker --version
# this will display the version of docker installed

#now installing nginx
docker pull nginx
# You can download Nginx from a pre-built Docker image, with a default Nginx configuration, by above command. This downloads all the necessary components for the container.

docker run --name docker-nginx -p 80:80 nginx
# Nginx installed, you can configure the container so that it’s publicly accessible as a web server.

# run is the command to create a new container

# The --name flag is how you specify the name of the container. If left blank, a generated name like nostalgic_hopper will be assigned.

# -p specifies the port you are exposing in the format of -p local-machine-port:internal-container-port. In this case, you are mapping port :80 in the container to port :80 on the server.

# nginx is the name of the image on Docker Hub.

# now this will show this on your public ip


# In your terminal, enter CTRL+C to stop the container from running.
docker ps -a
# verify the container status with this command

docker rm docker-nginx
# Remove the existing container

docker run --name docker-nginx -p 80:80 -d nginx
# Create a new, detached Nginx container,By attaching the -d flag, you are running this container in the background.

docker ps
# this will obtain info about your container

docker stop docker-nginx
# Stop the container

docker rm docker-nginx
# remove the container

## Building a Web Page to Serve on Nginx
mkdir -p ~/docker-nginx/html
# Create a new directory for your website content within the home directory

cd ~/docker-nginx/html
# by this you navigate into this

vi index.html
# now press i and write your code in html like



# then press ctrl+c then shift+colon then write wq and enter

docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx
# Linking the Container to the Local Filesystem

# open your public ip in browser you will see as the content as your html code

## Using Your Own Nginx Configuration File
cd ~/docker-nginx
docker cp docker-nginx:/etc/nginx/conf.d/default.conf default.conf
# Copy the Nginx config directory into your project folder

docker stop docker-nginx
docker rm docker-nginx
# to rebuild the container stop the container then remove it

docker run --name docker-nginx -p 80:80 -v ~/docker-nginx/html:/usr/share/nginx/html -v ~/docker-nginx/default.conf:/etc/nginx/conf.d/default.conf -d nginx
# This command links the custom website pages to the container.

docker restart docker-nginx
# you need to restart your container to reflect changes on the associated pages.

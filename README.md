# Docker Lab
A beginner-level Docker project to explore docker fundamentals, containers, servers, networking and ports.
## Project Overview
To run a web server inside a Docker container, understand how ports and container networking work, and practice diagnosing the kinds of problems that happen in real environments.

Here's a flowchart describing the process:

<img width="396" height="631" alt="image" src="https://github.com/user-attachments/assets/84899521-6de8-479c-a163-f13b80b31d95" />

## Technologies Used
+ Docker
+ NGINX
+ Linux commands
+ Docker networking
+ Git and GitHub
+ HTML
## What I Built
+ HTML web page.
+ A Dockerfile based on nginx:alpine.
+ A custom Docker image called my-web:1.0.
+ Multiple containers running the same web server.
+ A custom Docker network called lab-net.

## Troubleshooting Scenarios
### 1. Port already in use
+ Current situation:

   As the image demonstrates that container 'my-web' occupies the 8080 port on the computer.

     <img width="362" height="40" alt="image" src="https://github.com/user-attachments/assets/1e30fd1c-4765-4622-9037-c5af0c992327" />


+ Error:

   Any attempt of using that exact port will raise an error.

    <img width="438" height="76" alt="image" src="https://github.com/user-attachments/assets/c41e1b2d-fc12-4506-9416-4c295e691d02" />

+ Solution:
   Mapping the container to another unoccupied port
  
    <img width="435" height="77" alt="image" src="https://github.com/user-attachments/assets/53391933-cf94-4fb8-91e0-46e0df63f0c6" />



### 2. Wrong container port
+ Current situation:
    This container maps host port 8084 to container port 8800

    <img width="513" height="35" alt="image" src="https://github.com/user-attachments/assets/275ef7b7-6a4a-4204-b6cc-eff8e3f4689e" />

+ Error:

   Nginx server receives requests at port 80. Mapping to an incorrect container port will raise error when you try to run the web page on http://localhost:8084.

    <img width="695" height="673" alt="image" src="https://github.com/user-attachments/assets/4b763b5a-82f8-4822-afa9-a2dfb237a384" />

+ Solution:
   Rerun the container to the correct port where nginx listens.
  
    <img width="1098" height="168" alt="image" src="https://github.com/user-attachments/assets/7207fcc8-890c-4482-8c85-e5346f9cd0a5" />

   Now when you visit http://localhost:8084, the web page will load:

    <img width="476" height="176" alt="image" src="https://github.com/user-attachments/assets/f8da9dc3-f443-43d0-a43e-19c45f5b2ca6" />




  
### 3. Container exits immediately
+ Current situation:

   This container has a configuration file that doesn't exist.

     <img width="683" height="34" alt="image" src="https://github.com/user-attachments/assets/8f2b371a-6e25-4223-97d2-51fc40ffb106" />


+ Error:

   Container won't run because nginx can't find the configuration file.
  
    <img width="395" height="36" alt="image" src="https://github.com/user-attachments/assets/f15caf2d-85c6-44e0-844f-f3049e12a4de" />


+ Solution:

   Remove the container and restart it without the invalid configuration-file argument
  
    <img width="964" height="129" alt="image" src="https://github.com/user-attachments/assets/d125619b-ece4-4e44-87f2-d3a4e609e615" />


### 4. Container communication failure
+ Current situation:

   The network wasn't specified; therefore, the container will be on docker default network not our custom network.

    <img width="540" height="39" alt="image" src="https://github.com/user-attachments/assets/965309d4-692c-4cc1-b4f0-e3885615e490" />


+ Error:

   When you try reach the container in the custom network using curl image, it will raise an error.

    <img width="636" height="33" alt="image" src="https://github.com/user-attachments/assets/d1601551-7855-4863-ac59-04de80406ac2" />

+ Solution:
   	Connect the container to your custom network.
  
    <img width="669" height="217" alt="image" src="https://github.com/user-attachments/assets/79aeaa8e-2af0-447c-ae86-3944db8f1647" />

## What I Learned
+ Difference between Docker images and containers.
+ How Dockerfile instructions work (FROM, COPY).
+ How to build and run Docker image.
+ How port mapping works (8080:80).
+ Difference between host ports and container ports.
+ How containers communicate through Docker networks.
+ How to inspect containers and read their logs.
+ How to troubleshoot port conflicts, incorrect port mappings, container startup failures, and container networking issues.
  
## Author
 
   Ahmed Adil

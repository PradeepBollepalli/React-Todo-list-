# React Todo List Application Dockerization


# Table of Contents
  
  # Introduction
      
   1.Prerequisites
      
   2. Cloning the Repository
    
   3.Creating the Dockerfile
    
   4.Building the Docker Image
    
   5.Running the Docker Container
    
   6.Testing the Application
    
   7.Pushing Code to GitHub
    
   8.Pushing the Docker Image to Docker Hub
    
   9.Conclusion



 # Introduction:
 
  This documentation outlines the process of cloning a React Todo List application repository, creating a Dockerfile, building a Docker image, running the application in a Docker container, and pushing the code to GitHub 
  and the Docker image to Docker Hub.

# Prerequisites:

   1.Docker installed on your machine.
 
   2.Git installed on your machine.
 
   3.A Docker Hub account.
 
   4.A GitHub account.



# Cloning the Repository

   1.Open your terminal or command prompt.

   2.Navigate to the directory where you want to clone the repository

   3.Clone the repository:
   

   ![image](https://github.com/user-attachments/assets/cecc63f8-9b44-4d4d-8937-49ae722e37e9)

   4.Navigate into the cloned directory:

   ![image](https://github.com/user-attachments/assets/2f396675-5da5-4576-8ab6-022cac8e6df7)


 # Creating the Dockerfile
 
  1.In the root of the project directory, create a file named Dockerfile (without any extension).

   ![image](https://github.com/user-attachments/assets/ff4ce0a0-81bb-417a-a1d3-697a676401b1)


  2.Open the Dockerfile in a text editor and add the following configuration:

  ![image](https://github.com/user-attachments/assets/413d70b9-cb14-4bba-8aa4-b2704703aa7a)


# Building the Docker Image.

 1.Open your terminal and ensure you are in the project directory.

 2.Build the Docker image with the following command:

 ![image](https://github.com/user-attachments/assets/c0d519e8-f72a-4bbb-9080-05a108651434)


 # Running the Docker Container.
 
   Run the Docker container using the following command:

   ![image](https://github.com/user-attachments/assets/63d8f583-95e9-4a5e-96d8-7dbfac578cba)

  # Testing the Application
  
  Open your web browser and navigate to http://localhost:3000.

  You should see the React Todo List application running

 ![image](https://github.com/user-attachments/assets/7575d55f-b0b3-41e9-839d-9cd380a0dc7a)


# Pushing Code to GitHub

  Make sure you are in the project directory.
   
  I.Initialize Git if it hasn’t been initialized:
 
   1. git init


  II. Add the remote repository:

  git remote add origin https://github.com/PradeepBollepalli/React-Todo-list-.git

  III. Stage all changes:

  git add .

IV. Commit your changes:

 git commit -m "Initial commit with Dockerfile and project setup"
 
 Push the code to your GitHub repository:

![image](https://github.com/user-attachments/assets/32d62937-bae8-49ce-bc1f-dc791850246b)


# Pushing the Docker Image to Docker Hub

Log in to Docker Hub:

docker login

![image](https://github.com/user-attachments/assets/301bdf78-126b-412a-b7c9-6f42308b284d)


docker tag react-todo-app pradeep051/react-todo-app:latest

# Push the Docker image:

![image](https://github.com/user-attachments/assets/7a47f533-f956-41ef-8673-1a3b3ce6e4ed)

We can go and see in DockerHub wether image is Available or not.

![image](https://github.com/user-attachments/assets/3d82b704-aa87-45d5-8a15-bf877c67506f)



# Conclusion.

You have successfully cloned a React application, created a Dockerfile, built and run the Docker image, and pushed both your code and Docker image to GitHub and Docker Hub, respectively







   


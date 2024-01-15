def img
pipeline {
    environment {
        registry = "Rushikesh_H_Flask" //To push an image to Docker Hub, you must first name your local image using your Docker Hub username and the repository name that you created through Docker Hub on the web.
        registryCredential = 'DOCKERHUB'
        githubCredential = 'GITHUB'
        dockerImage = ''
    }
    agent any
    stages {
        
        stage('checkout') {
                steps {
                git branch: 'main',
                credentialsId: githubCredential,
                url: 'https://github.com/blueprintparadise/Deployment-AWS-Jenkins.git'
                }
        }

        stage('Cloning Git') { 
            steps { 
                git 'https://github.com/blueprintparadise/Deployment-AWS-Jenkins.git' 
            }
        }
        
        stage('Docker run') {
           steps {
                sh label: '', script: "docker build -t hey-python-flask:0.0.1.RELEASE ."
                sh label: '', script: "docker container run -d -p 3000:3000 hey-python-flask:0.0.1.RELEASE"
          }
        }
        
        
        stage ('Test'){
                steps {
                sh "pytest tests.py"
                }
        }
        

                    
        

      }
    }

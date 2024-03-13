pipeline {
    agent any
    environment {
        CONTAINER_NAME = "my-flask-app"
    }
    
    stages{    
        stage('Build and Test'){
            steps{
                sh 'docker build . -t my-flask-app:latest'
            }
        }
        stage('Deploy'){
            steps{
                  script{
                    //sh 'BUILD_NUMBER = ${BUILD_NUMBER}'
                    if (BUILD_NUMBER == "1") {
                        sh 'docker run -d --name $CONTAINER_NAME -p 5000:5000 $CONTAINER_NAME'
                    }
                    else {
                        sh 'docker stop $CONTAINER_NAME'
                        sh 'docker rm $CONTAINER_NAME'
                        sh 'docker run -d --name $CONTAINER_NAME -p 5000:5000 $CONTAINER_NAME' 
                      }
                    //sh 'echo "Latest image/code deployed"'
                }
            }
        }
    }
}
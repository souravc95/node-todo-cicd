pipeline {
    agent any
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/Rabi8429/node-todo-cicd.git', branch: 'master' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t rabi4450/no-todo-test:latest'
            }
        }
        stage('Push'){
            steps{
                withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
        	     sh "docker login -u ${env.rabi4450} -p ${env.dockerhubpwd}"
                 sh 'docker push rabi4450/no-todo-test:latest'
                }
            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}

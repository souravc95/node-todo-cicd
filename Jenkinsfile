pipeline{
    agent any
        stages{
            stage('Github checkout') {
                steps{
                    git 'https://github.com/Rabi8429/node-todo-cicd.git'
                }
                
            }
            stage('Build and Test') {
                steps{
                    sh 'docker build . -t rabi4450/node-todo-test'
                }
                
            }
            stage('Docker hub push') {
                steps{
                    withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u rabi4450 -p ${dockerhubpwd}'
                    
}
          
                    sh 'docker push rabi4450/node-todo-test'
                }
                
            }
            stage('Deploy') {
                steps{
                   sh "docker-compose down && docker-compose up -d" 
                }
            }            
        }
} 

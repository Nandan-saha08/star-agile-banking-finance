pipeline {
    agent any
    stages{
        stage('git cloned'){
            steps{
                git url:'https://github.com/Nandan-saha08/star-agile-banking-finance.git', branch: "master
                
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t nandansaha0807/staragileprojectfinance:v1 .'
                    sh 'docker images'
                }
            }
        }
         stage('Docker login') {
             Steps {
                  withCredentials([usernamePassword(credentialsID: 'dockerhub-pwd', passwordVariable: 'PASS', usernameVariable: 'USER')])
                       sh "echo $PASS  "
        
     stage('Deploy') {
            steps {
                sh 'sudo docker run -itd --name My-first-containe21211 -p 8083:8081 nandansaha0807/staragileprojectfinance:v1'
                  
                }
            }
        
    }
}

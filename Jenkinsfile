pipeline {
    agent any
    stages {
        stage('Git Clone') {
            steps {
                git url: 'https://github.com/Nandan-saha08/star-agile-banking-finance.git', branch: "master"
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t nandansaha0807/staragileprojectfinance:v1 .'
                    sh 'docker images'
                }
            }
        }
        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-pwd', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push nandansaha0807/staragileprojectfinance:v1'
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo docker run -itd --name Project_Con01 -p 8083:8081 nandansaha0807/staragileprojectfinance:v1'
            }
        }
    }
}

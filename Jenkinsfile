
pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'python207', url: 'https://github.com/demesne2001/Reporting.git']])
                echo 'checkout done'
            }
        }
        stage('Docker Image') {
            steps {
                script{
                    bat 'docker build . -f dockerfile.txt -t finaldockerproject'
                    
                }
                echo 'Docker Image done'
            }
        }
        stage('Docker Run') {
            steps {
                script{
                    bat 'docker run -d -p 3032:3032 finaldockerproject'
                }
                echo 'Docker push done'
            }
        }
        stage('Docker push') {
            steps {
                script{
                    bat 'docker login -u patelom0910 -p 09102001Om'
                }
                echo 'Docker push done'
            }
        }
    }
}


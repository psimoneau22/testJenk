pipeline {
    agent {
        docker {
            //image 'node:8-alpine'
            image 'microsoft/dotnet:2.1-sdk-alpine'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                // sh 'npm --version'
                // sh 'node --version'
                sh 'dotnet --info'
                sh 'dotnet publish -o ./dist'
            }
        }
        stage('Test') {
            steps {
                // sh './jenkins/scripts/test.sh'
            }
        }
    }
}
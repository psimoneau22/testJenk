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
        stage('Build dotnet') {
            steps {
                pwd()
                sh 'dotnet --info'
                sh 'dotnet publish -o ./dist'
                archiveArtifacts artifacts: 'bin/Release/netcoreapp2.1/win-x64/publish/*', fingerprint: true
            }
        }
        stage('Build react') {
            steps {

                dir() {
                    pwd('server')

                    sh 'npm --version'
                    sh 'node --version'sh './jenkins/scripts/test.sh'
                    sh 'npm run build'
                    archiveArtifacts artifacts: 'build/*', fingerprint: true
                }
            }
        }
    }
}
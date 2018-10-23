pipeline {
    agent none
    environment {
        CI = 'true'
    }
    stages {
        stage('Build dotnet') {
            agent {
                docker {
                    image 'microsoft/dotnet:2.1-sdk-alpine'
                }
            }
            steps {
                pwd()
                sh 'dotnet --info'
                sh 'dotnet publish -o ./dist'
                archiveArtifacts artifacts: 'bin/Release/netcoreapp2.1/win-x64/publish/*', fingerprint: true
            }
        }
        stage('Build react') {
            agent {
                docker {
                    image 'node:8-alpine'
                }
            }
            steps {
                dir('server') {
                    pwd()

                    sh 'npm --version'
                    sh 'node --version'
                    sh 'npm run build'
                    archiveArtifacts artifacts: 'build/*', fingerprint: true
                }
            }
        }
    }
}
pipeline {
    agent none
    stages {
        stage('Build and test typescript and linter ') {
            agent {
                docker { image 'node:14-alpine' }
            }
            steps {
                dir ('DotnetTemplate.Web') {
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm run lint'
                    sh 'npm t'
                }
            }
        }
       stage('Build and test c# ') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/sdk:5.0' 
                }
            }
            environment {
                DOTNET_CLI_HOME='/tmp/dotnet_cli_home'
            }
            steps {
                sh 'dotnet build'
                sh 'dotnet test'
            }
        }
    }
}

pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Restore') {
            steps {
                bat 'dotnet restore'
            }
        }
        
        stage('Build') {
            steps {
                bat 'dotnet build --configuration Release'
            }
        }
        
        stage('Test') {
            steps {
                bat 'dotnet test --configuration Release --no-build'
            }
        }
        
        stage('Publish') {
            steps {
                bat 'dotnet publish --configuration Release --output publish_output'
                archiveArtifacts artifacts: 'publish_output/**', followSymlinks: false
            }
        }
    }
    
    post {
        always {
            junit '**/TestResults/*.xml'
        }
    }
}

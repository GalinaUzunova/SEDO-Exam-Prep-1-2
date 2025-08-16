pipeline {
    agent any

  

    stages {
        stage('Checkout') {
            when { branch pattern: "main|feature", comparator: "REGEXP" }
            steps {
                checkout scm
            }
        }
        
        stage('Restore') {
            when { branch pattern: "main|feature", comparator: "REGEXP" }
            steps {
                bat 'dotnet restore'
            }
        }
        
        stage('Build') {
            when { branch pattern: "main|feature", comparator: "REGEXP" }
            steps {
                bat 'dotnet build --configuration Release'
            }
        }
        
        stage('Test') {
            when { branch pattern: "main|feature", comparator: "REGEXP" }
            steps {
                bat 'dotnet test --configuration Release --no-build '
            }
        }
    }

  
}

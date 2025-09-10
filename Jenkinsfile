pipeline {
    agent any
    
    tools {
        nodejs 'Node 22.x'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
    
    post {
        failure {
            mail to: 'your-email@example.com', 
                 subject: "Pipeline failed: ${currentBuild.fullDisplayName}", 
                 body: "Something went wrong with the build."
        }
    }
}
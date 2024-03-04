# MavenProject223
mavenprj223


pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code repository
                git 'https://github.com/Zuhairhadi/MavenProject223.git'
            }
        }
        
        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy your application, e.g., to a server
                sh 'mvn deploy'
            }
        }
    }
    
    post {
        success {
            // Notification for successful build
            echo 'Build successful - Sending notifications...'
            // Send notification or trigger downstream jobs
        }
        failure {
            // Notification for failed build
            echo 'Build failed - Sending notifications...'
            // Send notification or take other actions for failed build
        }
    }
}

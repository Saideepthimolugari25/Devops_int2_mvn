pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/demo-maven-pipeline.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Running mvn clean install...'
                bat 'mvn clean install'
            }
        }

        stage('Build and Test') {
            steps {
                echo 'Building and testing the project...'
                bat 'mvn package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

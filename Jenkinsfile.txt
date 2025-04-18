pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Adiii19/DockerJenkinsExperiment.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'ls -l' // List files for debugging
                sh 'docker build -t my-docker-webapp .' // Build Docker image from current directory
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8081:80 my-docker-webapp'
            }
        }
    }
}

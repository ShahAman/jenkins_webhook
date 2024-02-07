pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ShahAman/jenkins_webhook.git']])
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/ShahAman/jenkins_webhook.git'
                bat 'python -m pip install -r requirements.txt'
                bat 'python ops.py' 
            }
        }
        stage('Test') {
            steps {
                bat 'python -m pytest' 
            }
        }
    }
}
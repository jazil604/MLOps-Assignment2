pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/jazil604/MLOps-Assignment2.git'
            }
        }

        stage('Create Python Environment') {
            steps {
                powershell '''
                    $python = "C:\\Users\\HP PROBOOK\\AppData\\Local\\Python\\bin\\python.exe"
                    & $python -m venv .dk
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                powershell '''
                    .\\.dk\\Scripts\\python.exe -m pip install --upgrade pip
                    .\\.dk\\Scripts\\python.exe -m pip install -r requirements.txt
                '''
            }
        }

        stage('Test Application') {
            steps {
                powershell '''
                    .\\.dk\\Scripts\\python.exe -m pytest
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                powershell '''
                    docker build -t docker-flask-app:latest .
                '''
            }
        }
    }
}
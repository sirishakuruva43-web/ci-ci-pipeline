pipeline {
    agent any

    environment {
        DOCKER_EXE = 'C:\\Users\\Sirisha\\AppData\\Local\\Programs\\Docker\\Docker\\resources\\bin\\docker.exe'
    }

    stages {

        stage('Check Docker') {
            steps {
                bat '"%DOCKER_EXE%" --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '"%DOCKER_EXE%" build --no-cache -t vite-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat '''
                    "%DOCKER_EXE%" stop vite-container || echo Container not running
                    "%DOCKER_EXE%" rm vite-container || echo Container not found
                    "%DOCKER_EXE%" run -d -p 8081:80 --name vite-container vite-app
                '''
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Build successful"
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }
    }
}

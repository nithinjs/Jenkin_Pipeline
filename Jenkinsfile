pipeline {
    agent any
    environment {
        DIRECTORY_PATH = 'c:/path/to/directory/demo'
        TESTING_ENVIRONMENT = 'SIT753/TestEnv'
        PRODUCTION_ENVIRONMENT = 'Nithin Jayakumar Sarojam (Nithin JS)'
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path : ${DIRECTORY_PATH}"
                echo 'Compile the code and generate any necessary artefacts'
                echo 'used Maven  to build the project'
            }
           
        }

        stage('Unit and Integration Tests') {
            steps {
                echo ' Running unit tests to ensure the code functions as expected'
                echo 'used JUnit to run the unit tests'
                echo 'Running integration tests to ensure the components work together'
                echo 'used JUnit to run the integration tests'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis to ensure code quality'
                echo 'used SonarQube to perform code analysis'
                echo 'Code analysis completed successfully'
            }
        }

        stage('Security Scan') {
            steps {
                echo "Performing security scan to identify vulnerabilities"
                echo 'used SonarQube to perform security scan'
            }
        }

        stage('Deploy to Staging ') {
            steps {
                echo 'Deploying the application to the staging environment'
                echo "Deploying the application to the staging environment ${TESTING_ENVIRONMENT}"
                echo 'used AWS CodeDeploy to deploy the application'
                
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment'
                echo 'used JUnit to run the integration tests'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production environment ${PRODUCTION_ENVIRONMENT}"
                echo 'used AWS CodeDeploy to deploy the application'
            }
        }
    }
}

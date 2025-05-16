 pipeline {
    agent any
    environment {
        DIRECTORY_PATH = 'c:/path/to/directory/demo'
        TESTING_ENVIRONMENT = 'SIT753/TestEnv'
        PRODUCTION_ENVIRONMENT = 'Nithin Jayakumar Sarojam(Nithin JS)'
        LOG_FILE = 'log.txt'
        RECIPIENT = 'sidharthsid0413@gmail.com' 
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path: ${DIRECTORY_PATH}"
                echo 'Compile the code and generate any necessary artefacts'
                echo 'used Maven to build the project'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    try {
                        sh "echo 'Running unit and integration tests...' > ${LOG_FILE}"
                        sh "echo 'Used JUnit to run the tests.' >> ${LOG_FILE}"
                        currentBuild.result = 'SUCCESS'
                    } catch (err) {
                        currentBuild.result = 'FAILURE'
                        throw err
                    }
                }
            }
            post {
                always {
                    emailext(
                        to: "${RECIPIENT}",
                        subject: "Test Stage Result - ${currentBuild.result}",
                        body: "Unit and Integration Tests completed with status: ${currentBuild.result}",
                        attachmentsPattern: "${LOG_FILE}",
                        mimeType: 'text/plain'
                    )
                }
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
                script {
                    try {
                        sh "echo 'Performing security scan...' > ${LOG_FILE}"
                        sh "echo 'Used SonarQube to perform the security scan.' >> ${LOG_FILE}"
                        currentBuild.result = 'SUCCESS'
                    } catch (err) {
                        currentBuild.result = 'FAILURE'
                        throw err
                    }
                }
            }
            post {
                always {
                    emailext(
                        to: "${RECIPIENT}",
                        subject: "Security Scan Result - ${currentBuild.result}",
                        body: "Security Scan completed with status: ${currentBuild.result}",
                        attachmentsPattern: "${LOG_FILE}",
                        mimeType: 'text/plain'
                    )
                }
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

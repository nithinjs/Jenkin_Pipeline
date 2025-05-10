pipeline {
    agent any
    environment {
        DIRECTORY_PATH = 'c:/path/to/directory/demo'
        TESTING_ENVIRONMENT = 'SIT753/TestEnv'
        PRODUCTION_ENVIRONMENT = 'Nithin Jayakumar Sarojam'
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path : ${DIRECTORY_PATH}"
                echo 'Compile the code and generate any necessary artefacts'
            }
            post {
                success {
                    echo 'Build was successful'
                    mail to: 'avanius8@gmail.com',
                    subject: "Birthday Wishes from your friend",
                    body: "Happy Birthday to you Avani (In advance)! May your day be filled with joy and laughter. Wishing you all the best on your special day! I'll order Full Kuzhimanthi for you. Only you can finish it whole. Enjoy your day!"
                    
                }
                failure {
                    echo 'Build failed'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Unit tests'
                echo 'Integration tests'
            }
        }

        stage('Code Quality Check') {
            steps {
                echo 'Check the quality of the code'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy the application to a testing environment ${TESTING_ENVIRONMENT}"
            }
        }

        stage('Approval') {
            steps {
                echo 'Waiting for manual Approval from the testing team'
                sleep(time: 10, unit: 'SECONDS')
                echo 'Approval received from the testing team'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production environment ${PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}

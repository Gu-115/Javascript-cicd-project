
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out JavaScript project'
            }
        }

        stage('Check Node.js') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    if [ -f package.json ]; then
                        npm install
                    else
                        echo "package.json not found. Skipping npm install."
                    fi
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    if [ -f package.json ]; then
                        npm test --if-present
                    else
                        echo "No package.json found. Skipping tests."
                    fi
                '''
            }
        }
    }

    post {
        success {
            echo 'JavaScript CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'JavaScript CI/CD Pipeline failed!'
        }
    }
}


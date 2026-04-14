pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh '''
                ls -la 
                node -v
                npm -v
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Executing tests...'
                sh '''
                ls -la
                test -f build/index.html
                npm test
                ls -la
                '''
            }
        }
        stage('End-to-End-Test') {
            agent {
                dockerContainer {
                    image 'mcr.microsoft.com/playwright:v1.25.1-focal'
                }
            }
            steps {
                echo 'Executing end to end tests...'
                sh '''
                ls -la
                npm install serve
                npx serve -s build -l 3000 &
                sleep 10
                npx playwright test
                npx playwright show-report
                ls -la
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh '''
                
                '''
            }
        }
    }

    environment {
        NODE_ENV = 'production'
    }

    post {
        always {
            echo 'Always post section'
            archiveArtifacts artifacts: 'build/**', fingerprint: true
            junit 'test-results/junit.xml'
        }
        success {
            echo 'Success'
        }
        failure {
            echo 'Failure'
        }
    }
}
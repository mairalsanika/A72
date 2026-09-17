pipeline {
    agent any

    environment {
        // Sets Python path so Jenkins can execute scripts on Windows
        PATH = "C:\\Users\\sanik\\AppData\\Local\\Programs\\Python\\Python312;${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out source code from GitHub...'
                // Update URL if using a different repository for Project 3
                git branch: 'main', url: 'https://github.com/mairalsanika/A72.git'
            }
        }

        stage('Parallel Checks') {
            parallel {
                stage('Frontend Check') {
                    steps {
                        echo 'Starting Frontend Check Stage...'
                        bat 'python frontend_check.py'
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Starting Backend Check Stage...'
                        bat 'python backend_check.py'
                    }
                }
            }
        }

        stage('Summary') {
            steps {
                echo 'Both frontend and backend checks completed successfully in parallel!'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Project 3 Parallel Build succeeded!'
        }
    }
}
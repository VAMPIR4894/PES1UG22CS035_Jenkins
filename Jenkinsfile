pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'g++ -o output PES1UG22CS035-1.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './abc'  // Run the compiled binary
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}

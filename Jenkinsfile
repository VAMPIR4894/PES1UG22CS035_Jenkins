pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/VAMPIR4894/PES1UG22CS035_Jenkins.git'  // Replace with your repository URL
        BRANCH = 'main' // Change as needed
        CPP_FILE = 'hello1.cpp'
        EXECUTABLE = 'PES1UG22CS035-1'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    sh 'git clone $REPO_URL repo && cd repo && git checkout $BRANCH'
                }
            }
        }

        stage('Create .cpp File') {
            steps {
                script {
                    sh "echo '#include <iostream>\\nusing namespace std;\\nint main() {\\n cout << \"Hello, Jenkins!\\" << endl;\\n return 0;\\n}' > repo/$CPP_FILE"
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'cd repo && g++ $CPP_FILE -o $EXECUTABLE'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'cd repo && ./$EXECUTABLE'
                }
            }
        }

        stage('Push to Repository') {
            steps {
                script {
                    sh '''
                        cd repo
                        git config --global user.email "your-email@example.com"
                        git config --global user.name "your-name"
                        git add $CPP_FILE
                        git commit -m "Added new .cpp file"
                        git push origin $BRANCH
                    '''
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}

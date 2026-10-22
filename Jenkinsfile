pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
       stage('Checkout') {
    steps {
        git branch: 'main',
            url: 'https://github.com/Harshitha19-git/CICDJenkins.git'
    }
} stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yourusername/python-app.git'
            }
        }

        stage('Install') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Compile') {
            steps {
                bat 'python -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m pytest'
            }
        }

        stage('Package') {
            steps {
                bat 'python -m zipfile -c app.zip app.py requirements.txt'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'app.zip'
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed. Please check the logs for details.'
        }
    }
}

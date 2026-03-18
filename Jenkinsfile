pipeline {
    agent any

    environment {
        PATH = "/usr/bin:/usr/local/bin:/bin:/usr/sbin"
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                echo "PATH=$PATH"
                which docker
                docker --version
                docker build -t avanish9795/notes-app:latest .
                '''
            }
        }
    }
}

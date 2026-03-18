pipeline {
    agent any

    environment {
        PATH = "/usr/bin:/usr/local/bin:/bin"
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t avanish9795/notes-app:latest .'
            }
        }
    }
}

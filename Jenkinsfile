pipeline {
    agent any

    environment {
        PATH = "/usr/bin:/usr/local/bin:/snap/bin:/usr/sbin:/sbin:/bin"
    }

    stages {
        stage('Test Docker') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }
    }
}

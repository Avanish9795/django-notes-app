@Library("Shared") _
pipeline {
    agent { label "mishra" }

    stages {

        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage("code") {
            steps {
                echo "This is cloning the code"
                git url: "https://github.com/LondheShubham153/django-notes-app.git", branch: "main"
                echo "Code Cloning successful"
            }
        }

        stage("Build") {
            steps {
                echo "This is building the code"
                sh "whoami"
                sh "docker build -t notes-app:latest ."
            }
        }

        stage("Push to DockerHub") {
            steps {
                echo "This is pushing the image to Docker Hub"

                withCredentials([usernamePassword(
                    credentialsId: "dockerHubCred",
                    usernameVariable: "DOCKER_USER",
                    passwordVariable: "DOCKER_PASS"
                )]) {
                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    docker tag notes-app:latest $DOCKER_USER/notes-app:latest
                    docker push $DOCKER_USER/notes-app:latest
                    '''
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}

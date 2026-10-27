@Library("Shared") _
pipeline {
    agent {label "monu"}
    
     stages{
        stage("Clone") {
            steps {
                script{
                 clone("https://github.com/mahtaba515/django-notes-app.git","dev")
                }
            }
        }

        stage("Build") {
            steps {
                script{
                    docker_build("notes-app","latest","xdmahtab")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script{
                    docker_push("notes-app","latest","xdmahtab")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying the application"
                sh 'docker compose up -d'
            }
        }
    }
}

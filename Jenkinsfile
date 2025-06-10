@Library("Shared") _
pipeline{
    agent {label "jarvis"}
    
    stages{
        stage("Hello Jenkins"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    git_clone("https://github.com/Atharvakamtalwar/react_django_demo_app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "atharvakamtalwar")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "atharvakamtalwar")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying code!"
                sh "docker compose down && docker compose up -d"
                echo "Deploying Successful!"
            }
        }
    }
}

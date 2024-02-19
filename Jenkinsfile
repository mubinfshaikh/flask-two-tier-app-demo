pipeline {
    agent any
    
    stages{
        stage("Code"){
            steps{
                git url: "https://github.com/mubinfshaikh/flask-two-tier-app-demo.git", branch: "jenkins"
            }
        }
        stage("Build"){
            steps{
                sh "docker build -t flask-two-tier-app ."
            }
        }
        stage("Push to DockerHub"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh "docker tag flask-two-tier-app ${env.dockerHubUser}/flask-two-tier-app:latest"
                    sh "docker push ${env.dockerHubUser}/flask-two-tier-app:latest" 
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}

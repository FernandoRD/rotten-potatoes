pipeline{
    agent { label 'docker_executor' }

    stages{
        stage('Checkout Source'){
            steps{
                git url:'https://github.com/FernandoRD/rotten-potatoes.git', branch:'main'
            }        
        }
        stage('Build Image'){
            steps{
                script{
                    dockerapp = docker.build("fernandord/rotten-potatoes:v${env.BUILD_ID}", '-f ./src/Dockerfile .')
                }
            }
        
        }
        stage('Push Image'){
            steps{
                script{
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }
    }
}

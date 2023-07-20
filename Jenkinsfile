pipeline{
    agent { label 'antares' }

    stages{
        stage('Checkout Source'){
            steps{
                git url:'https://github.com/FernandoRD/rotten-potatoes.git', branch:'main'
            }        
        }
        stage('Build Image'){
            steps{
                script{
                    dockerapp = docker.build("fernandord/rotten-potatoes:${env.BUILD_ID}", '-f ./src/Dockerfile .')
                }
            }
        
        }
        
    }
}

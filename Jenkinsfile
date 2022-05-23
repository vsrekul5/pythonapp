pipeline{
    agent any
    environment{
        app = ''
    }
    stages{
        stage('Build'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vsrekul5/pythonapp.git']]])                                
            }
        }
        stage('build docker image'){
            steps{
                script{
                 app = docker.build("pyapp")
                }
            }
            
        }
        stage('create container'){
            steps{
                script{
                    docker.withRegistry('https://118875261478.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:ecrid1') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }              
                
                }            
            }
        }
    }
}
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
                    app = docker.build("partifact/pyapp")
                 //app = docker.build("pyapp")
                 //sh 'docker build -t partifact .'
                 //sh 'docker tag partifact:latest 118875261478.dkr.ecr.us-east-1.amazonaws.com/partifact:latest'
                }
            }
            
        }
        stage('Push container image'){
            steps{
                script{
                    docker.withRegistry('https://118875261478.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:ecrid1') {
                    //app.push("${env.BUILD_NUMBER}")
                    app.push("latest")                    
                    }              
                
                }            
            }
        }
    }
}
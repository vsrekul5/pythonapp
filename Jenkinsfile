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
                    //app = docker.build("partifact")
                 //app = docker.build("pyapp")
                 //app.run('-p 8085:5000')
                 sh 'docker build -t jenkins .'
                 sh 'docker tag jenkins:latest public.ecr.aws/q2r8c9m4/jenkins:latest'
                }
            }
            
        }
        stage('Push container image'){
            steps{
                script{
                    //docker.withRegistry('https://118875261478.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:ecrid1') {
                    aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/q2r8c9m4
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")                    
                               
                
                }            
            }
        }
    }
}

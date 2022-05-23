pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vsrekul5/pythonapp.git']]])                                
            }
        }
        stage('build docker image'){
            steps{
                sh 'docker --version'
                sh 'sudo docker build -t vsrekul/pyapp .'
            }
            
        }
    }
}
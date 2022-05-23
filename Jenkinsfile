pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vsrekul5/pythonapp.git']]])
            }            
        }
    }
}

pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/vsrekul5/pythonapp.git'
            }
        }
    }
}
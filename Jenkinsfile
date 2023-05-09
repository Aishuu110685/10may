pipeline{
    agent any
    
    tools {
        maven 'mymaven'
            }
    stages{
        
        stage('Git Clone'){
            
            steps{
                git branch: 'main', url: 'https://github.com/Aishuu110685/without.git'
            }
        }
        
        stage('Build'){
            steps{
                sh 'mvn install'
            }
        }
        
        stage('Docker Build'){
            steps{
                sh 'docker build -t aishwarya5502/myjavaproject10may .'
            }
        }
        
        stage('Docker Push'){
            steps{
                withCredentials([string(credentialsId: 'dockerinfo', variable: 'dockerpush')]) {
                 
                sh 'docker login -u aishwarya5502 -p ${dockerpush}'
                }
                 sh 'docker push aishwarya5502/myjavaproject10may'
            }
           
        }
    }
}

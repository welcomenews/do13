pipeline {
    agent any
    stages {
        stage('Git clone') {
           steps {
             script {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                userRemoteConfigs: [[url: 'git@github.com:welcomenews/do13.git']]])
             }    
           }    
        }    
        stage('Install nginx') {
            steps {
                sh 'apt insatll nginx -y'    
            }
        }
        stage('Configure nginx') {
                sh 'mkdir -p /var/www/html/releases'
                sh 'cp /var/lib/jenkins/workspace/install-nginx/index.html /var/www/html/releases/'
        }    
     }   
}     

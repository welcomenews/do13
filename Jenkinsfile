pipeline {
    agent any
    stages {
        stage('Git clone') {
           steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                userRemoteConfigs: [[url: 'git@github.com:welcomenews/do13.git']]])
           }    
        }    
    //    stage('Install nginx') {
    //        steps {
    //            sh 'sudo apt install nginx -y'    
    //        }
    //    }
        stage('Configure nginx') {
            steps {
                sh 'sudo mkdir -p /var/www/html/releases'
                sh 'cp /var/lib/jenkins/workspace/install-nginx/index.html /var/www/html/releases/'
            }    
        }    
     }   
}     

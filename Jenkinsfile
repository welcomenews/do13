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
                sh 'sudo mkdir -p /var/www/html/releases/v0.1'
                sh 'sudo cp /var/lib/jenkins/workspace/install-nginx/index.html /var/www/html/releases/v0.1'
                sh 'sudo ln -s releases/v0.1/ index-simlink'
                sh 'sudo cp nginx.conf /etc/nginx/'
                sh 'systemctl restart nginx.service'
            }    
        }    
     }   
}     

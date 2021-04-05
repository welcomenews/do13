// Define variable
def version = 'v0.1'

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
                sh 'sudo mkdir -p /var/www/html/releases/${version}'
                sh 'sudo cp /var/lib/jenkins/workspace/install-nginx/index.html /var/www/html/releases/${version}'
                sh (script: 'if (fileExists("index-simlink")) {
                    sh 'sudo rm index-simlink'
                }')    
                sh 'sudo ln -s releases/${version}/ index-simlink'
                sh 'sudo cp nginx.conf /etc/nginx/'
                sh 'sudo systemctl restart nginx.service'
            }    
        }    
     }   
}     

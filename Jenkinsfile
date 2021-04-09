// Define variable
def version = 'v0.2'

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
        stage('Remove index-simlink') {
            when { expression { return fileExists ('/var/www/html/index-simlink') } }
            steps {
              sh 'sudo rm -rf /var/www/html/index-simlink'
            }  
        }    
            
        stage('Configure nginx') {   
            steps {
                sh "sudo mkdir -p /var/www/html/releases/$version"
                sh "sudo cp /var/lib/jenkins/workspace/install-nginx/index.html /var/www/html/releases/$version"
                sh "sudo ln -s /var/www/html/releases/$version/ /var/www/html/index-simlink"
      //        sh 'sudo cp nginx.conf /etc/nginx/'
                sh 'sudo systemctl restart nginx.service'
            }    
        }    
     }   
}     

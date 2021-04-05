pipeline {
    agent any

    stages {
        stage('Install nginx') {
            steps {
                //cd 
                sh 'mkdir -p /var/www/html/releases'
                sh 'apt insatll nginx -y'    
                sh 'cp /var/www/html/index.html /var/www/html/releases/'
            }
        }
     }   
}     

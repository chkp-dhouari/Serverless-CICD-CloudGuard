pipeline {
      agent any
     
  stages {
          
         stage('Clone Github repository') {
            
    
           steps {
              
             checkout scm
           
             }
  
          }
    stage('Serverless and CloudGuard Install') {   
       steps {   
             withAWS(credentials: 'AWScreds', region: 'us-east-1'){        
                sh 'sudo apt-get update'
                sh 'sudo apt install -y npm nodejs'
                sh 'npm -v'
                sh 'sudo apt install -y build-essential'
                sh 'sudo npm install serverless -g'
              
                sh 'sudo npm install -D https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
                sh 'sls deploy'
               }
             }
        }
        
        
  } 
}

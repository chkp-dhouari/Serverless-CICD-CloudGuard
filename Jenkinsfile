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
                sh 'apt-get update && apt-get install -y nodej && apt-get install -y npm'
                
                sh 'npm install -g npm@latest && chown -R $(whoami) /usr/local/lib/node_modules'
                sh 'npm i -g npm'
                sh 'npm install serverless -g'
                sh 'npm install -D https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
                sh 'whoami'
                sh 'sls deploy"
               }
             }
        }
        
        
  } 
}

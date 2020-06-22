pipeline {
      agent any
      environment {
            token = credentials("token")
      }
  stages {
          
         stage('Clone Github repository') {
           steps {
               checkout scm
                 }
             }
     stage('Serverless and CloudGuard Install') {   
         steps {   
                    
                sh 'apt-get update && apt-get install -y nodejs && apt-get install -y npm'
                sh 'npm i -g npm && npm install serverless -g'
                sh 'npm install -D https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
                }
              }
           
        
        stage("Deploying Serverless app with Cloudguard Security"){
             steps {  
               withAWS(credentials: 'awscreds', region: 'us-east-1'){
                  sh 'sls deploy'
               }
             }
        }        
   } 
}

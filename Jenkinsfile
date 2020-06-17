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
                   
         script {      
             try{
                sh 'apt install -y npm'
                sh 'apt install –yes nodejs' 
                sh 'npm install serverless -g'
                sh 'npm install -g https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
           
               } catch (Exception e) {
    
                 echo "Code Analysis is BLOCK and recommend not using the source code"  
                  }
              }
            }
         }
           
           
          stage('Serverless Deploy and CLoudGuard SAST/DAST Phase') {
             
            steps {

              sh 'sls deploy'
              
              
             } 
           }
      
        
        
  } 
}

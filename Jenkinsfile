node {

   stage('SCM Checkout') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/LovesCloud/Javatomcatmavenapplicationdemo'
      }
   
   stage('Build') {
      
       // Get maven home path and build
         def mvnHome =  tool name: 'Maven 3.5.4', type: 'maven'   
         sh "${mvnHome}/bin/mvn package"      
     }
   
   stage('Deploy') {
      sshagent(['56cf3049-5c47-41f1-a3ff-c7faaa816825']) {
        sh 'scp -o StrictHostKeyChecking=no target/*.war rajni@34.73.32.204:/opt/tomcat/latest/webapps'
      }
   }
}

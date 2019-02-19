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
      sshagent(['tomcatdeploymentserver']) {
        sh 'scp -o StrictHostKeyChecking=no target/*.war admin@34.73.32.204:/opt/tomcat/latest/webapps'
      }
   }
}

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
     // sshagent(['56cf3049-5c47-41f1-a3ff-c7faaa816825']) {
     // sshagent(['abeab169-3c7e-4291-98f3-7f190a3d4099']) {
      sshagent(['41e05a25-d97d-4c2e-b953-306bf59a8ad9']) {
        sh 'scp -i StrictHostKeyChecking=no target/*.war root@34.73.80.173:/opt/tomcat/latest/webapps'
        //sh 'scp -o StrictHostKeyChecking=no target/*.war root@3.89.145.107:/opt/tomcat/webapps'
         
        
         // /opt/tomcat/latest/webapps'
      }
   }
}

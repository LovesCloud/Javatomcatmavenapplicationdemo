#!/usr/bin/env groovy

node {
   def mvnHome
   stage('git checkout') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/LovesCloud/Javatomcatmavenapplicationdemo'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      //mvnHome = tool 'Maven 3.5.4'
   }
   
   stage('Build') {
      
       // Get maven home path and build
         def mvnHome =  tool name: 'Maven 3.5.4', type: 'maven'   
         sh "${mvnHome}/bin/mvn package"
      
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('deploy') {
    sshagent(['807ca4ff-aa82-4c14-b9e5-5cba44515031']) {
        sh 'scp -o StrictHostKeyChecking=no target/*.war root@34.192.236.63:/opt/tomcat/webapps'
    }
   }
}

node{
   stage('SCM Checkout'){
     git 'https://github.com/rummansadhit/jenkins_java_tomcat_cicd_1.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'LocalMaven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat'){
      
      sshagent(['tomcat-id']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war rummansadhit@52.146.38.46:/opt/tomcat/apache-tomcat-8.5.71/webapps/'
       }
    
   }


}

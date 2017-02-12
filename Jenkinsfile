node {
   stage('Preparation') { 
      git 'https://github.com/VPPCourseUser/fleetman-position-tracker'
   }
   stage('Build') {
      sh "mvn package"
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'      
   }
  
 
}

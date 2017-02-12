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
   stage('Deploy'){
      withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
           ansiblePlaybook credentialsId: 'ssh-Credentials', installation: 'ansible-installation', playbook: 'deploy.yaml', sudoUser: null      
   }
}     
}

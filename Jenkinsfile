@Library('kartiklib') _


pipeline {
 agent any
 
 stages {
    stage('build') {
      steps {
       script{
      build()
          }     
      }
    }
  
    stage('sonarqube+gate') {
      steps {
       script{
      codecoverage()
          }
         }
       }
     }
    

 
 post {
         always {
              echo 'yes!!'
             /* logstashSend failBuild: true, maxLines: 1000 */
              }
  }

}

pipeline {
 agent any
 stages {
    stage('build') {
      steps {
      logstash {
        bat 'mvn clean package'
        echo 'project build'
        }
      }
    }
    stage('sonarqube') {
      steps {
      logstash {
        withSonarQubeEnv('sonarserver'){
                 bat 'mvn sonar:sonar' 
                echo """" sonarqube1 """
                 echo "sonarqube1currentResult: ${currentBuild.currentResult}"
             }
       }
      }
    }
    stage('gate') {
      steps {
      logstash {
        timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    // Requires SonarQube Scanner for Jenkins 2.7+
                    waitForQualityGate abortPipeline: true
                         echo """" Sonargate1"""
                         echo "sonargate11currentResult: ${currentBuild.currentResult}"
}
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


pipeline {
 agent any
 stages {
    stage('checkout') {
      steps {
      logstash {
        git(url: 'https://github.com/elkjs/new-.git', branch: 'master', changelog: true, /*credentialsId: '580151e44c0c3736bb24e6d141ff26791724f2c6'*/ poll: true)
        }
       }
    }
    stage('build') {
      steps {
      logstash {
        build 'new 1'
        echo 'project build'
        }
      }
    }
    stage('sonarqube') {
      steps {
      logstash {
        build 'new1 sonar'
        echo 'sonarqube'
       }
      }
    }
    stage('gate') {
      steps {
      logstash {
        build 'new1gate'
        echo 'sonar gate'
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


pipeline {
 agent any
 stages {
    stage('checkout') {
      steps {
      logstash {
        git(url: 'https://github.com/elkjs/new-.git', branch: 'master', changelog: true, credentialsId: '10sharma10', poll: true)
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

# post {
#         always {
#              logstashSend failBuild: true, maxLines: 1000
#              }
#
# 
#  }
}


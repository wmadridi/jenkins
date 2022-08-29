pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('Test') {
      steps {
        sh '''echo "test"



'''
      }
    }

    stage('Post Build') {
      steps {
        archiveArtifacts(onlyIfSuccessful: true, artifacts: '*/*.war')
      }
    }

    stage('Deploy') {
      steps {
        sh 'rm -r /var/lib/tomcat9/webapps/spark*'
        sh 'cp target/*.war /var/lib/tomcat9/webapps'
      }
    }

  }
}
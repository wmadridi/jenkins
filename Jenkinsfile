
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
                sh 'echo Test'
            }
        }
        stage('Post Build') { 
            steps {
                archiveArtifacts artifacts: '*/*.war', followSymlinks: false
            }
        }
        stage('Deploy') { 
            steps {
                deploy adapters: [tomcat9(credentialsId: 'aa0130e3-5fa5-49f8-959b-f958a225ea23', path: '', url: 'http://localhost:8085')], contextPath: 'test', war: '*/*.war'
            }
        }
    }
}


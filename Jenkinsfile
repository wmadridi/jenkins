

pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}


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
                deploy adapters: [tomcat9(credentialsId: '36f4bf41-38bf-4883-87f8-81adfe9f25ce', path: '', url: 'http://localhost:8080/')], contextPath: 'java', onFailure: false, war: '**/*.war' 
            }
        }
    }
}



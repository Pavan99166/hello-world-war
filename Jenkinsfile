pipeline {
    agent { label 'dev' }
    stages {
    stage('checkout') {
          steps {
              sh "git clone https://github.com/Pavan99166/hello-world-war.git"
            }
        }
        stage('build') {
          steps {
              sh "mvn clean package"
            }
        }
        }
    }


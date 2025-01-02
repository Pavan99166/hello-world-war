pipeline {
    agent { label 'dev' }
    stage('checkout') {
          steps {
              sh "git clone https://github.com/Pavan99166/hello-world-war.git"
            }
        }
    stages {
        stage('build') {
          steps {
              sh "mvn clean package"
            }
        }
        }
    }
}
}

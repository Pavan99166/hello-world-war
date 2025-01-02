pipeline {
    agent { label 'dev' }
    stages {
    stage('checkout') {
          steps {
              sh " rm -rf hello-world-war "
              sh "git clone https://github.com/Pavan99166/hello-world-war.git"
            }
        }
        stage('build') {
          steps {
              sh "mvn clean package"
            }
        }
         stage('deploy') {
          steps {
		       sshagent(['5e52fdd9-5cc2-42d7-ac80-c0f8a08e4de3'])
               sh " scp /opt/jenkins/workspace/hello_world_war_pipeline root@ip-172-31-38-245:/opt/apache-tomcat-10.1.34/webapps "
            }
        }
    }


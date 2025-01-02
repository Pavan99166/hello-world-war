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
               sh " sudo scp /opt/jenkins/workspace/hello_world_war_pipeline/target/hello-world-war-1.0.0.war root@ip-172-31-38-245:/opt/apache-tomcat-10.1.34/webapps "
            }
        }
         stage('Email notification') {
          steps {      
               sh "echo "your build hello_world_war_pipeline is success" | mail -s  "Jenkine build Success:hello_world_war_pipeline" pavankumarks2022@gmail.com "
            } 
         }
    }
}



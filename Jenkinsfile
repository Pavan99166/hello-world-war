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
		  post {
			  success {
			     echo "pipeline success"
				 mail (
				       to:'pavankumarks2022@gmail.com'
					   subject: "job is success:  ${env.JOB_NAME} - ${env.BUILD_NUMBER}",
					   body: "the build is succees for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} was successfull. \n\n" +
                             "view the details here:${env.Build_URL}"
                ) 							 						
        }
failure {
		    echo 'pipeline is failed. please check the logs.'
			mail (
				       to:'pavankumarks2022@gmail.com'
					   subject: "job is failed:  ${env.JOB_NAME} - ${env.BUILD_NUMBER}",
					   body: "the build is failed for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} was successfull. \n\n" +
                             "view the details here:${env.Build_URL}"
							 )
    }
}    
     } 
	}
              
     } 
    }

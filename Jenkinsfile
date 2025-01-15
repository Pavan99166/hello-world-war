pipeline {
    agent { lable 'slave1' } 
    environment {
        ARTIFACT_URL = 'http://13.201.3.51:8082/artifactory/hello-world-war-libs-release/com/efsavage/hello-world-war/1.0.0/hello-world-war-1.0.0.war'
        TOMCAT_PATH = '/opt/apache-tomcat-10.1.34'
    }
    stages {
        stage('Download Artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'artifactory-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    script {
                        // Using a more explicit way of calling shell script with environment variables
                        sh """
                        echo 'Starting artifact download...'

                        cd ${TOMCAT_PATH}/webapps

                        # Correctly fetch the artifact using the credentials
                        curl -L -u "${USERNAME}:${PASSWORD}" -O "${ARTIFACT_URL}"

                        echo 'Artifact downloaded, restarting Tomcat...'

                        cd ${TOMCAT_PATH}/bin
                        ./shutdown.sh
                        sleep 10  # Wait for a few seconds to allow Tomcat to shut down

                        ./startup.sh
                        echo 'Tomcat started successfully.'
                        """
                    }
                }
            }
        }
    }
}

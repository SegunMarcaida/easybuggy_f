pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven3"
    }

    stages {
        stage('Test') {
            steps {
                // Run Maven on a Unix agent.
                sh "mvn test"
            }
        }
        stage('Build') {
            steps {
                //Anális with sonarqube
                    
                // Run Maven on a Unix agent.
                sh "mvn clean package"
                
                //Compilation+Packaged
                sh "mvn install"
            }
        }
    }
}

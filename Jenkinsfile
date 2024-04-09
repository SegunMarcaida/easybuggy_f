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
                sh "mvn clean verify sonar:sonar -Dsonar.projectKey=easy-buggy -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqp_f1d40dd817f4d04263ece5948d7fd7be887bcc4e"
                    
                // Run Maven on a Unix agent.
                sh "mvn clean package"
                
                //Compilation+Packaged
                sh "mvn install"
            }
        }
    }
}

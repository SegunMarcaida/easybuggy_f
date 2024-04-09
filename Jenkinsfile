pipeline {
    agent any

    tools {
        // Asegúrate de que Maven esté configurado correctamente en Jenkins
        maven 'Maven3'
    }

    stages {
        stage('Preparar') {
            steps {
                // Obtiene el código fuente del repositorio
                checkout scm
            }
        }

        stage('PMD') {
            steps {
                // Ejecuta PMD
                sh '''
                echo "Ejecutando PMD..."
                pmd check -f text -R rulesets/java/quickstart.xml -d easybuggy -r pmd-report_easybuggy.txt
                '''
            }
        }

        stage('Compilar y Testear') {
            steps {
                // Cambia al directorio del proyecto y ejecuta las pruebas con Maven
                dir('easybuggy') {
                    sh '''
                    echo "Ejecutando pruebas con Maven..."
                    mvn test

                    echo "Ejecutando Maven Install..."
                    mvn install
                    '''
                }
            }
        }
    }

    post {
        // Acciones a realizar después de completar las etapas, por ejemplo, limpiar o enviar notificaciones
        always {
            echo 'Proceso completado.'
        }
    }
}

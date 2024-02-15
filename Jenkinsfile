pipeline{
    agent any
    tools{
        maven 'Maven3'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts:'/**target/*.war'
                }
            }
        }
        stage('Deploy to Tomcat server'){
            steps{
              deploy adapters: [tomcat9(credentialsId: '8dadb2a6-3fea-4297-9147-85ca115c5144', path: '', url: 'https://tomcat.apache.org/tomcat-9.0-doc/building.html#Install_Apache_Ant')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}

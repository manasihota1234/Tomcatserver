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
          stage('Deploy to container'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.91.76.36:8080/')], contextPath: null, war: '**/*.war'
            }
          }
        }
}

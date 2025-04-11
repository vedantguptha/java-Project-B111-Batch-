pipeline{
    agent any
    tools{
         maven "maven"
    }
    stages{
        stage('Clean') {
            steps {
                cleanWs()
            }
        }
        stage ("Code Commit"){
            steps{
                git changelog: false, poll: false, url: 'https://github.com/vedantguptha/java-Project-B111-Batch-.git'
            }
        }
        stage('Unit Test maven') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Integration Test maven') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage ('Package') {
            steps {
                sh 'mvn package'
            }  
        }
          
    }
}
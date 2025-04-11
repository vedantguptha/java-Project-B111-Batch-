pipeline{
    agent any
    tools{
         maven "maven"
    }
    environment {
              APP_NAME = "loginregisterapp-1.0.0" 
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
        stage('Artifactory') {
            steps {
                sh 'aws s3 cp $WORKSPACE/target/*.war s3://b111-lapw-labs/${APP_NAME}.war'
            }
        }   
    }
}
pipeline{
    agent any
    tools{
         maven "maven"
    }
    environment {
              APP_NAME = "loginregisterapp" 
    }
    parameters {
        string(name: 'APP_VERSION', defaultValue: '1.0.0', description: 'Enter App Version')
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
        stage ('Print Version number') {
            steps {
                 echo "New Application Version -, ${params.APP_VERSION}"
            }  
        }
        stage('Artifactory') {
            steps {
                sh 'aws s3 cp $WORKSPACE/target/*.war s3://b111-lapw-labs/${APP_NAME}-${params.APP_VERSION}.war'
            }
        }   
    }
}
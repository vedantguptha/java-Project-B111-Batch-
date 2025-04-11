pipeline{
    agent any
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
    }
}
pipeline{
    agent any
    stages{
        stage ("Code Commit"){
            steps{
                git changelog: false, poll: false, url: 'https://github.com/vedantguptha/java-Project-B111-Batch-.git'
            }
        }
    }
}
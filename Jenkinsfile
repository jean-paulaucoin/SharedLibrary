pipeline {
    agent any
  
    tools {
        maven 'Maven 3.8.4'
    }
  
    stages {
        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/jean-paulaucoin/SharedLibrary.git'
                sh 'mvn clean package'
            }
        }
      
        stage('Test') {
            steps {
                echo 'hello test'
            }
        }
      
        stage('Pre-Prod') {
            steps {
                echo 'hello pre-prod. you will have to pass code quality percentage to continue'
            }
        }
      
        stage('Generate Artifact') {
            steps {
                sh 'cp target/*.jar ./ProdArtifacts'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'ProdArtifacts/*.jar', fingerprint: true
                }
            }
        }
      
        stage('Deploy') {
            steps {
                echo 'congrats, you made it through sonar. goodbye!!'
            }
        }
    }
}

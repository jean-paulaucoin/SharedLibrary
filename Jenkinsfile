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
      
        stage('Pre-Prod') {
            steps {
                echo 'Here is where we can plug in SonarQube checks before the Prod Artifacts are created'
            }
        }
      
        stage('Create Prod Artifacts') {
            steps {
                sh 'cp target/*.jar .'
            }
            post {
                success {
                    archiveArtifacts '*.jar'
                }
            }
        }
      
        stage('Deploy') {
            steps {
                echo 'App Deploying...'
            }
        }
    }
}

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
                sh 'ls | grep -v -E "(jenkinsfile|.java|.xml|.png)$" && exit 1 || echo "Files are valid, continue."'
            }
        }
      
        stage('Pre-Prod') {
            steps {
                echo 'hello pre-prod. you will have to pass code quality percentage to continue'
            }
        }
      
        stage('Generate Artifact') {
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
                echo 'congrats, you made it through sonar. goodbye!!'
            }
        }
    }
}


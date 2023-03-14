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
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
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
    stage('Deploy') {
      steps {
        echo 'congrats, you made it through sonar. goodbye!!'
      }
    }
  }
  step([
  $class: 'ArtifactArchiver',
  artifacts: '**/target/*.jar',
  fingerprint: true
])
def artifact = "$BUILD_NUMBER-${env.JOB_NAME}.jar"
echo "Artifact generated: $artifact"
}

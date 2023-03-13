pipeline {
  agent any
  
  stages {
    stage('Build') {
      steps {
        echo 'hello build'
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
        echo 'congrats, you made it through sonar. goodbye!'
      }
    }
  }
}

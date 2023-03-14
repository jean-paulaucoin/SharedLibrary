pipeline {
  agent any
  
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
    stage('Deploy') {
      steps {
        echo 'congrats, you made it through sonar. goodbye!!'
      }
    }
  }
}

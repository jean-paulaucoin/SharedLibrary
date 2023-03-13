pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
      
    stage('Deploy') {
//       environment {
//         PROD_HOST = 'prod.example.com'
//         PROD_USER = credentials('prod-ssh-user')
//         PROD_KEY = credentials('prod-ssh-key')
//       }
      steps {
        echo 'made it this far. DEPLOYING';
      }
    }
  }
}

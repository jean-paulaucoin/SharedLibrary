pipeline {
    agent any

    stages {
        stage('User Input') {
  steps {
    script {
      def userInput = input(
        message: 'Enter the name of the file to create:',
        parameters: [
          string(
            name: 'fileName',
            defaultValue: 'newfile.txt',
            description: 'The name of the new file'
          )
        ]
      )
      sh("touch ${userInput}")
      sh("echo 'New file created!'")
    }
  }
}
        stage('Build') {
            steps {
                sh 'echo "Building the application"'
            }
        }
    }
}

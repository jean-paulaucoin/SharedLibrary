pipeline {
    agent any

    stages {
        stage('User Input') {
            steps {
                script {
                    def userInput = input(
                        message: 'Enter the name of the repository to create:',
                        parameters: [
                            string(
                                name: 'repoName',
                                defaultValue: 'my-repo',
                                description: 'The name of the new repository'
                            )
                        ]
                    )
                    echo "Creating repository ${userInput.repoName}"
                    // add code to create the repository
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


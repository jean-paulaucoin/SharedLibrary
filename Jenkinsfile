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
                    echo "Creating repository ${userInput}"
                    // add code to create the repository
                }
            }
        }
        stage('Create File') {
            steps {
                script {
                    def repoName = env.CHANGE_ID ?: 'my-repo' // use default value if running outside of a pull request
                    sh "touch ${repoName}.txt"
                    withCredentials([usernamePassword(credentialsId: 'jeanpaulaucoin', usernameVariable: 'jeanpaulaucoin', passwordVariable: 'Sam$ung96123!')]) {
                        sh """
                            git config --global user.email "aucoinjeanpaul@gmail.com"
                            git config --global user.name "Jean-Paul Aucoin"
                            git clone https://github.com/<jean-paulaucoin/SharedLibrary/>/${repoName}.git
                            cd ${repoName}
                            git checkout -b add-file
                            cp ../${repoName}.txt .
                            git add .
                            git commit -m "Add ${repoName}.txt"
                            git push --set-upstream origin add-file
                        """
                    }
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

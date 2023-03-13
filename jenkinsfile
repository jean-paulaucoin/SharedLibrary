pipeline {
    agent any

    stages {
        stage('Input') {
            input {
                message 'Enter the name of the GitHub repository:'
                parameters {
                    string(name: 'REPO_NAME', defaultValue: '', description: '')
                }
            }
        }

        stage('Clone') {
            steps {
                git url: "https://github.com/${params.REPO_NAME}.git"
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}

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
    
    stage('Test') {
        steps {
            script {
                def fileTypes = ["*.java", "*.xml", "*.png"]
                def changedFiles = sh(
                    script: "git diff --name-only HEAD^ HEAD",
                    returnStdout: true
                ).trim().split("\n")
                def invalidFiles = []
                for (String file : changedFiles) {
                    if (!fileTypes.any { type -> file.endsWith(type) }) {
                        invalidFiles.add(file)
                    }
                }
                if (!invalidFiles.isEmpty()) {
                    error "Found the following files that are prohibited per the app type standards: ${invalidFiles.join(', ')}"
                }
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
 

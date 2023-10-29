pipeline {
    agent any
    
    stages {
        stage('Check') {
            steps {
                // Clone the Git repository to the Jenkins workspace
                script {
                    checkout scm
                }
            }
        }
        
        stage('Copy') {
            steps {
                // Copy the file from the Git repository to another location in the workspace
                script {
                    // Specify the source and destination paths
                    def sourceFile = "${JENKINS_HOME}\\workspace\\${JOB_NAME}\\index.html"
                    def destinationDir = "${JENKINS_HOME}\\workspace\\${JOB_NAME}\\copied_files\\"
                    
                    // Create the destination directory if it doesn't exist
                    bat "mkdir ${destinationDir}"
                    ///
                    // Copy the file using the 'cp' shell command
                    bat "copy ${sourceFile} ${destinationDir}"
                }
            }
        }
    }
    
    post {
        always {
            // Clean up: Print the copied files for reference
            script {
                bat "dir ${JENKINS_HOME}\\workspace\\${JOB_NAME}\\copied_files\\"
            }
        }
    }
}

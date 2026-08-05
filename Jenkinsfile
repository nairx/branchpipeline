pipeline {
    agent any

    tools {
        jdk 'JDK17'       // Name configured in Jenkins
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Current Branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Compile') {
            steps {
                bat 'javac src\\App.java'
            }
        }

        stage('Run') {
            steps {
                bat 'java -cp src App'
            }
        }

        stage('Branch Specific') {
            steps {
                script {

                    if (env.BRANCH_NAME == "main") {
                        echo "Running Production Tasks"
                    }
                    else if (env.BRANCH_NAME == "develop") {
                        echo "Running Development Tasks"
                    }
                    else {
                        echo "Running Feature Branch Tasks"
                    }

                }
            }
        }

    }

    post {
        always {
            echo "Pipeline Finished"
        }

        success {
            echo "Build Successful"
        }

        failure {
            echo "Build Failed"
        }
    }
}

pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Pull Code from GitHub') {
            steps {
                checkout scm
            }
        }

        stage('Compile Java Program') {
            steps {
                sh '''
                    mkdir -p out
                    javac -d out hello.java
                '''
            }
        }

        stage('Execute Java Application') {
            steps {
                sh 'java -cp out hello'
            }
        }
    }

    post {
        success {
            echo 'Java application executed successfully!'
        }

        failure {
            echo 'Java application execution failed!'
        }
    }
}

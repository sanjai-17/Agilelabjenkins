pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Compile Java Program') {
            steps {
                bat 'javac Calculator.java'
            }
        }

        stage('Run Java Program') {
            steps {
                bat 'java Calculator'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '*.class', fingerprint: true
            echo 'Build Successful! Class file archived.'
        }

        failure {
            echo 'Build Failed'
        }
    }
}
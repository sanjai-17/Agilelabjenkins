pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/yourusername/calculator-ci.git'
            }
        }

        stage('Compile Java Program') {
            steps {
                sh 'javac Calculator.java'
            }
        }

        stage('Run Java Program') {
            steps {
                sh 'echo "5 3 +" | java Calculator'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '*.class', fingerprint: true
        }

        failure {
            echo 'Build Failed'
        }
    }
}
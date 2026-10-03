pipeline {
    agent any

    triggers {
        githubPush()
    }

    tools {
        maven 'Maven'
    }

    stages {

        stage('git repo & clean') {
            steps {
                bat "if exist mavenjava rmdir /s /q mavenjava"
                bat "git clone https://github.com/holikagiriboina/mavenjava.git"
                bat "mvn clean -f mavenjava"
            }
        }

        stage('install') {
            steps {
                bat "mvn install -f mavenjava"
            }
        }

        stage('test') {
            steps {
                bat "mvn test -f mavenjava"
            }
        }

        stage('package') {
            steps {
                bat "mvn package -f mavenjava"
            }
        }
    }
}

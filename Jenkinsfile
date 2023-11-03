pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hi') {
            steps {
                echo 'Hello'
            }
        }
        stage('Hay Hi') {
                    steps {
                        echo 'Hello'
                    }
                }
        stage('git checkout') {
                            steps {
                                git branch: 'feature_muhammad', changelog: false, credentialsId: 'git_credentials_msrahman', poll: false, url: 'https://github.com/msrahman82/ibt-maven.git'
                                sh 'ls -all'
                            }

                        }
    }
}
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
                echo 'Hi World'
            }
        }
         stage('Git Checkout') {
            steps{
            checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/feature/Derick']], extensions: [], userRemoteConfigs: [[credentialsId: '590e1990-6318-4b7c-86cb-f9c7cbf0b390', url: 'https://github.com/IBT-learning/ibt-maven.git']])
            }
        }
        stage("List files "){
            steps{
             sh "ls"
           }
       }
        stage(" Testing webhook "){
                   steps{
                    echo "success webhook"
                  }
              }
    }
}

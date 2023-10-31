pipeline {
    agent any

    stages{
    stage('Git checkout') {
        steps{
            git branch: ‘feature-rizme' , changelog: false, credentialsId: 'GitHub_user_rizme', poll: false, url: 'https://github.com/IBT-learning/ibt-maven.git'
        }
    }
    stage('Validate'){
        steps{
            withMaven(maven: 'maven_3.8') {
               sh 'mvn validate'
            }
        }
    }
    stage('Compile'){
        steps{
            withMaven(maven: 'maven_3.8') {
                sh 'mvn compile'
        }
    }
   }
     stage('Test'){
            steps{
                withMaven(maven: 'maven_3.8') {
                    sh 'mvn test'
            }
        }
    }
    stage('SonarQube Analysis'){
        environment{
            sonarScan = tool 'ibt-sonarqube_4.8'
        }
        steps{
            withSonarQubeEnv(credentialsId: 'student-sonar-token', installationName: 'IBT sonarqube') {
                sh "${env.sonarScan}/bin/sonar-scanner"
            }
        }
    }
     stage('Package'){
                steps{
                    withMaven(maven: 'maven_3.8') {
                        sh 'mvn package'
                }
            }
        }
     stage('Dynamic Scan'){
        steps{
            dependencyCheck additionalArguments: '''
                     -o "./"
                     -s "./"
                     -f "ALL"
                    --prettyPrint ''', odcInstallation: 'dependency-check'
             dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }

     }

     }

}

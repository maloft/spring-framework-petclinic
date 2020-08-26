pipeline {
    agent any
    tools{
        maven "Maven"
    }
    
    stages{
        stage(verify) {
            steps {
               sh 'mvn -v'
            }
        }
        
         stage(compile) {
            steps {
                sh 'mvn clean compile'
            }
        }
         stage(test) {
            steps {
               sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    slackSend channel: 'jenkins-training', message: 'Mohamed : jenkins sois jentil', teamDomain: 'devinstitut', tokenCredentialId: 'slack-token'
                }
            }
        }
    }
}
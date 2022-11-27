pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello: Slack Notifications'
            }
        }
        stage('STAGE TEST') {
            steps {
                script {
                    env.STAGE = 'STAGE TEST'
                    sh 'echo "Testins stage && Slack"'
                }
            }
            post {
                success {
                    slackSend color: 'good', message: "Build Success: [Hector Zapata] [${JOB_NAME}] Ejecucion Exitosa", teamDomain: 'D044YF496TY', tokenCredentialId: 'token-slack'
                }
                failure {
                    slackSend color: 'danger', message: "Build Failure: [Hector Zapata] [${env.JOB_NAME}]  Ejecucion fallida en stage [${env.STAGE}]", teamDomain: 'D044YF496TY', tokenCredentialId: 'token-slack'
                }
            }
        }
        stage('Good Bye') {
            steps {
                echo 'Good Bye: Slack Notifications'
            }
        }
    }
}

pipeline{
    agent any

    environment {
        MSTEAMS_HOOK = "https://quatrixglobal.webhook.office.com/webhookb2/61fe461b-4257-4bb2-bc64-6b73fbe8351b@a96a137b-5bac-4d28-8f5b-9ded43babdcf/JenkinsCI/c7c81ddb9cd34aa2b6603d178c289273/a423d303-77b2-4f8b-af1e-7f98950259fb/V2X-5LS4W0EzmjeaB5DLS8DOK5e668MlnGiemHWgPbufc1"
    }
    stages{
        stage("A"){
            steps{
                echo "========executing step 1========"

                sh ''' 
                    echo "installed office plugin on jenkins"
                    '''
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            office365ConnectorSend(
                status: "Build status",
                webhookUrl: "${MSTEAMS_HOOK}",
                message: "Build Successful",
                color: "#00ff00",

            )
        }
        failure{
            office365ConnectorSend(
                status: "Build status",
                webhookUrl: "${MSTEAMS_HOOK}",
                message: "Build Failed",
                color: "#EE4B2B",
            )
        }
    }
}
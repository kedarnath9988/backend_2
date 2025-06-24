pipeline{
    agent{
        label 'AGENT-01'
    }
    options {
            timeout(time: 30, unit:'MINUTES')
            disableConcurrentBuilds()
            ansiColor('xterm')
    }
    environment{
        def appversion = ''
    }

    stages {
        stage('getversion'){
            steps{
                script{
                    def application_version = readJSON file: 'package.json'
                        appversion  = application_version.version 
                    echo "the application version is $appversion"

                }
            }
        }

        stage('install dependencies ') {
            steps{
            sh"""
            npm install 
            echo "$appversion"
            """
        }
        }
        stage('artifact'){
            steps{
                sh"""
                zip -r backend-$appversion.zip  * -x Jenkinsfile -x backend-$appversion.zip
                
               """
            }
        }

    }
    post{
        always{
            echo "i will excuite always"
            deleteDir()
        }
        success{
            echo "pipeline excuited successfully "
        }
        failure {
            echo "pipeline failed "
        }
    }
}
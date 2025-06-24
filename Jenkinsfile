pipeline{
    agent{
        label 'AGENT-01'
    }
    options {
            timeout(time: 30, unit:'MINUTES')
            disableConcurrentBuilds()
            ansiColor('xterm')
    }

    stages {
        stage('build') {
            steps{
            sh"""
            echo "this is build stage"
            ls -ltr 
           
            """
        }
        }

    }
    post{
        always{
            echo "i will excuote always"
        }
        success{
            echo "pipeline excuited successfully "
        }
        failure {
            echo "pipeline failed "
        }
    }
}
pipeline {
    agent { 
        node {
            label 'docker-agent-python'
            }
      }
    triggers {
        pollSCM '* * * * *' //Aktives Polling jeden Minute - *5*** ist alle 5 Minuten
    }
    stages {
        stage('42Crunch Audit-Scan'){
            steps {
            echo "Run Audit-Scan "
            echo "The build URL of this Job is: ${env.GIT_LOCAL_BRANCH}"
            echo "The build URL of this Job is: ${env.GIT_URL}"
            sleep 37
        }
        }
        stage('Deploy to API-Gateway') {
            steps {
                echo "Testing.."
                sleep 21
            }
        }
        stage('API-Test') {
            steps {
                echo 'Deliver....'
                sleep 13
            }
        }
    }
}
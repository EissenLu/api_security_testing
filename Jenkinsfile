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
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                pip install -r requirements.txt
                '''
            }
        }
        stage('42Crunch Audit-Sacn'){
            steps {
            audit repositoryName: "${env.GIT_URL}", 
            branchName: "${env.GIT_LOCAL_BRANCH}", 
            credentialsId: '42crunch-token-id', 
            minScore: 75, 
            platformUrl: 'https://platform.42crunch.com', 
            logLevel: 'DEBUG'
        }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py -name="Test Name"
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
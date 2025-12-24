pipeline {
    agent {
    node {
        label "AGENT-1"
    }
    }
    environment {
        COURSE="Jenkins"
        TRAINER="SIVA"
    }
        options {
        timeout(time: 10, unit: 'SECONDS') 
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
            steps {
                
                script { 

                sh  """
                 echo "Building"
                 echo "$COURSE"
                 #sleep 10

                    """
                }
            }
        }
        stage('Stage') {
            steps {
                
                script { 

                sh  """
                 echo "Staging"
                 echo "$TRAINER"
                    """
                }
            }
        }
                stage('Test') {
            steps {
                
                script { 

                sh  """
                 echo "Testiing"
                 env

                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying"
            }
        }
    }

    post{
        always{
            echo 'I will always say Hello again!'
            cleanWs()
        }
        success {
            echo 'I will run if  success !'
        }

        failure {
            echo 'I will run if failure !'
        }
        aborted {
           echo 'Pipeline is aborted executing more time'
        }
    }
}


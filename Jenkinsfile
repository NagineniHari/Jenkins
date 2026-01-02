pipeline {
    // This steps are Pre-build sections
    agent {
    node {
        label "AGENT-1"
    }
    }
    environment {
        COURSE="Jenkins"
        TRAINER="SIVA"
        DURATION="120HRS"
    }
        options {
       // timeout(time: 10, unit: 'MINUTES') 
        disableConcurrentBuilds()
    }
        parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
      // This is build section part
    stages {
        stage('Build') {
            steps {
                
                script { 

                sh  """
                 echo "Building"
                 echo "$COURSE"
                 #sleep 10
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.DEPLOY}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"


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
        // approvals added 
        stage('Deploy') {
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
          when {
           expression { "$params.DEPLOY" =="true"}
          }

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


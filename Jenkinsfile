pipeline{
    agent{
        label 'jenkins-agent'
    }

    options {
        timeout (time : 30 , unit : 'MINUTES' )
        disableConcurrentBuilds()
    }
    stages {
        stage('Init'){
            steps{
                sh """
                    cd terraform
                    terraform init
                """
            }
        }
        stage('Plan'){
            steps{
                sh """
                    pwd
                    cd terraform
                    terraform plan
                """
            }
        }

        stage('Deploy'){
            steps{
                sh """
                    cd terraform
                    terraform apply -auto-approve
                """
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}
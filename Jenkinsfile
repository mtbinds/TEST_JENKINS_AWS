pipeline {
    agent any

    environment {
        AWS_CREDENTIALS = 'aws-credentials'
        TF_VAR_region = 'us-east-1'
    }

    stages {
        stage('Checkout') {
            steps {
                // Cloner votre dépôt contenant les fichiers Terraform
                git 'https://github.com/mtbinds/TEST_JENKINS_AWS.git'
            }
        }

        stage('Terraform Init') {
            steps {
                script {
                    terraformInit()
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                script {
                    terraformPlan()
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    terraformApply()
                }
            }
        }
    }
}

def terraformInit() {
    sh 'terraform init'
}

def terraformPlan() {
    sh 'terraform plan -out=tfplan'
}

def terraformApply() {
    sh 'terraform apply -auto-approve tfplan'
}
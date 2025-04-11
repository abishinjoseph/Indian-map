pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
        TF_VAR_bucket_name = 'abishin-terraform-bucket-a36f08f6'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-creds',
                    url: 'https://github.com/abishinjoseph/Indian-map.git'
            }
        }

        stage('Initialize Terraform') {
            steps {
                bat 'terraform init'
            }
        }

        stage('Validate Terraform') {
            steps {
                bat 'terraform validate'
            }
        }

        stage('Plan Terraform') {
            steps {
                bat 'terraform plan'
            }
        }

        stage('Apply Terraform') {
            steps {
                bat 'terraform apply -auto-approve'
            }
        }
    }
}

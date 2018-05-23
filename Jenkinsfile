#!groovy

env.TERRAFORM_CMD = 'sudo docker run --network host -w /app -v /home/maxstack/.aws:/root/.aws -v /home/maxstack/.ssh:/root/.ssh -v /home/maxstack/sample:/app hashicorp/terraform:light'

node {

  stage ('Checkout') {
    checkout scm
  }

  stage ('pull latest light terraform image') {
    sh 'sudo docker pull hashicorp/terraform:light'
  }

  stage ('Terraform Plan') {
    sh '${TERRAFORM_CMD} -version'
  }

  // Optional wait for approval
  input 'Deploy stack?'

  stage ('Terraform Apply') {
    sh '${TERRAFORM_CMD} -version'
  }

  stage ('Post Run Tests') {
    echo "Insert your infrastructure test of choice and/or application validation here."
    sleep 2
    sh '${TERRAFORM_CMD} -version'
  }

}

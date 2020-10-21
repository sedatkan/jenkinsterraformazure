pipeline {
 
  agent {
    docker {
      image 'hashicorp/terraform:light'
      args '--entrypoint='
    }
  }
  stages {
    stage('Terraform Plan') { 
      steps {
        
        sh 'echo started'  
        sh  'terraform init'
        sh  'terraform validate'
        sh  'terraform plan -no-color -out=create.tfplan' 
        sh  'terraform apply --auto-approve'
        input ('Execute plan')        
}
    }
  
    stage ('Terraform Destroy') {
      steps{
      sh "terraform destroy --auto-approve"
      }
          
      }
  }
}

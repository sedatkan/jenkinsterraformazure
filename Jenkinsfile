pipeline {
 
  agent {
    docker {
      image 'zenika/terraform-azure-cli:latest'
      args "--user root --privileged"     
}
  }
  stages {
    stage('Terraform Plan') { 
      steps {
        
        sh 'echo started'  
        sh 'az login  '
        sh  'terraform init'
        sh  'terraform validate'
        sh  'terraform plan -no-color -out=create.tfplan' 
        
               
}
    }
  
      stage('Approval') {
      steps {
        script {
          def userInput = input(id: 'confirm', message: 'Apply Terraform?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Apply terraform', name: 'confirm'] ])
        }
      }
    }  

    
  stage('TerraformApply') {
      steps {
        script {
          sh 'terraform version'
      }
    }
}

    stage ('Terraform Destroy') {
      steps{
      sh "terraform version"
      }
          
      }

  }
}



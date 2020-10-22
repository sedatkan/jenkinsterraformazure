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
        sh 'az login --service-principal -u  d01c49cf-d4cc-47c4-8f5b-b834511bf1b2   -p  1p2PgHsgPQn_7rgHjz2r3c94wSKmzu0MSP   --tenant d73fdb28-d3ed-4e01-b2a4-a4682c19d1bd'
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



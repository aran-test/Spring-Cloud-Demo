pipeline {
  
  agent any
  
  stages {
    stage('Test') {
        steps {
            echo 'Testing'
        }
    }
    
    stage('Build Docker Image') {
        steps {
            echo 'Building Image'
        }
    }

    stage('Deploy to develop') {
        when {
            branch 'develop'
        }
        steps {
            echo 'Deploying to develop'
        }
        
        when {
            expression { BRANCH_NAME ==~ /hotfix|hotfix\/[0-9]*|release\/[0-9]*/ }
        }
        steps {
            echo 'Deploying to Staging and QA'
        }
    }
  }
}
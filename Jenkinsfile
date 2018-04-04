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

    stage('Deploy for develop') {
        when {
            branch 'develop'
        }
        steps {
            echo 'Deploying to develop'
        }
    }

    stage('Deploy for release or hotfix') {
        when {
            expression { BRANCH_NAME ==~ /hotfix|hotfix\/[0-9]*|release\/[0-9]*/ }
        }
        steps {
            echo 'Deploying to Staging and QA'
        }
    }
    stage('Deploy to Live') {
        when {
            expression { BRANCH_NAME ==~ /hotfix|hotfix\/[0-9]*|release\/[0-9]*/ }
        }
        input {
            message "Should we deploy this version to Live?"
            ok "Go, go, go!"        
        }
        steps {
            echo 'Deploying to Live'
        }
    }
  }
}
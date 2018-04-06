node {
  checkout scm

    if (env.BRANCH_NAME == 'develop') {
        stage('Test'){
            sh './gradlew clean check'
        }

        stage('Build Docker Image') {
            echo 'Building image'
            echo 'Pushing image to AWS ECR'
        }

        stage('Deploy to Developement Environment') {
            echo 'Deploy to Dev'
        }

    } else if (env.BRANCH_NAME ==~ /hotfix|hotfix\/[0-9]*|release\/[0-9]*/) {
        stage('Test'){
            sh './gradlew clean check'
        }
        stage ('Merging changes back to develop') {
            echo "Merging $env.BRANCH_NAME back to develop"
        }
        stage('Build Docker Image') {
            echo 'Building image'
            echo 'Pushing image to AWS ECR'
        }
        stage('Deploy to Stage') {
            echo 'Deploy to Staging'
        }
        stage('Deploy to QA') {
            echo 'Deploy to QA'
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
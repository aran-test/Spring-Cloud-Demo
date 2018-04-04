node {
  checkout scm

    if (env.BRANCH_NAME == 'develop') {
        stage('Test'){
            sh './gradlew clean check'
        }

        stage('Build Docker Image') {
            echo 'Building image'
        }

        stage('Deploy to Developement Environment') {
            echo 'Deploy to Dev'
        }

    } else if (env.BRANCH_NAME ==~ /hotfix|hotfix\/[0-9]*|release\/[0-9]*/) {
        stage('Test'){
            sh './gradlew clean check'
        }

        stage('Build Docker Image') {
            echo 'Building image'
        }
        stage('Deploy to Stage') {
            echo 'Deploy to Staging'
        }
        stage('Deploy to QA') {
            echo 'Deploy to QA'
        }
        

    } 
}
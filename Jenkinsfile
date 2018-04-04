node {
  checkout scm

	if (env.BRANCH_NAME == 'develop') {
		stage('Test'){
			sh './gradlew clean check'
		}

		stage('Build Docker Image'){
			echo 'Building image'
		}

		stage('Deploy to Developement Environment'){
			echo 'Deploy to Dev'
		}

    } else if (env.BRANCH_NAME ==~ """release/*"""){
        stage('Deploy to Test Environment'){
            echo 'Deploy to Staging and QA'
        }
    } else if (env.BRANCH_NAME == 'master') {
        stage('Deploy to Live Environment'){
            echo 'Deploy to Live'
        }
    } else {
        stage('Unknown stage'){
            echo 'No deployment? '
        }
    }
    
}
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

    } else if (env.BRANCH_NAME == 'master') {
        println 'Deploy to live'
    } else if (env.BRANCH_NAME ==~ /release/){
        println 'Deploy to staging'
    } else {
        println "No deployment for branch ${env.BRANCH_NAME}"
    }
    
}
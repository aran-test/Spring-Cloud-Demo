node {
  checkout scm

    stage('Build + Test') {
        sh "./gradlew clean build"
    }

    stage('Deploy') {
    	steps {
	    	if (env.BRANCH_NAME == 'develop') {
	            println 'Deploy to dev'
	        } else if (env.BRANCH_NAME == 'master') {
	            println 'Deploy to live'
	        } else if (env.BRANCH_NAME ~= 'release/*'){
	            println 'Deploy to staging'
	        } else {
	            println "No deployment for branch ${env.BRANCH_NAME}"
	        }
    	}
        
    }
}
node {
  checkout scm

    stage('Build + Test') {
        sh "./gradlew clean build"
    }

    stage('Deploy to Development') {
        when {
        	branch 'develop'
        }
        steps {
                println 'deploying to develop ......'
        }
    }

    stage('Deploy to test envs') {
    	when {
    		branch 'release/*'
    	}
    	steps {
    		println 'deploying to qa and staging.........'
    	}
    }

    stage('deploy to live') {
    	when {
    		branch 'master'
    	}
    	steps {
    		input message: 'Click to deploy to live'
    		println 'Deploying to live.....'
    	}
    }
}
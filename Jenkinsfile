node {
  checkout scm

    stage('Build') {
        def mvnHome = tool 'M3'
        sh "${mvnHome}/bin/mvn package"
    }

    stage('Deploy') {
        if (env.BRANCH_NAME == 'develop') {
            println 'Deploy to dev'
        } else if (env.BRANCH_NAME == 'master') {
            println 'Deploy to test'
        } else if (env.BRANCH_NAME == 'release'){
            println 'Deploy to staging'
        } else {
            println "No deployment for branch ${env.BRANCH_NAME}"
        }
    }
}
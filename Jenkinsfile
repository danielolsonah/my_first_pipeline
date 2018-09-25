pipeline {
    agent any
    stages {
        stage('No-op') {
            steps {
                sh 'ls'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            mail to: 'danielallenolson@gmail.com',
             subject: "Successful Pipeline: ${currentBuild.fullDisplayName}",
             body: "Everything is fine with ${env.BUILD_URL}"
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
        	mail to: 'danielallenolson@gmail.com',
            	subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
            	body: "Something is wrong with ${env.BUILD_URL}"
    	}
        changed {
            echo 'Things were different before...'
        }
    }
}
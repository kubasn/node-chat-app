pipeline {

    agent any

    stages {
        
        stage('Test') {
            steps {
                echo 'Test...'
		     nodejs('npm') {
		sh 'npm install'
                sh 'npm run test'
            }
        }
	}
    }
    
    post {
    
    	always {
    	    echo 'End'
    	}
    	
    	success {
	    echo 'Success'
    	}
    	
        failure {
            echo 'Failure'
            emailext attachLog: true,
                body: "${currentBuild.currentResult}:  build ${env.BUILD_NUMBER} Job ${env.JOB_NAME}",
                to: 'sosinkuba@gmail.com',
                subject: "Result-test failed"
        }
    }
}

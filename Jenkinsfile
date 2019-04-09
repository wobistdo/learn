pipeline {
    agent none
    stages {
        stage ('Example Build') {
            agent{label 'docker-slave0'}
            steps{
                echo 'begin build+++++++++++++++++++++'
                sh 'g++ helloworld.cpp -o helloworld '
                sh 'whereis java'
                echo 'end build+++++++++++++++++++++++'
            }
        }
        stage ('Example Test') {
            agent{label 'docker-slave0'}
            steps{
                echo 'begin test+++++++++++++++++++++'
                sh 'whereis java'
                echo 'end test+++++++++++++++++++++++'
            }
        }
	}
	post {
		always{
			agent{label 'docker-slave0'}
			emailext(
				subject: '${ENV, var="JOB_NAME"}-build log number =  ${BUILD_NUMBER}',
				attachLog: true,
				attachmentsPattern: '*.md',
      				from: env.DEFAULT_REPLYTO,
      				replyTo: env.DEFAULT_REPLYTO, 
				recipientProviders: [developers(),upstreamDevelopers()],
				body: 'this is body'
			)
		}
	}
}

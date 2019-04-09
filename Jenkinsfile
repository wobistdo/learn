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
            agent{label 'docker-slave1'}
            steps{
                echo 'begin test+++++++++++++++++++++'
                sh 'sleep 5s'
                sh 'whereis java'
                echo 'end test+++++++++++++++++++++++'
            }
        }
	post ('Example Send email'){
		always{
			emailext(
				subject: '${ENV, var="JOB_NAME"}-build log number =  ${BUILD_NUMBER}',
				attachmentsPattern: '*.md',
      				from: env.DEFAULT_REPLYTO,
      				replyTo: env.DEFAULT_REPLYTO,
				body: '${FILE, path="email.html"}',
				to: '1057502789@qq.com'
			)
		}
	}
}

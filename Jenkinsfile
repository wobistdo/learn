pipeline {
    agent any
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

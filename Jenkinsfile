pipeline {
    agent any
    // 定义了参数输入
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    }
    stages {
        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"
            }
        }
       stage('Example2') {
            steps {
                echo "Nice to meet you, ${params.PERSON}"
            }
        }
    }
}

pipeline {
    agent {
        kubernetes {
          //cloud 'kubernetes'
          defaultContainer 'alpine'
          yaml '''
            kind: Pod
            spec:
              containers:
              - name: alpine
                image: alpine:3.17.0
                imagePullPolicy: Always
                command:
                - sleep
                args:
                - 99d
    '''
        }
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        // 这里的hello2 是我加的，就是说明，这是stages下的第二个任务 ,就是在pipeline中加单行注释 用 // 就行
        stage('Hello2') {
            steps {
                sh '''echo \'Hello World，i 应该是 可以了 -2 ！！！\'
                ls -a /home/jenkins/agent/workspace'''
            }
        }

        stage('SCM') {
            steps {
                git 'https://github.com/sunmao-dx/EventRetriever.git'
            }
        }
        
        stage('SonarQube analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonar-devops';
                    withSonarQubeEnv('sonarqube-scanner') { // If you have configured more than one global server connection, you can specify its name
                    sh "${scannerHome}/bin/sonar-scanner -X"
                    }
                }
            }
        }
    }
}

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
                echo 'Hello World，i 应该是 可以了 ！！！'
            }
        }
       
    }
}

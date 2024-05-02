pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Maven Build') {
            steps {
                sh 'mvn -DskipTests clean package' 
            }
        }
        stage("Docker Build") {
            steps {
              sh '''
                  #oc start-build --from-build=<build_name>
                  oc start-build --from-dir=.
              '''
            }
        }
    }
}

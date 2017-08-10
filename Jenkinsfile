pipeline {
    agent any
    tools {
        maven 'maven-3.5.0'
    }
    stages {
         stage ('Initialize') {
            steps {
                sh '''
                    export "PATH=/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.141-2.6.10.1.el7:${PATH}"
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"                    
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'source /etc/profile'
                sh 'echo "JAVA_HOME=$JAVA_HOME"'
                sh 'mvn -Dmaven.test.failure.ignore=true install -X' 
            }
          
        }

          stage ('Compile') {
            steps {
               sh 'mvn clean compile'
            }
          
        }


          stage ('Deploy') {
            steps {
               sh 'mvn deploy'
            }
          
        }
    }
}

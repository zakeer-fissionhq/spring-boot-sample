pipeline {
    agent any
    tools {
        maven 'maven-3.5.0'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    sh 'echo "JAVA_HOME=$JAVA_HOME"'
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"                    
                '''
            }
        }

        stage ('Build') {
            steps {
               
               
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

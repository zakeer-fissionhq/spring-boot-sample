pipeline {
    agent any
    tools {
        maven 'maven-3.3.9'
    
    }
   
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"                    
                     echo "JAVA_HOME=${JAVA_HOME}"
                    // next 2 are equivalents
                    sh "${JAVA_HOME}/bin/java -version"
                    sh 'java -version'
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

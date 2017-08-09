pipeline {
    agent any
    tools {
        maven 'maven-3.5.0'
      
    
    }
   
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    export "PATH=/usr/lib/jvm/jre-1.8.0-openjdk:${PATH}"
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

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
                    jdk = tool name: '/usr/lib/jvm/jre-1.8.0-openjdk'
                    env.JAVA_HOME = "${jdk}"
                    echo "jdk installation path is: ${jdk}"
                    // next 2 are equivalents
                    sh "${jdk}/bin/java -version"
                    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
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

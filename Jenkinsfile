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
                '''
            }
        }


  stage('Checkout') {
    sh 'git clone https://github.com/zakeer-fissionhq/spring-boot-sample.git'
  }

  stage('Build') {
    sh 'mvn -B -V -U -e clean package'
  }

  stage('Archive') {
    junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
  }

}
}

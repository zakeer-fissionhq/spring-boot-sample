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
    git 'https://github.com/bertjan/spring-boot-sample'
  }

  stage('Build') {
    sh 'mvn -B -V -U -e clean package'
  }

  stage('Archive') {
    junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
  }

}
}

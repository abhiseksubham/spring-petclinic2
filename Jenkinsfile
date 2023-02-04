pipeline {
  agent any
  stages {
    stage('Complile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''mvn clean verify sonar:sonar \\
  -Dsonar.projectKey=petclinic \\
  -Dsonar.host.url=http://172.31.25.122:9000 \\
  -Dsonar.login=sqp_2fc24fb18b3c406273ebccba348c0630ac780db7'''
      }
    }

  }
}
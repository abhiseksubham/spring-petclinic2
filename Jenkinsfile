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
  -Dsonar.host.url=http://3.110.58.143:9000 \\
  -Dsonar.login=sqp_01433a1d0f74efb99d9aedcb1c5fa2996db603c9'''
      }
    }

  }
}
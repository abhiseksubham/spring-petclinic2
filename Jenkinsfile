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
        sh '''./mvnw sonar:sonar \\
  -Dsonar.projectKey=petclinic \\
  -Dsonar.host.url=http://172.31.25.122:9000 \\
  -Dsonar.login=sqp_01433a1d0f74efb99d9aedcb1c5fa2996db603c9
'''
      }
    }

  }
}
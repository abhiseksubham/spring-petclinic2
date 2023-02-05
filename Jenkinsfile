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

    stage('Unit Tests') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
      }
    }

    stage('Package') {
      steps {
        sh './mvnw package -DskipTests=true'
      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            sh './mvnw spring-boot:run </dev/null &>/dev/null &'
          }
        }

        stage('Integration and Performance Tests') {
          steps {
            sh './mvnw verify'
          }
        }

      }
    }

  }
}
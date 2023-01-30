pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''./mvnw sonar:sonar \\
-Dsonar.projectKey=spring-petclinic \\
-Dsonar.host.url=http://172.31.27.242:9000 \\
-Dsonar.login=sqp_e4471a747f7f3ebe289a6eec2ac9f1ceb125b7cd'''
      }
    }

    stage('Unit Test') {
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
      steps {
        sh './mvnw spring-boot:run </dev/null &>/dev/null &'
      }
    }

  }
}
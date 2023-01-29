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
-Dsonar.projectKey=Spring-PetClinic \\
-Dsonar.host.url=http://172.31.27.242:9000 \\
-Dsonar.login=sqp_06d359678d828c02978d25adfee21829532cfaca'''
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
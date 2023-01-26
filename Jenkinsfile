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
        sh '''mvn sonar:sonar \\
  -Dsonar.projectKey=Spring-PetClinic \\
  -Dsonar.host.url=http://172.31.27.242:9000 \\
  -Dsonar.login=sqp_06d359678d828c02978d25adfee21829532cfaca'''
      }
    }

  }
}
pipeline {
  agent any
  stages {
    stage('compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('static analysis') {
      steps {
        sh '''./mvnw sonar:sonar \\
-Dsonar.host.url=http:// 43.205.133.38 :9000/ \\
-Dsonar.projectKey=petclinic \\
-Dsonar.login=sqp_484a377541a3e4535d53eae206efb72781907152'''
      }
    }

  }
}
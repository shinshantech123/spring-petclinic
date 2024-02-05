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
        sh '''mvn sonar:sonar \\
  -Dsonar.projectKey=petclinic \\
  -Dsonar.host.url=http://localhost:9000 \\
  -Dsonar.token=sqp_484a377541a3e4535d53eae206efb72781907152'''
      }
    }

    stage('unit test') {
      steps {
        junit '**/target/surefire-reports/'
      }
    }

  }
}
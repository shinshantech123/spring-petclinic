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
      parallel {
        stage('unit test') {
          steps {
            sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
          }
        }

        stage('junit') {
          steps {
            junit '**/target/surefire-reports/'
          }
        }

      }
    }

    stage('junit test results') {
      steps {
        junit '**/target/surefire-reports/'
      }
    }

  }
}
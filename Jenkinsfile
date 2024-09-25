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
        sh '''mvn clean verify sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.projectName=\'Petclinic\' \\
  -Dsonar.host.url=http://3.17.149.199:9000 \\
  -Dsonar.token=sqp_541d387979c1aedc118c079cee451452121f8fe8'''
      }
    }

    stage('Unit Tests') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
      }
    }

  }
}
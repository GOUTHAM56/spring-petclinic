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
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.projectName=\'Petclinic\' \\
  -Dsonar.host.url=http://3.17.149.199:9000 \\
  -Dsonar.token=sqp_8dec01c93e62c74d06c5bc0b3e75b899f10a65b4'''
      }
    }

    stage('Unit Tests') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
        junit '**/target/surefire-reports/*.xml'
      }
    }

    stage('Package') {
      steps {
        sh './mvnw package -DskipTests=true'
      }
    }

  }
}
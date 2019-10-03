pipeline {
  agent any
  stages {
    stage("Checkout") {
      steps {
        git url: 'https://github.com/lintmint/calculator.git'
      }
   }
   stage("Compile") {
     steps {
      sh "./gradlew compileJava"
     }
    }
   stage("Code coverage") {
     steps {
      sh "./gradlew jacocoTestReport"
      sh "./gradlew jacocoTestCoverageVerification"
          sh "./gradlew jacocoTestReport"
          publishHTML (target: [
               reportDir: 'build/reports/jacoco/test/html',
               reportFiles: 'index.html',
               reportName: "JaCoCo Report"
          ])
          sh "./gradlew jacocoTestCoverageVerification"
      }
    }
  }
} 

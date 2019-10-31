pipeline {
  agent any
  stages {
    stage("Lockit") {
    lock('lock1') {
    }
    stage("Checkout") {
      steps {
        git url: 'https://github.com/lintmint/calculator.git'
      }
   }
      //
      stage ("wait_prior_starting_smoke_testing") {
    def time = 30
    echo "Waiting 30 seconds for deployment"
    sleep time.toInteger() // seconds
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
/*
          publishHTML (target: [
               reportDir: 'build/reports/jacoco/test/html',
               reportFiles: 'index.html',
               reportName: "JaCoCo Report"
          ])
*/
//          sh "./gradlew jacocoTestCoverageVerification"
     } // end env lock
      }
    }
  }
} 

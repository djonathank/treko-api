pipeline {
  agent {
    docker {
      sh "chmod"
      image "node:8-alpine"
      args "--network=skynet"
    }
  }
  stages {
    stage("Build") {
      steps {
        sh "chmod +x ./scripts/dropdb.sh"
        sh "apk add --no-cache mongodb"
        sh "npm install"
      }
    }
   stage("Test") {
      steps {
        sh "npm run test:ci"
      }
     post {
       always {
         junit "log/*.xml"
       }
     }
    }
  }
}

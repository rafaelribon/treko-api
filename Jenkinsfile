pipeline {
  agent{
    docker{
      image "node:8-alpine"
      args "--network=skynet"
    }
  }
  stages{
    stage("Build"){
      steps{
       sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/main' >> /etc/apk/repositories"
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/community' >> /etc/apk/repositories"
        sh "apk update"
        sh "apk add mongodb=4.0.5-r0"
        sh "chmod +x ./scripts/dropdb.sh"
        sh "npm install"
      }
    }
    stage("Test"){
      steps{
        sh "npm run test:ci"
      }
    }
  }
}

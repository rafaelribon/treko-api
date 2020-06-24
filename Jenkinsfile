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
          sh "apk add --no-cache --repository='http://dl-cdn.alpinelinux.org/alpine/v3.9/main' >> /etc/apk/repositories"
          sh "apk add --no-cache --repository='http://dl-cdn.alpinelinux.org/alpine/v3.9/community' >> /etc/apk/repositories"
          sh "apk add --no-cache mongodb"
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

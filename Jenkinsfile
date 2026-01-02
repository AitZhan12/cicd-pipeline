pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        git(url: 'https://github.com/AitZhan12/cicd-pipeline.git', branch: 'test', changelog: true)
      }
    }

    stage('Shell script') {
      steps {
        sh 'cd scripts && chmod +x build.sh && ./build.sh'
      }
    }

    stage('Test shell script') {
      steps {
        sh 'cd scripts && chmod +x test.sh && ./test.sh'
      }
    }

    stage('Build docker image') {
      steps {
        sh '''docker build -t aitzhanic/ci-cd-demo:${BUILD_NUMBER} .
docker tag aitzhanic/ci-cd-demo:${BUILD_NUMBER} aitzhanic/ci-cd-demo:latest'''
      }
    }

    stage('Build docker image push') {
      steps {
        sh '''docker login -u ${DOCKER_USER} -p ${DOCKER_PASS}
docker push aitzhanic/ci-cd-demo:${BUILD_NUMBER}
docker push aitzhanic/ci-cd-demo:latest
docker logout'''
      }
    }

  }
}
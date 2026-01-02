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

  }
}
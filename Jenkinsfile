pipeline {
  agent any
  stages {
    stage(' git clone or git pull ') {
      steps {
        git url: 'https://github.com/minnnmin/test.git', branch: 'main'
      }
    }

    stage(' docker image build and push to p-registry ') {
      steps {
        sh '''
	docker build -t 192.168.8.100:5000/web:blue2 .
	docker push 192.168.8.100:5000/web:blue2
	'''
      }
    }

    stage(' update deployment image ') {
      sh '''
      kubectl set image deployment/web-blue blue=192.168.8.100:5000/web:blue2
      '''
    }
  }
}

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
	docker build -t 192.168.8.100:5000/web:green .
	docker push 192.168.8.100:5000/web:green
	'''
      }
    }

    stage(' create deployment, svc ') {
      steps {
        sh '''
	kubectl apply -f green.yaml
	'''
      }
    }
  }
}



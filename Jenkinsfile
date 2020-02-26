pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/adil1806/Kalyanam-UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			ng build --base-href=/matrimony/                      
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/dist/matrimony /opt/apache-tomcat-9.0.30/webapps
             curl -u admin:admin http://3.6.206.161:8888/manager/reload?path=/build 
             '''
		}
	}
}
}

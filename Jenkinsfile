node('linux') {   
	git url: 'https://github.com/ajulayfi/java-project.git'
	stage('Unit Tests') {
    		sh 'ant'
		sh 'ant -f test.xml -v' 
		junit 'reports/result.xml'
	}
	stage('Build') {
		sh 'ant'
		sh 'ant -f build.xml -v' 
	}
	stage('Deploy') {
		sh 'aws s3 cp dist/rectangle-${BUILD_NUMBER}.jar s3://itidal-assignment-10/' 
	}

}

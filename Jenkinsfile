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
		sh 'curl https://github.com/ajulayfi/java-project/blob/master/Jenkinsfile https://s3.amazonaws.com/alju3541-assignment-4'	
	}

}

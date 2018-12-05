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
		sh 'aws s3 cp https://github.com/eyad-ust/java-project/blob/master/lib/junit-4.10.jar s3://alju3541-assignment-4/'	
	}

}

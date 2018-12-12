properties([pipelineTriggers([githubPush()])])

node('linux') {
    stage('Unit Tests') {
      git 'https://github.com/ajulayfi/java-project.git'
      sh 'ant -f test.xml -v'
      junit 'reports/result.xml'
    }
    stage('Build') {
      sh 'ant -f build.xml -v'
    }
    stage('Deploy'){
        sh 'aws s3 cp /workspace/docker-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://bucket-abdul2018'
        sh 'aws s3 cp s3://bucket-abdul2018/classweb.html workspace/docker-pipeline/dist'
    }
    
}

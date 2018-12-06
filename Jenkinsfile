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
        sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://bucket-abdul2018'
    }
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '7cf49247-b83a-4f43-9cb9-957fd6ba1be5', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    // some block
        sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
        }
}

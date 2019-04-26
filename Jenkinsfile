node('linux'){
    stage('Unit Tests'){
        git 'https://github.com/jun08561/java-project.git'
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        sh 'ant'
        sh 'ant -f build.xml -v'
    }
    
    stage('Deploy'){ 
      sh "aws s3 cp $WORKSPACE/dist/*.jar s3://jun08561/rectangle-${BUILD_NUMBER}.jar" 
 } 
    
      stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '37b7f539-bc32-4133-9e62-9e6563ece743', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    // some block
        sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1 '
}
}

node('master') 
{
    stage('ContinuousDevelopment_loan') 
    {
    git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild_loan') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeploy_loan')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipline/webapp/target/webapp.war ubuntu@172.31.46.231:/var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContinuousTesting_loan')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipline/testing.jar'
    }
    stage('ContinuousDelivery_loan')
    {
        input 'Waiting for approval form the delivery manager'
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipline/webapp/target/webapp.war ubuntu@172.31.33.149:/var/lib/tomcat8/webapps/testenv.war'
    }
    
}

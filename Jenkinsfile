node('master') 
{
    stage('ContinuousDevelopment') 
    {
    git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeploy')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipline/webapp/target/webapp.war ubuntu@172.31.41.245:/var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        input 'Waiting for approval form the delivery manager'
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipline/webapp/target/webapp.war ubuntu@172.31.41.245:/var/lib/tomcat8/webapps/testenv.war'
    }
    
}

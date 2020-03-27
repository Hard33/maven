node ('master')
{
    stage ('Continuous Download')
    {
        git 'https://github.com/Hard33/maven.git'
    }
    stage ('Continuous Build')
    {
        sh label: '', script: 'mvn package'
    }
    stage ('Continuous Deployment')
    {
        sh label: '', script: 'scp -pr /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war root@172.31.91.95:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage ('Continuous Testing')
    {
        git 'https://github.com/Hard33/FunctionalTesting.git'
        sh label: '', script: 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage ('Continuous Delivery')
    {
        sh label: '', script: 'scp -pr /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war root@172.31.94.78:/var/lib/tomcat8/webapps/prodapp.war'
    }
}

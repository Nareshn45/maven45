pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/Nareshn45/maven45.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.25.210:/var/lib/tomcat9/webapps/testapp.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                input message: 'Waiting for approval from the DM!', submitter: 'chiranjeevi'
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                input message: 'Waiting for approval from the DM!', submitter: 'chiranjeevi'
                sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.25.236:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
    }
}

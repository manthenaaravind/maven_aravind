pipeline
{
    agent
    {
        label 'master'
    }
    stages
    {
        stage('continuiusdownload')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/selenium-saikrishna/maven.git'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Declarative pipeline is failed', cc: '', from: '', replyTo: '', subject: 'Declarative pipeline is failed', to: 'aravind.m458@gmail.com'
                    }
                }
                
            }
        }
        stage('continuousbuild')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Declarative pipeline is failed', cc: '', from: '', replyTo: '', subject: 'Declarative pipeline is failed', to: 'aravind.m458@gmail.com'
                    }
                }
                
            }
        }
        stage('continuousdeploy')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /root/.jenkins/workspace/mydeclarativepipeline/webapp/target/webapp.war ubuntu@172.31.25.147:/var/lib/tomcat8/webapps/qaqa.war'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Declarative pipeline is failed', cc: '', from: '', replyTo: '', subject: 'Declarative pipeline is failed', to: 'aravind.m458@gmail.com'
                    }
                }
            }
        }
        stage('continuoustesting')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
                        sh 'java -jar /root/.jenkins/workspace/mydeclarativepipeline/testing.jar'
                        
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Declarative pipeline is failed', cc: '', from: '', replyTo: '', subject: 'Declarative pipeline is failed', to: 'aravind.m458@gmail.com'
                    }
                }
            }
        }
        stage('continuousdeliver')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /root/.jenkins/workspace/mydeclarativepipeline/webapp/target/webapp.war ubuntu@172.31.27.239:/var/lib/tomcat8/webapps/prodprod.war'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Declarative pipeline is failed', cc: '', from: '', replyTo: '', subject: 'Declarative pipeline is failed', to: 'aravind.m458@gmail.com'
                    }
                }
                
            }
        }
    }
}

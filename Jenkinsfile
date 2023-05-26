pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps{
                
            
            deploy adapters: [tomcat9(credentialsId: '7dc873b7-be97-4a10-9ecc-3fa33b431c75', path: '', url: 'http://172.31.5.100:8080')], contextPath: 'test1', war: '**/*.war'
        }
        }
        stage('ContTesting')
        {
         steps
         {
             
         
            git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        
             sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
         }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '7dc873b7-be97-4a10-9ecc-3fa33b431c75', path: '', url: 'http://172.31.5.189:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
        
        
        
        
    }
}

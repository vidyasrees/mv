pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                'git https://github.com/vidyasrees/mv.git'
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
                deploy adapters: [tomcat9(credentialsId: '61ffc965-29e1-4559-8c82-f5feeef73375', path: '', url: 'http://172.31.22.70:8080')], contextPath: 'Test1', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
                
            }
        }
         stage('ContinuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '61ffc965-29e1-4559-8c82-f5feeef73375', path: '', url: 'http://172.31.29.7:8080')], contextPath: 'Prod1', war: '**/*.war'
            }
        }
        
        
        
    }
}

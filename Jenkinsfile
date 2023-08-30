pipeline
{
    agent any 
    stages
    {
        stage('contdownloads')
        {
            steps
            {
              git 'https://github.com/TheKarnaa/mymaven.git'
            }
        }
         stage('contbuild')
        {
            steps
            {
              sh 'mvn package'
            }
        }
         stage('contdeployment')
        {
            steps
            {
              deploy adapters: [tomcat9(credentialsId: 'e943ebe5-735d-4de6-bb06-ea63ad1d83a4', path: '', url: 'http://172.31.27.166:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
         stage('conttesting')
        {
            steps
            {
              git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
              sh 'java -jar  /home/ubuntu/.jenkins/workspace/DeclaretivePipeline/testing.jar'
            }
        }
        stage('contdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '94be728b-a36a-4fd3-a51a-1ec63b80cae1', path: '', url: 'http://172.31.26.183:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}

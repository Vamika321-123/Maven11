node('built-in')
{
 stage('Continuous Download') 
  {
    git 'https://github.com/IntelliqDevops/maven.git'
  }
     stage('Continuos Build')
        {
            sh 'mvn package'
        }
          stage('Continuous Deployment')
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '2e5986f7-49df-4694-8979-8164566d13a1', path: '', url: 'http://54.79.149.20:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        stage('Continuous Testing')
              {  
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
             }
                stage('Continuos Delivery')
                    {
                        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '2e5986f7-49df-4694-8979-8164566d13a1', path: '', url: 'http://3.26.62.132:8080')], contextPath: 'prodapp', war: '**/*.war'
                    }
}



node('built-in')
{
    stage('Continous Download')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('Continuos Build')
    {
        sh 'mvn package'
    }
    stage('Continous Deployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'b2906f26-d037-4434-8077-f5c7e0449e2c', path: '', url: 'http://172.31.45.70:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('Continous Testing')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        
        sh 'java -jar /var/lib/jenkins/workspace/Pipeline1/testing.jar'
    }
    stage('Continous Delivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'b2906f26-d037-4434-8077-f5c7e0449e2c', path: '', url: 'http://172.31.43.209:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}

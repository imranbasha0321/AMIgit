pipeline {
    agent any
    stages{
        stage('continuousdownload')
        {
         steps{
             
           script {
                git 'https://github.com/imranbasha0321/AMIgit.git'
            }
            }
        }
        stage('contbuild') {
            steps {
                script {
                    sh 'mvn package'
                }
            }
        }
        stage('contdeploy')
        {
            steps 
            {
              script 
              {
                  deploy adapters: [tomcat9(credentialsId: '16d81036-abc4-4d98-9299-1e58abad8ec9', path: '', url: 'http://54.153.108.135:8080')], contextPath: 'mytestapp', war: '**/*.war'
              }
            }
        }
        stage('conttest') 
        {
            steps 
            {
                script 
                {
                    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                    sh 'java -jar /var/lib/jenkins/workspace/descriptivepipeline/testing.jar'
                }
            }
        }
        stage('contdelivery')
        {
            steps {
                script 
                {
                    deploy adapters: [tomcat9(credentialsId: '16d81036-abc4-4d98-9299-1e58abad8ec9', path: '', url: 'http://54.193.178.151:8080')], contextPath: 'myprodapp', war: '**/*.war'
                }
                
            }
        }
    }
}

pipeline{
    agent{
        label "aws_kishor"
    }
    tools{
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn --version"
                sh 'mvn test'
            }  
        }
        stage("SonarQube"){
            steps{
             
                sh 'mvn sonar:sonar'
            }  
        }
        stage("Build"){
            steps{
                sh 'mvn package'
            }  
        }
        stage("Deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '2f37f574-c632-4fd2-96bf-1e17f0f083f5', path: '', url: 'http://54.152.32.154:8080')], contextPath: 'tomcatproject', war: '**/*.war'
            }  
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}

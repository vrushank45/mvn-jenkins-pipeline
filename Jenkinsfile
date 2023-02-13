pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn test"
            }
        }
        stage("Build"){
            steps{
                sh "mvn package"
            }
        }
        stage("Deploy on Test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'Tomcat9details', path: '', url: 'http://192.168.187.128:3030/')], contextPath: '/app2', war: '**/*war'
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

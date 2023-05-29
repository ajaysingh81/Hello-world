pipeline{
    agent any
    tools{
        maven "maven-3.9.2"
    }
 
    stages{
        stage("Fetch Code"){
            steps{
                git 'https://github.com/ajaysingh81/Hello-world.git'
            }
        }
        
        stage("Build Code"){
            steps{
                sh 'mvn clean install'
            }
        }
        
        stage("Test Code"){
            steps{
                sh 'mvn test'
            }
        }
        
        stage("Deploy"){
            steps{
                sshagent(['pem']) {
                    sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ubuntu@3.108.252.246:/opt/apache-tomcat-10.1.9/webapps'
                }
            }
        }
    
    }
}

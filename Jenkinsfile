pipeline{
    
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
    
    agent any
    
    stages{
        
        stage('Clone the repo')
        {
            steps{
                git 'https://github.com/HariKunjeti/samplejavaapp.git'
            }
        }
        stage('Compile the code')
        {
            steps{
                sh 'mvn compile'
            }
        }
        stage('Code Review')
        {
            steps{
                sh 'mvn pmd:pmd'
            }
        }
      
        stage('Unit Testing')
        {
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Package')
        {
            steps{
            sh 'mvn package'
            }
        }
    }
}

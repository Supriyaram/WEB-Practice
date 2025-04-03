pipeline {
    agent any
   
    stages {
        stage('Create web directory')
        {
            input {
              message 'Enter the data'
              parameters {
                    string(name:'AUTHOR', defaultValue: 'Sergio', description: 'Author of the web application deployment ')
                    string(name:'ENVIRONMENT', defaultValue: 'Development',description: 'Environment to deploy')
                 }
            }
            steps{
                echo "The responsible of this project is ${AUTHOR} and and will be deployed in ${ENVIRONMENT}"
                //Fisrt, drop the directory if exists
                sh 'rm -rf /var/jenkins_home/web'
                //Create the directory
                sh 'mkdir /var/jenkins_home/web'
                
            }
        }
        
        stage('Copy the web application to the container directory') {
            steps {
                echo 'Copying web application...'             
                sh 'cp -r web/* /var/jenkins_home/web'
            }
        }
        stage('Checking the app') {
            steps {
                echo 'Testing the web app'
                sh 'wget http://localhost:9000'
            }
        }       
    }
}

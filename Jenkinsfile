pipeline {
    agent any

    stages {
        stage('Code Fetch') {
            steps {
                echo 'code fetch from github.'
                git url:'https://github.com/dineshkshrestha/html5-boilerplate.git',branch:'main'
            }
        }
              
        stage('stop docker') {
            steps {
                echo 'code build with docker.'
                sh 'docker stop $(docker ps -q) && docker system prune -a '
            }
        }
        stage('Build') {
            steps {
                echo 'code build with docker.'
                sh 'docker build -t html-website .'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'code deployed in container.'
                sh ' docker run -d -p 80:80 html-website'
            }
        }
    }
}

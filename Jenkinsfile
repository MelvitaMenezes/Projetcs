pipeline{
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main',
                        credentialsId: 'MelvitaMenezes',
                        url: 'https://github.com/MelvitaMenezes/Projetcs.git'
                }
            }
        }
        stage('build Docker Image') {
            steps {
                script {
                    sh 'docker build -t static-website .'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh ''' docker stop static-website || true
                            docker rm static-website || true
                            docker run -d --name static-website -p 9000:80 static-website '''
                }
            }
        }
    }
}
    

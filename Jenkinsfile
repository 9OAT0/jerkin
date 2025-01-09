pipeline {
    agent any
    stages {
        stage('Copy file to Docker server') {
            steps {
                sh '''
                scp -i ~/.ssh/id_rsa -r /var/lib/jenkins/workspace/team12_spering/* root@13.60.223.206:~/team12_spering
                '''
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '''
                ssh -i ~/.ssh/id_rsa root@13.60.223.206 "cd ~/team12_spering && docker build -t team12_image ."
                '''
            }
        }
        stage('Create Docker Container') {
            steps {
                sh '''
                ssh -i ~/.ssh/id_rsa root@13.60.223.206 "docker run -d --name team12_containe -p 80:80 team12_image"
                '''
            }
        }
    }
}

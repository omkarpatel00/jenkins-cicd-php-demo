pipeline {
    agent any
    
    stages {
        stage('SSH Connection') {
            steps {
                script {
                    def sshCredentialId = 'your_ssh_credential_id'
                    def ec2PublicIP = 'your_ec2_public_ip'
                    
                    sh "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'mkdir op-new'"
                }
            }
        }
        
        stage('Git Clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'your_git_credentials_id', url: 'https://github.com/yourusername/your-repo.git']]])
            }
        }
        
        stage('Deploy to Host') {
            steps {
                script {
                    def sshCredentialId = 'your_ssh_credential_id'
                    def ec2PublicIP = 'your_ec2_public_ip'
                    
                    sh "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'scp -rp pipeline {
    agent any
    
    stages {
        stage('SSH Connection') {
            steps {
                script {
                    def sshCredentialId = 'your_ssh_credential_id'
                    def ec2PublicIP = 'your_ec2_public_ip'
                    
                    sh "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'mkdir test-dir'"
                }
            }
        }
        
        stage('Git Clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'your_git_credentials_id', url: 'https://github.com/yourusername/your-repo.git']]])
            }
        }
        
        stage('Deploy to Host') {
            steps {
                script {
                    def sshCredentialId = 'your_ssh_credential_id'
                    def ec2PublicIP = 'your_ec2_public_ip'
                    
                    sh "ssh -i /home/ubuntu/.ssh -o StrictHostKeyChecking=no ubuntu@${ec2PublicIP} 'scp -rp /var/lib/jenkins/workspace/your-pipeline-job-name/* ubuntu@${ec2PublicIP}:/var/www/html/'"
                }
            }
        }
    }
}
 ubuntu@${ec2PublicIP}:/var/www/html/'"
                }
            }
        }
    }
}

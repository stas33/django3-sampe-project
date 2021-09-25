pipeline {
    agent any


    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/stas33/django3-sampe-project.git'

                
            }
        }
        
        stage('Test') {
            steps {
                sh '''
                    python3 -m venv venv
                    source venv/bin/activate
                    pip install -r requirements.txt
                    cd myproject
                    cp myproject/.env.example myproject/.env
                    ./manage.py test'''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                echo "Test Deploy"
                '''
                /* sshagent (credentials: ['ssh-deployment-1']) {

                sh '''
                    pwd
                    echo $WORKSPACE
                    ansible-playbook -i ~/workspace/ansible-project/hosts.yml -l deploymentservers ~/workspace/ansible-project/playbooks/check.yml
                    ''' */

            }
        }
    }
}

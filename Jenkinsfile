pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'sudo apt-get install python3-pip -y'
                sh 'pip3 install django'
                sh 'pip3 install gunicorn'
            }
        }
        stage('Build') {
            steps {
                sh('''
                    pip3 install --user --upgrade setuptools wheel
                    python3 helloworld/setup.py sdist bdist_wheel

            ''')
            }
        }
        stage('Run') {
            steps {
                sh ('''
                    cd /home/ubuntu/workspace/test-pipeline/helloworld
                    gunicorn helloworld_project.wsgi
                ''')
            }
        }
    }
}


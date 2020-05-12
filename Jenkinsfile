pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'sudo apt-get install python3-pip -y'
                sh 'pip3 install django'
                sh 'sudo apt-get install gunicorn3 -y'
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
                    gunicorn3 - 0.0.0.0:8000 helloworld_project.wsgi
                ''')
            }
        }
    }
}


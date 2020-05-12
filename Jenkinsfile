pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh('''
                    apt-get install python3-pip -y
                    pip3 install django
                    sudo apt-get install gunicorn3 -y
                    sudo apt-get install daemonize -y
                ''')
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
                    daemonize -E BUILD_ID=dontKillMe gunicorn3 -b 0.0.0.0:8000 helloworld_project.wsgi --daemon
                ''')
            }
        }
    }
}


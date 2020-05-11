pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'sudo apt-get install python3-pip -y'
                sh 'pip3 install django'
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
                    python3 helloworld/manage.py runserver 0.0.0.0:8000 &
                    sleep 120
                ''')
            }
        }
    }
}


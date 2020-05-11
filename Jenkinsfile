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
                    python3 setup.py sdist bdist_wheel

            ''')
            }
        }
        stage('Run') {
            steps {
                sh ('''
                    python3 manage.py runserver
                ''')
            }
        }
    }
}


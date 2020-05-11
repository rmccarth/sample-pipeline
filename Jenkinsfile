pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'sudo apt-get install python-pip -y'
                sh 'pip install django'
            }
        }
        stage('Build') {
            steps {
                sh('''
                    python3 -m pip install --user --upgrade setuptools wheel
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


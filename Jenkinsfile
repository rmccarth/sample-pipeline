pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'pip install django'
                sh 'python3 -c 'print "insert test here"'
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
            sh ('''
                python3 manage.py runserver
            ''')
        }
    }
}



pipeline {
    agent { label 'jenkins-slave-python' }
    stages {
        stage('build') {
            steps {
              sh 'python3 -m pip install --user --upgrade setuptools wheel'
              sh 'python3 setup.py sdist bdist_wheel'
            }
        }
        stage('Uploading') {
            steps {
              script {
                googleStorageUpload bucket: 'gs://for-python-task/artifacts', credentialsId: 'jenkins-my', pattern: 'dist/*'
              }
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('AWS STS') {
            steps {
                echo 'AWS STS'
                sh 'aws sts get-caller-identity'
            }
        }
        stage('AWS s3 list') {
            steps {
                echo 'AWS STS'
                sh 'aws s3 ls'
            }
        }
        stage('GIT git clone') {
            steps {
                echo 'Git clone'
                sh 'rm -rf upload-csv-dynamo-automation/'
                sh 'git clone https://github.com/rdespitia70/upload-csv-dynamo-automation.git'
                sh 'ls -lrt upload-csv-dynamo-automation/'
            }
        }
        stage('Upload to s3') {
            steps {
                sh 'aws s3 cp upload-csv-dynamo-automation s3://rdem1-csv-loader-bucket --recursive'
            }
        }
    }
}

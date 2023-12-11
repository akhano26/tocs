pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/akhano26/tocs.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'MyUbuntuServer',
                            transfers: [sshTransfer(sourceFiles: '**/*', remoteDirectory: '/myapp')],
                            execCommand: 'python /myapp/test.py'
                        )
                    ]
                )
            }
        }
    }
}

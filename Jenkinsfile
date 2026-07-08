pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment { 
        COURSE = 'Jenkins'
    }

    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Building... scripted shell command"
                        echo $COURSE
                        env
                    """
                }
                echo "Building..."
            }
        }
        stage('Test') {
            steps {
                echo "Testing..."
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying..."
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            cleanWs()
        }
        success{
            echo "Build and Test completed successfully!"
        }
        failure{
            echo "Build or Test failed!"
        }
        aborted{
            echo "Build or Test aborted!"
        }
    }
}
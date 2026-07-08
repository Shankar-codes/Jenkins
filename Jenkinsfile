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
        timeout(time: 1, unit: 'SECONDS') 
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
                script {
                    sh """
                        echo "Testing... scripted shell command"
                        echo $COURSE
                        env
                    """
                }
                echo "Testing..."
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh """
                        echo "Deploying... scripted shell command"
                        echo $COURSE
                        env
                    """
                }
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
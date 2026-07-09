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

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
// this is build section. added comment for just webhook checking
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
                echo "Just checking poll SCM webhook"
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
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
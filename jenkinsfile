pipeline {
    agent none
    stages {
        stage("checkout the coode") {
            agent {
                label "slave"
            }
            steps {
                echo "Checkout the code form github"
                git credentialsId: 'github_key', url: 'https://github.com/panda8899repo/login-app.git'
            }
        }
        stage("clean and test project") {
            agent {
                label "slave"
            }
            steps {
                echo "cleaning and testing project"
                sh "mvn clean test "
            }
        }
    }
}

pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/ManojKumar8244/java-ci-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    sh '''
                    mvn sonar:sonar \
                    -Dsonar.projectKey=java-ci-demo \
                    -Dsonar.organization=your-org-name
                    '''
                }
            }
        }
    }
}

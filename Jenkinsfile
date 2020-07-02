pipeline {
    agent {
        docker{
            image 'ruby'
        }
    }
    stages{
        stage ('Build'){
            steps{
                echo 'Bulding or Develop dependence test'
                sh 'bundle install'
            }
        }
        stage ('Test'){
            steps{
                echo 'Running regressition test'
                sh 'duncle exec cucumber -p ci'
            }
        }
        stage ('UAT'){
            steps {
                echo 'Wait for user Acceptance'
                input(message:'Go to production?', ok:'Yes')
            }
        }
        stage('Prod'){
        steps {
            echo 'WebApp is Ready :)'
            }
        }
        
    }
}
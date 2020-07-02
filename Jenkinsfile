pipeline {
    agent {
        docker{
            image 'qaninja/rubywd'
        }
    }
    stages{
        stage ('Build'){
            steps{
                echo 'Bulding or Develop dependence test'
                sh 'rm -f Gemfile.lock'
                sh 'bundle install'
            }
        }
        stage ('Test'){
            steps{
                echo 'Running regressition test'
                sh 'bundle exec cucumber -p ci'
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
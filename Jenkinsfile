pipeline{
    agent none
    stages{
        stage('Gitscm'){
            agent {
                label 'mydockerarth'
            }
            steps{
                
            echo "maven code downloaing ..."
            git 'https://github.com/deepaksharma2007/simple-java-maven-app.git'
            stash includes: "*" , name: 'mygit'
            sh 'ls -l'
            sh 'pwd'
            }
                
        }
        stage('Build'){
            agent{
                label 'mydockerarth'
            }
            steps{
                unstash 'mygit'
                sh 'mvn package'
                sh 'ls -l'
                stash includes: '**/target/**/' , name: 'mave' 
            }
        }
        stage('run'){
            agent {
                label 'mydockerarth'
            }
            steps{
                unstash 'mave'
                echo "This is the fix -123 feature branch"
            
                
            }
        }
    }
}

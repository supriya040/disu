pipeline {
    agent any
    
    stages {
        stage ('SCM checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/meets-patel/disu2.git'
            }
            
        }
        
        stage ('docker image build') {
            steps {
                sh '/usr/bin/docker image build -t meetpatel2223/disu .'
            }
        }
        
        stage ('Docker Login') {
            steps {
                sh 'echo dckr_pat_BywiI2AmHoGCgefxffyJfSJj1NA | /usr/bin/docker login -u meetpatel2223 --password-stdin'
            }
        }
        
        stage ('docker image Push') {
            steps {
                sh '/usr/bin/docker image push meetpatel2223/disu'
            }
        }
        
        stage ('remove existing service') {
            steps {
                sh '/usr/bin/docker service rm disu'
            }
        }
        
        stage ('create docker service') {
            steps {
                sh '/usr/bin/docker service create --name disu -p 4010:4010 meetpatel2223/disu'
            }
        }
        
    }
}

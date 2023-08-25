pipeline {
    agent any
    
    stages {
        stage ('SCM checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/supriya040/disu.git'
            }

        }
        
        stage ('docker image build') {
            steps {
                sh '/usr/bin/docker image build -t supriya040/disu .'
            }
        }
        
        stage ('Docker Login') {
            steps {
                sh 'echo dckr_pat_dfAoP_83SlNhGyz2NoRX4v9B8Pc | /usr/bin/docker login -u supriya040 --password-stdin'
            }
        }
        
        stage ('docker image Push') {
            steps {
                sh '/usr/bin/docker image push supriya040/disu'
            }
        }
        
        stage ('remove existing service') {
            steps {
                sh '/usr/bin/docker service rm disu'
            }
        }
        
        stage ('create docker service') {
            steps {
                sh '/usr/bin/docker service create --name disu -p 80:4010 supriya040/disu'
            }
        }
        
    }
}

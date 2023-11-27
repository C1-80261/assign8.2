pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80261/assign8.2.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_p3jYrxxLOa_ZepweHHBzo_zTS8A | /usr/bin/docker login -u rutvijapatil --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t rutvijapatil/web1 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push rutvijapatil/web1'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm service1'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name service1 -p 9091:80 --replicas 5 rutvijapatil/web1'
            }
        }
    }
}

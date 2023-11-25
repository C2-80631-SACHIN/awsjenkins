pipeline {
    agent any
    stages {
        stage ('build docker image') {
            steps {
                sh '/usr/bin/docker image build -t sc4458/jenkinsdemo .'
            }
        }

        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_dvWd9FEukz-2ikcZfuyKDbDfmXo | /usr/bin/docker login -u sc4458 --password-stdin'
            }
        }
        stage ('push docker image') {
            steps {
                sh '/usr/bin/docker image push sc4458/jenkinsdemo'
            }
        }
        stage ('reload docker service') {
            steps {
                sh '/usr/bin/docker service update --image sc4458/jenkinsdemo --force myservice'
            }
        }

    }
}

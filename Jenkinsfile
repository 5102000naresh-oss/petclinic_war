node {

    def email = '5102000naresh@gmail.com'

    try {

        stage('git') {

            git branch: 'main',
            url: 'https://github.com/5102000naresh-oss/petclinic_war.git'
        }

        stage('build') {

            sh 'mvn clean package'
        }

        stage('tomcat') {

            sshagent(['tc']) {

                sh '''
                scp -o StrictHostKeyChecking=no \
                target/petclinic.war \
                ubuntu@13.126.240.241:/home/ubuntu/apache-tomcat-11.0.22/webapps/
                '''
            }
        }

        mail to: email,
        subject: 'Build Report',
        body: 'Build Success'

    }

    catch(Exception e) {

        mail to: email,
        subject: 'Build Report',
        body: 'Build Failure'

        throw e
    }
}

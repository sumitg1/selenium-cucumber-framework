pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    sh 'mvn test -Dcucumber.options="--tags @search" -Dwebdriver.driver=firefox'
                }
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    bat 'mvn test -Dcucumber.options="--tags @search" -Dwebdriver.driver=firefox'
                }
            }
        }
    }
}

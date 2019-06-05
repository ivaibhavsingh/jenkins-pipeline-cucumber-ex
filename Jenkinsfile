pipeline{

    agent any

    stages {

        stage ('Compile Stage')
        {

            steps {

                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn clean install'
                    echo 'failing at step 1'

                }
                

            }
        }
    stage ('Test Stage') {

            steps {

                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn test'
                echo 'failing at step 2'
                }

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'
                   echo 'failing at step 3'

            }

        }

    }

}

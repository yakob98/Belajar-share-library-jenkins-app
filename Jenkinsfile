@Library("belajar-jenkins-shared-library@main") _

import programyakob.jenkins.Output;

pipeline{
    agent any
    stages{
        stage("Import Hello"){
            steps{
                script{
                    Output.hello(this, "Groovy")
                }
            }
        }

        stage("Vars Hello"){
            steps{
                script{
                    hello.world()
                }
            }
        }
    }
}
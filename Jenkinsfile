// Pipeline untuk menjalankan task di agent mana pun yang sedang kosong
// pipeline{
//     agent any

//     stages{
//         stage("Hello"){
//             steps{
//                 echo "Hello World"
//             }
//         }
//     }
// }

// Menargetkan agent dengan menggunakan label untuk menjalankan task
pipeline{
    agent any
    environment{
        AUTHOR = "Yacob Hae"
        EMAIL = "yacobhae@gmail.com"
    }

    parameters{
        string(name: "NAME", defaultValue: "Guest", description: "Siapa Nama Anda ?")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "Siapa Anda ?")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "Butuh di Deploy ?")
        choice(name: "SOCIAL_MEDIA", choices: ['Instagram', 'Facebook', 'Telegram'], description: "Pilih Sosial Media yang mana?")
        password(name: "SECRET", defaultValue: "", description: "Encrypt Key")
    }

    triggers{
        // cron("*/2 * * * *")
        pollSCM("*/2 * * * *")
        // upstream(upstreamPProjects : 'job1,job2', threshold: hudson.model.Result.SUCCESS)
    }

    options{
        disableConcurrentBuilds()
        // timeout(time: 10, unit: 'SECONDS')
        timeout(time: 10, unit: 'MINUTES')
    }
//    agent any //    {
        // node{
        //     label "java && jenkins"
        // }
//    }


// menambahkan stage
    stages{

        stage("Parameters"){

            // agent{
            //     node{
            //         label "java && jenkins"
            //     }
            // }

            steps{
                echo("Hello ${params.NAME} !")
                echo("Your Descriptions ${params.DESCRIPTION} !")
                echo("Your Social Media is ${params.SOCIAL_MEDIA} user")
                echo("Need to deploy ${params.DEPLOY} to Deploy")
                echo("Your Secret is ${params.SECRET}")
                
            }
        }



        stage("Prepare"){
            environment{
            APP = credentials("yakob_test")
            }
            // agent{
            //     node{
            //         label "java && jenkins"
            //     }
            // }
            steps{
                echo("Author : ${AUTHOR}")
                echo("Email : ${EMAIL}")
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Branch Name : ${env.BRANCH_NAME}")
                echo("App User : ${APP_USR}")
                // echo("App Password : ${APP_PSW}")
                // sh("echo 'App Password : ${APP_PSW}' > 'secret_pass.txt'")
                sh('echo "App Password : $APP_PSW" > "Rahasia.txt" ')
            }
        }


        stage("Build"){
            // agent{
            //     node{
            //         label "java && jenkins"
            //     }
            // }
            steps{
                script{
                    for (int i = 0; i < 10; i++){
                    echo("Script ${i}")
                    }
                }
                echo "Start Build"
                sh("sh mvnw clean compile test-compile")
                echo "Finish Build 3"
                sleep(5)
            }
        }

        stage("Test"){
            // agent{
            //     node{
            //         label "java && jenkins"
            //     }
            // }
            steps{
                script{
                    def data = [
                        "firstName" : "yakob",
                        "lastName" : "hae"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
                echo "Start test "
                sh("sh mvnw test ")
                echo "Finish test"
                // sh('cat /etc/passwd')
                sleep(5)
            }
        }

        stage("Deploy"){
            input{
                message "Boleh di Deploy ?"
                ok "Tentu Saja"
                submitter "yacob"
                parameters{
                    choice(name: "TARGET_ENV", choices: ['DEV', 'QA', 'PRD'], description: "Pilih Sosial Media yang mana?")
                }
            }
            // agent{
            //     node{
            //         label "java && jenkins"
            //     }
            // }
            steps{
                // echo "Start Deploy 1"
                // //sh("sh mvnw deploy")
                // echo "Finish Deploy 2"
                echo "Deploy to ${TARGET_ENV}"
                sleep(5)
            }
        } 
    }

    post{
        always{
            echo "Kita akan selalu bertemu"
        }
        success{
            echo "Yes Berhasil Run"
        }
        failure{
            echo "Yahhh Gagal :("
        }
        cleanup{
            echo "Apapun yang terjadi tetap harus di bersihkan"
        }
    }
}
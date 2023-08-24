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
//    agent any //    {
        // node{
        //     label "java && jenkins"
        // }
//    }


// menambahkan stage
    stages{
        stage("Build"){
            agent{
                node{
                    label "java && jenkins"
                }
            }
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
            agent{
                node{
                    label "java && jenkins"
                }
            }
            steps{
                script{
                    def data = [
                        "firstName" : "yakob",
                        "lastName" : "hae"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
                // echo "Start test "
                // sh("sh mvnw test ")
                // echo "Finish test"
                // sh('cat /etc/passwd')
                sleep(5)
            }
        }

        stage("Deploy"){
            agent{
                node{
                    label "java && jenkins"
                }
            }
            steps{
                echo "Start Deploy 1"
                //sh("sh mvnw deploy")
                echo "Finish Deploy 2"
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
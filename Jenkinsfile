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
    agent any //    {
        // node{
        //     label "java && jenkins"
        // }
//    }
// menambahkan stage
    stages{
        stage("Build"){
            steps{
                echo "Start Build"
                sh('./mvnw clean compile test-compile')
                echo "Finish Build 3"
                sleep(5)
            }
        }

        stage("Test"){
            steps{
                echo "Hello Test"
                echo "Hello Test 2"
                echo "Hello Test 3"
                sh('cat /etc/passwd')
                sleep(5)
            }
        }

        stage("Deploy"){
            steps{
                echo "Hello Deploy"
                echo "Hello Deploy 2"
                echo "Hello Deploy 3"
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
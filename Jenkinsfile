node("slave_windows_root"){

    stage("Git Checkout"){
        catchError(buildResult:"ABC"){
        gitFunctions.gitClone(url="https://github.com/ricky001/gitlab4j-api.git")
        bat "ls"
        }
    }

    parallel(

        "Windows Node":{
            stage("Printing Message"){
                echo "Hello World from Master"
                commonFunctions.createFile("abc.txt","Hello how are you")
                commonFunctions.createFile("123.txt","My Name is Somya Chawla")
                commonFunctions.createFile("more.txt","My Name is Divya Chawla")
                bat "dir"
                stash name:'file',includes:'*.txt',excludes:'abc.txt'
            }
        },
        "Linux Node":{
            node("windows_2"){
                stage("Get OS Name"){
                    def osName=commonFunctions.getOS()
                    echo "${osName}"
                    sleep(10)
                    unstash 'file'
                }
            }

        }
    )
    


}

node("slave_windows_root"){

    stage("Git Checkout"){
        catchError(buildResult:"FAILURE",stageResult:"UNSTABLE"){
        gitFunctions.gitClone(url="https://github.com/ricky001/gitlab4j-api.git")
        bat "dir"
        }
    }

    parallel(

        "Windows Node":{
            stage("Printing Message"){
                echo "Hello World from Master"
                commonFunctions.createFile("null","Hello how are you")
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

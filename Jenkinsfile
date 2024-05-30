node("slave_windows_root"){

    stage("Git Checkout"){
        gitFunctions.gitClone(url="https://github.com/ricky001/gitlab4j-api.git")
    }

    parallel(

        "Windows Node":{
            stage("Printing Message"){
                echo "Hello World from Master"
            }
        },
        "Linux Node":{
            node("windows_2"){
                stage("Get OS Name"){
                    def osName=commonFunctions.getOS()
                    echo "${osName}"
                }
            }

        }
    )
    


}

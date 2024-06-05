node("slave_windows_root") {
    stage("Git CheckOut") {
        catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
            gitFunctions.gitClone(url='https://github.com/ricky001/gitlab4j-api.git')
            commonFunctions()
        }
    stage("Parallel Builds"){
            parallel(
                "Windows Build":{
                    node("windows_2"){
                            commonFunctions.createFile("aa.txt","Hey I am Somya running on Windows")
                            commonFunctions.createFile("ab.txt","Hey I am Vicky running on Windows")
                            stash name: 'file',includes:'*.txt'
                    }

            },
                "Linux Build":{
                    node("slave_windows_root"){
                        sleep(10)
                        unstash 'file'
                        def filesArray = commonFunctions.detectFiles(env.WORKSPACE,"*.txt")
                        echo "${filesArray}"
                    }

                }
                )
    }
    }
}

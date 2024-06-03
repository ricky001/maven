node("slave_windows_root") {
    stage("Git CheckOut") {
        catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
            gitFunctions.gitClone(url='https://github.com/ricky001/gitlab4j-api.git')
        }
    stage("Parallel Builds"){
            parallel(
                "Windows Build":{
                    node("slave_windows_root"){
                            commonFunctions.createFile("aa.txt","Hey I am Somya running on Windows")
                            commonFunctions.createFile("ab.txt","Hey I am Vicky running on Windows")
                            stash name: 'file',includes:'*.txt'
                    }

            },
                "Linux Build":{
                    node("windows_2"){
                        unstash 'file'
                    }

                }
                )
    }
    }
}

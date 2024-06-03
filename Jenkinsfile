node("slave_windows_root") {
    stage("Git CheckOut") {
        catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
            gitFunctions.gitClone(url: 'https://github.com/ricky001/gitlab4j-api.git1')
        }
    }
}

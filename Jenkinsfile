@Library(["shared-lib"]) _
node {
    parallel(
        CheckOut: {
            node('slave_windows_root') {
                stage("CheckOut") {
                    echo "Hello World on slave_windows_root"
                }
            }
        },
        Hello: {
            node('windows_2') {
                stage("Hello") {
                    echo "Hello From windows_2"
                }
            }
        }
    )

    stage("After Parallel") {
        echo "After Parallel"
        String osName = commonFunctions.getOS()
        echo "${osName}"
    }
}

@Library("shared-lib@ORST-211") _
node {

    stage("Git Checkout") {
        git changelog: false, poll: false, url: 'https://github.com/ricky001/gitlab4j-api.git'
    }

    parallel(
        "Windows Build": {
            node('slave_windows_root') {
                stage("CheckOut") {
                    echo "Hello World on slave_windows_root"
                }
            }
        },
        "Linux Build": {
            node('windows_2') {
                stage("Hello") {
                    echo "Hello From windows_2"
                    String osName = commonFunctions.getOS()
                    echo "${osName}"
                }
            }
        }
    )
}

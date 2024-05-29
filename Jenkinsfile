//This is a sample Jenkins File

pipeline{

    agent none
    stages{
       stage("CheckOut"){
            agent {label "slave_windows_root"}
           steps{

               echo "Hello World on slave_windows_root"
           }
       }
       stage("Hello"){
           agent {label "windows_2"}
           steps{
                echo "Hello From windows_2"
           }
    }

}

pipeline{
    agent any
    stages{
        stage ('run script'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'vsphereMaikWaigant', usernameVariable: 'VI_USERNAME', passwordVariable: 'VI_PASSWORD')]) {
                  sh """
                    ls -lah
                    pwd
                    podman run --rm -it --entrypoint="/usr/bin/pwsh" \
                    -e VI_SERVER = "10.133.250.201" \
                    -e VI_USERNAME=${VI_USERNAME} \
                    -e VI_PASSWORD=${VI_PASSWORD} \
                    -e VI_VM=SputnikMaik \
                    -v ${WORKSPACE}/:/scripts vmware/powerclicore Get-ChildItem
                    # /scripts/pcli_core_docker_sample2.ps1
                  """
                }
            }
        }       
    }
}

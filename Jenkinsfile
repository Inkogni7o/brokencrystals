pipeline {
  agent any
    environment {
      SEMGREP_APP_TOKEN = credentials('SEMGREP_APP_TOKEN')
      // DTRACK_API_KEY = credentials('dtrack_api_key')

      // Uncomment the following line to scan changed
      // files in PRs or MRs (diff-aware scanning):
      SEMGREP_BASELINE_REF = "main"
      // Uncomment the following lines if Semgrep AppSec Platform > Findings Page does not create links
      // to the code that generated a finding or if you are not receiving PR or MR comments.
      // SEMGREP_JOB_URL = "${BUILD_URL}"
      // SEMGREP_COMMIT = "${GIT_COMMIT}"
      // SEMGREP_BRANCH = "${GIT_BRANCH}"
      // SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^https:\/\/github.com\/(.*).git$/, '$1')
      // SEMGREP_REPO_URL = env.GIT_URL.replaceFirst(/^(.*).git$/,'$1')
      // SEMGREP_PR_ID = "${env.CHANGE_ID}"
    }
    stages {
    //   stage('Semgrep-Scan') {
    //     steps {
    //         sh '''docker pull semgrep/semgrep && \
    //         docker run \
    //         -e SEMGREP_APP_TOKEN=$SEMGREP_APP_TOKEN \
    //         -e SEMGREP_REPO_URL=$SEMGREP_REPO_URL \
    //         -e SEMGREP_REPO_NAME=$SEMGREP_REPO_NAME \
    //         -e SEMGREP_BRANCH=$SEMGREP_BRANCH \
    //         -e SEMGREP_COMMIT=$SEMGREP_COMMIT \
    //         -e SEMGREP_PR_ID=$SEMGREP_PR_ID \
    //         -v "$(pwd):$(pwd)" --workdir $(pwd) \
    //         semgrep/semgrep semgrep ci --json --json-output=semgrep.json'''
    //   }
    // }
    // stage('Njsscan-scan') {
    //   steps {
    //     sh  ''' docker pull opensecurity/njsscan && \
    //     docker run -v "$(pwd):$(pwd)" -w $(pwd) \
    //     opensecurity/njsscan --json -o njsscan-scan.json $(pwd) .
    //     '''
    //   }
    // }

      // stage("Trivy-Scan"){
      //     steps{
      //         sh '''docker pull aquasec/trivy && \
      //         docker run -v "$(pwd):$(pwd)" -w $(pwd) \
      //         aquasec/trivy fs . -f json > trivy_scan.json'''
      //     }
      // }

      // stage("Cdxgen-Scan") {
      //   steps {
      //     sh 'touch WORKSPACE'
      //     sh ''' docker pull ghcr.io/cyclonedx/cdxgen && \
      //     docker run -v "$(pwd):$(pwd)" -w $(pwd) \
      //     ghcr.io/cyclonedx/cdxgen -r -o sbom.json
      //     '''
      //   }
      // }

      // stage('dependencyTrackPublisher') {
      //       steps {
      //     dependencyTrackPublisher artifact: './syft-sbom.json', projectName: 'my-project', projectVersion: '0.1', synchronous: true, dependencyTrackApiKey: DTRACK_API_KEY
      //       }
      // }

    // stage('Nuclei-Scan'){
    //   steps {
    //     sh ''' docker pull projectdiscovery/nuclei:latest && \
        
        
    //     '''
    //   }
    // }

    // stage('Gitleaks-Scan') {
    //   steps {
    //     sh ''' docker pull zricethezav/gitleaks:latest && \
    //     docker run -v "$(pwd):$(pwd)" \
    //     zricethezav/gitleaks:latest detect -f json -s $(pwd) -r $(pwd)/gitleakes_scan.json --exit-code 0
    //     '''
    //   }
    // }

    stage('Kics-Scan') {
      steps {
        sh '''docker pull checkmarx/kics:latest && \
        docker run -v "$(pwd):$(pwd)" \
        checkmarx/kics:latest scan -f json -p $(pwd) --exclude-severities high,medium,low,info,trace > kics_result.json 
        '''
      }
    }
 }
}
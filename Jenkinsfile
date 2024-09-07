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
    //     docker run opensecurity/njsscan --html $(pwd)
    //     '''
    //   }
    // }

      stage("TRIVY File scan"){
          steps{
              sh """docker pull aquasec/trivy:0.18.3 &&
              aquasec/trivy:0.18.3 trivy repo https://github.com/Inkogni7o/brokencrystals""" 
          }
      }


      // stage('dependencyTrackPublisher') {
      //       steps {
      //     dependencyTrackPublisher artifact: './syft-sbom.json', projectName: 'my-project', projectVersion: '0.1', synchronous: true, dependencyTrackApiKey: DTRACK_API_KEY
      //       }
      // }
  }
}
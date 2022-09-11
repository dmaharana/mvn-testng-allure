JP = [
    sourceUrl: '',
    gitBranch: '',
    repoName: '',
    testRunCmd: 'mvn clean test && allure generate --clean',
    srcLocation: '/home/titu/Documents/source/pyworkspace/pytest-example',
]
node('buildnode') {

}

def Preparation_stage(JP) {
    sh "git clone ${JP.sourceUrl} -b ${JP.gitBranch} --depth 1"
}
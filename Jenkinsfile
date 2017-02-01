node {
	def VERSION = "latest"
	stage("Checkout") {
		git branch: 'jenkins-integration', url: 'https://github.com/ipfs/js-ipfs.git'
		VERSION = sh(returnStdout: true, script: "git rev-parse HEAD").trim()
	}
	stage("Build") {
		sh "docker build -t quay.io/ipfs/js-ipfs:$VERSION ."
	}
	stage("Test") {
		sh "docker run quay.io/ipfs/js-ipfs:$VERSION"
	}
}

ansiColor('xterm') {
	node {
		def VERSION = "latest"
		stage("Checkout") {
			VERSION = sh(returnStdout: true, script: "git rev-parse HEAD").trim()
		}
		stage("Build") {
			sh "docker build -t quay.io/ipfs/js-ipfs:$VERSION ."
		}
		stage("Test") {
			sh "docker run quay.io/ipfs/js-ipfs:$VERSION"
		}
	}
}

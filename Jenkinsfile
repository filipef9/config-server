node("docker") {
    docker.withRegistry('https://hub.docker.com/', 'docker-hub') {
    
        git url: 'https://github.com/filipef9/config-server.git'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build 'config-server'
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}

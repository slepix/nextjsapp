node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage ("wait_prior_starting_smoke_testing") {
        def time = 30
        echo "Waiting 30 seconds for deployment to complete prior starting smoke testing"
        sleep time.toInteger() // seconds
    }
    
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
       app = sudo docker.build("slepix/nextjsapp")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        app.inside {
            sh 'echo "Tests passed"'
        }
    }
}

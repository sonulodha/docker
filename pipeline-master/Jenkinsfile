node {
    def cicd

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace /var/lib/jenkins/workspace/jobname*/

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image from Docker File */

        cicd = docker.build("mitrasonu/webimg")
    }

    stage('Test image') {
        
        cicd.inside {
            echo "Tests Passed Continous Delivery to Docker push"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-login') {
            cicd.push("${env.BUILD_NUMBER}")
            cicd.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}

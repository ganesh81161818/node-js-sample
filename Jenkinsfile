stage('Run Docker Container') {
    steps {
        script {
            // Clean up existing containers using port 3000
            sh '''
            CONTAINER_ID=$(docker ps -q --filter "ancestor=my-node-app")
            if [ ! -z "$CONTAINER_ID" ]; then
              echo "Stopping existing container using my-node-app image..."
              docker stop $CONTAINER_ID
              docker rm $CONTAINER_ID
            fi

            # Also handle if port 3000 is bound by any container
            PORT_IN_USE=$(docker ps --filter "publish=3000" -q)
            if [ ! -z "$PORT_IN_USE" ]; then
              echo "Stopping container using port 3000..."
              docker stop $PORT_IN_USE
              docker rm $PORT_IN_USE
            fi

            # Now run the new container
            docker run -d -p 3000:3000 my-node-app
            '''
        }
    }
}

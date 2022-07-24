# AVK

## What do we do
We are a startup for automating ci processes. Due to the fact that @johanneslosch is uses to develop Java Spring applications, he needs to make sure that a database is publicly accessible. Due to security reasons, he does not want to have one static databatabase. Instead, we create a temporary database or other docker images.

## How do we do this?
We deliver a github action (TODO) which sends a http request to the server. You can vue this image below. 
![Request Flowchart](https://lucid.app/publicSegments/view/c9107b4b-a960-452b-a8bb-0dff941aca6d/image.png)

So we have one master server which handles the requests and forwards them to the docker service. Which also formats the request for the docker api. Then we start the container and send the Github action module the response with URL to the docker-server and the used ports for requested containers.

After the CI workflow finishes, we get a new Reqest to stop and destroy the container(s). This is necessary because we follow 100 % the GDPR.
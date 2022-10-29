Deployment logic for the stocks app in the test environment

What is needed:
 - Docker Swarm environment
 - 2 secrets created in the swarm for the DB credentials:
   - echo "user" | docker secret create stocksmongouser -
   - echo "pass" | docker secret create stocksmongouserpassword -
 - The crazymax/swarm-cronjob:latest image running as a container or the program running as a service in the swarm cluster (https://crazymax.dev/swarm-cronjob/)
 - A container registry (self hosted in this case)
 
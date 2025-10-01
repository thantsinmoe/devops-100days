Task: There exists a deployment named nginx-deployment; initiate a rollback to the previous revision.

# Check deployments
k get deploy
k describe deploy nginx-deployment

# Roll back deployments
k rollout undo deploy nginx-deployment
k describe deploy nginx-deployment

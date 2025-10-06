Task:
1. Create a pod named print-envars-greeting.

2. Configure spec as, the container name should be print-env-container and use bash image.

3. Create three environment variables:

a. GREETING and its value should be Welcome to

b. COMPANY and its value should be xFusionCorp

c. GROUP and its value should be Datacenter

4. Use command ["/bin/sh", "-c", 'echo "$(GREETING) $(COMPANY) $(GROUP)"'] (please use this exact command), also set its restartPolicy policy to Never to avoid crash loop back.

5. You can check the output using kubectl logs -f print-envars-greeting command.

# Create pod with dry-run
k run print-envars-greeting --image=bash --env="GREETING=Welcome to" --env="COMPANY=xFusionCorp" --env="GROUP=Datacenter" --dry-run=client -o yaml > pod.yaml
vi pod.yaml # Edit pod.yaml
k apply -f pod.yaml

# Check logs
k get po
k logs -f print-envars-greeting
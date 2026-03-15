# Section 3 – Thought Process – Production Went Down

## Scenario

The application in production is reported as unavailable. Users cannot access the service, and monitoring systems indicate that the application may be down.

The goal is to investigate the issue systematically and restore the service as quickly as possible.

## Step 1 – Confirm the Incident

The first step is to confirm whether the service is actually down.

This can be done by:
- checking monitoring dashboards
- verifying alerts from monitoring systems
- attempting to access the application manually
- testing the endpoint using tools like curl

Example:

curl https://example.com

This confirms whether the issue is real and affecting users.

## Step 2 – Check Recent Changes

Most production outages occur after a recent change.

Check:
- recent deployments
- CI/CD pipeline activity
- recent commits in the repository
- infrastructure changes
- configuration updates

If a deployment occurred recently, it is a strong candidate for the root cause.

## Step 3 – Check Infrastructure

Next, inspect the infrastructure to verify that services are running.

Check:
- running containers
- Kubernetes pods
- load balancer status
- database connectivity
- network configuration

Example commands:

docker ps
kubectl get pods
kubectl get services

This helps determine whether infrastructure components are healthy.

## Step 4 – Inspect Logs

Logs usually reveal the root cause of the failure.

Check:
- application logs
- container logs
- reverse proxy logs
- Kubernetes events

Example:

docker logs <container_id>
kubectl logs <pod-name>

Look for:
- application crashes
- configuration errors
- dependency failures
- connection issues

## Step 5 – Mitigation

If the outage was caused by a recent deployment, the fastest solution is often a rollback.

Example:

kubectl rollout undo deployment/app

The main goal is to restore service availability as quickly as possible.

## Step 6 – Fix the Root Cause

After restoring service, investigate and correct the underlying problem.

Possible causes include:
- incorrect configuration
- missing environment variables
- dependency issues
- network or database failures

Once identified, implement a proper fix.

## Step 7 – Verify Recovery

After applying the fix, verify that the system is functioning normally.

Check:
- monitoring dashboards
- error rates
- application responses
- logs for remaining issues

## Step 8 – Post-Incident Documentation

Finally, document the incident.

Include:
- what happened
- what caused the outage
- how it was fixed
- how similar issues can be prevented

This improves future incident response and system reliability.

## Conclusion

A structured troubleshooting process helps quickly identify and resolve production incidents.

The key steps include confirming the issue, checking recent changes, inspecting infrastructure and logs, applying mitigation strategies, fixing the root cause, and documenting the incident for future improvements.
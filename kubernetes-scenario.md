# Production Chaos Scenarios: Real Engineering Challenges

These aren't definition questions. These are real chaos scenarios that reveal whether you can think like a production-ready engineer - not just run commands.

## 1. Deployment Succeeded But Traffic Still Going to Old Version

**Scenario:**
A deployment succeeded, but traffic is still going to the old version.
Explain exactly where you start debugging.

**What this tests:**
- Understanding of the full deployment pipeline beyond kubectl
- Knowledge of load balancing, DNS, and traffic routing layers
- Ability to systematically isolate failure points
- Production incident response thinking

---

## 2. Kubernetes Pods Healthy But Users See 504 Errors

**Scenario:**
A Kubernetes application is healthy according to `kubectl get pods`, but users report 504 errors.
Walk me through your troubleshooting flow.

**What this tests:**
- Understanding that pod health ≠ service health
- Knowledge of networking, ingress, service discovery
- Ability to think beyond the obvious metrics
- Real-world scenario: probes may pass but the app isn't actually serving traffic correctly

---

## 3. AWS Bill Spiked 3x Overnight With No Deployments

**Scenario:**
Your AWS bill spiked 3x overnight. No deployments happened. What's your step-by-step response?

**What this tests:**
- Understanding of AWS cost drivers (data transfer, compute, storage, unused resources)
- Incident response prioritization
- Ability to investigate without panicking
- Real scenario: runaway processes, misconfigured auto-scaling, leaked resources

---

## 4. CI/CD Pipeline Taking 40+ Minutes, Must Get to Under 10

**Scenario:**
CI/CD pipeline is taking 40+ minutes. Your CTO wants it under 10 without adding hardware.
What will you optimize?

**What this tests:**
- Understanding of pipeline stages and bottlenecks
- Knowledge of caching, parallelization, and optimization techniques
- Ability to think critically about trade-offs
- Real-world constraints: no budget, existing infrastructure

---

## 5. SRE Says Stable, Dev Says Slow, Monitoring Says GREEN

**Scenario:**
An SRE says infra is stable, dev team says the system is slow, and monitoring shows everything is GREEN.
Who do you believe — and what do you check first?

**What this tests:**
- Understanding of the gap between monitoring and user experience
- Ability to navigate conflicting information
- Knowledge of latency, percentiles, and blind spots in metrics
- Real scenario: p99 latency matters more than average; something is falling through cracks

---

## 6. Terraform Apply Failing Due to Drift on Critical Live Infra

**Scenario:**
Terraform apply is failing due to drift, but the infra is currently live and critical.
How do you fix it without causing downtime?

**What this tests:**
- Understanding of Terraform state and drift
- Knowledge of risk mitigation in production
- Ability to make decisions under pressure
- Real scenario: manual changes, out-of-band modifications, state conflicts

---

## 7. Rollback Script Fails During Production Outage With 5 Minutes Until SLA Breach

**Scenario:**
Your rollback script fails during a production outage. You have 5 minutes before SLA breach.
Walk me through your decision.

**What this tests:**
- Crisis decision-making under time pressure
- Understanding of when to abandon automation and go manual
- Knowledge of fallback strategies
- Real scenario: automation itself can become the bottleneck; sometimes you need humans

---

## 8. Secret Accidentally Committed to GitHub That's Already Been Cloned

**Scenario:**
A secret was accidentally committed to GitHub. It has already been cloned.
What are your next exact steps?

**What this tests:**
- Understanding of security incident response
- Knowledge of secret rotation procedures
- Ability to act decisively and in the right order
- Real scenario: git history is permanent; prevention and response matter equally

---

## 9. Kubernetes Cluster Upgrade Works in Staging But Corrupts Core DNS in Production

**Scenario:**
A Kubernetes cluster upgrade works in staging but corrupts core DNS in production.
How do you approach patching and restoring service?

**What this tests:**
- Understanding of cluster health dependencies
- Knowledge of DNS and service discovery criticality
- Ability to navigate catastrophic but recoverable failures
- Real scenario: staging != production; subtle environment differences break upgrades

---

## 10. Tell Me About a Real Failure You Introduced

**Scenario:**
Tell me a real scenario where YOU introduced a failure in infrastructure.
What happened, what did you learn, and what changed after?

**Most candidates freeze here. Because this question isn't about tools - it's about awareness, accountability, and engineering maturity.**

**What this tests:**
- Honesty and self-awareness
- Ability to learn from mistakes
- Engineering maturity and accountability
- Real-world perspective on incident response
- Growth mindset and continuous improvement

---

## Notes

These scenarios are designed to test:
1. **Systems thinking** - understanding how components interact
2. **Troubleshooting methodology** - not just knowing commands, but how to think
3. **Production readiness** - can you handle real chaos?
4. **Decision-making** - what matters when everything is broken?
5. **Accountability** - do you own your mistakes?

Real engineers don't memorize answers - they learn to ask the right questions and think systematically.

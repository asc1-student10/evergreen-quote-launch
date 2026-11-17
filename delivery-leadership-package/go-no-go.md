# Go / No-Go: Friday Launch Demo

**Date / time:** Nov 18, 2026, [time]
**Decision:** ☐ GO   ☐ NO-GO   ☒ GO WITH CONDITIONS

## CI evidence

- Latest run on `delivery/lead`, both jobs: [green]. Link: [https://github.com/asc1-student10/evergreen-quote-launch/actions/runs/44160700053/job/134313407368]
- Workflow file: `.github/workflows/ci.yml`
- Steps checked: Test the API (API test suite); Type-check and build the client.

## Local cluster evidence (kind `kind-evergreen`, our VM)

- Three `evergreen-quote-api` pods and one `mongo` pod: [Running] as of this afternoon.

## Shared demo cluster (not ours)

- Namespace `demo`, owned by another team, platform team.
- Three API pods in CrashLoopBackOff since the variable rename about 30 minutes ago.
- Routed to [owner] just now. Not our environment, and not a condition of this decision.

## What "GO" would mean

- Friday's demo runs on our local kind cluster, against our verified stack.
- The shared demo cluster incident is tracked by its owner and does not affect our merge or demo.

## What "NO-GO" would mean

- Hold the demo if our CI or local cluster is red at Thursday's rehearsal.
- Owner: Ricky Cotton. Re-evaluate: Thursday.

## My call

GO WITH CONDITIONS. Friday's demo runs on our own cluster and our own CI, and both are the evidence we can stand behind. The shared demo cluster is broken, but it belongs to the platform team and has its own owner, so it is tracked there, not in our go/no-go.

Conditions:
1. Our latest two-job CI run is green at Thursday's rehearsal.
2. Our local kind cluster still shows three API pods and one mongo pod Running at Thursday's rehearsal.

What would change my mind: our own `k8s/deployment.yaml` turns out to use the same `MONGO_URI` name the shared cluster now injects, which would mean our stack shares the fault and this becomes a NO-GO.

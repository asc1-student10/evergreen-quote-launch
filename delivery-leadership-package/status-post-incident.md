# Status Update: Shared Demo Cluster Incident

**To:** Demo Environment Platform Owner
**From:** Ricky Cotton, Delivery Lead
**Date:** Nov 18, 2026, 4:00PM

## What we observed
- In the shared demo cluster's `demo` namespace, three `evergreen-quote-api` pods are in CrashLoopBackOff, with restart counts still climbing.
- The `mongo` pod is 1/1 Running with no restarts.
- The API logs show connection refused to `127.0.0.1:27017`, and the deployment sets `MONGO_URI` where our app reads `MONGODB_URI` [confirm against `api/src`].
- The quote page has shown "Could not load recent quotes" since about 13:25.

## What is not affected
- Our stack is separate. Our local kind cluster has three API pods and mongo Running at this time, and our latest CI run is green.
- We have not changed anything on the shared demo cluster, and we won't.

## What I need from you
- **Owner:** Confirm you own the shared demo cluster's incident.
- **Action:** Confirm whether the variable rename is the cause, and restore the name the app reads.
- **Time:** Tell me by Thursday at 12:00pm when this will be resolved, so I can give the manager a date.

Friday's demo runs on our local cluster, so we are not blocked. I'll send the manager a separate holding message.

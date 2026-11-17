# Program Showcase: Evergreen Quote Launch

## Slide 1: Delivery goal & did we hit it?

- **Goal:** By Thursday, Evergreen Insurance Quote is merged to `main` with a green two-job CI run, and a quote saved in the browser survives a reload with the same premium, served from the database through the API.
- **Hit?** ☒ Yes
- **Why:** The client is wired to the API, the seam defect is fixed, the rates are aligned, and GraphQL is mounted. The container, the local cluster demo, and the merge to `main` are [done].

## Slide 2: What shipped

- the quote list shows quotes from the database, and a saved quote appears after a reload.
- Merged PR: https://github.com/asc1-student10/evergreen-quote-launch
- Green two-job CI run on the merge commit: https://github.com/asc1-student10/evergreen-quote-launch/actions/runs/44170230703

## Slide 3: Two key decisions

- **Decision 1: Keep the instant estimate in the app, and make the saved premium the service's number.** Why it mattered: customers see an estimate immediately, and the number they save is the one the service stores. We checked that both calculations match.
- **Decision 2: Split marketing's life-first request.** We approved the landing hero and banner, which are content, and routed the form default to the team that owns the estimate code. Why it mattered: a one-word change to shared code two days before launch needed the owning team's review.

## Slide 4: Risks & injects

- **Top risk:** The demo depends on a running database. The client reads from the API, which reads from MongoDB, so a stopped service breaks the quote list and saves.
- **Other tracked risks:** Premium rates differed between client and API (now aligned); wiring files were missing or misplaced (fixed); port 3000 is shared by three processes (we stop the dev server before any port-forward).
- **Inject #1 (Tue):** Life-first request and renters. Split the request; deferred renters with its two validation systems as the reason.
- **Inject #2 (Wed):** A shared demo cluster went into a crash loop after a variable rename. It belongs to the platform team, which owns the fix. Our own cluster and CI were green, so we made a go-with-conditions call for Friday.

## Slide 5: What three phases built

- **The journey:** A static page that promised a quote, then a React app that computed one, then an API that remembered it. This week they became one product: the page, the app, and the database connected.
- **What I take back to work on Monday:** A response that looks right isn't proof: I want to see the number, and the test that would catch it being wrong.
- **What I'd do differently next round:** Check the environment before each working block, so a stale process or missing file surfaces early.

## Q&A prep

- **"Why not make every estimate a network call?"** It would make the estimate wait on the service and fail whenever the service is down. We keep the estimate in the app and check it against the service before each demo.
- **"A $4,050 premium for a $300,000 home policy? Is that right?"** That's the sponsor's rate table applied to the coverage amount. 
- **"Why didn't you ship life-first?"** The landing hero and banner shipped. The form default is a one-word change in shared code, so it went to the team that owns it.
- **"Why do some saved quotes show older premiums?"** The six original seed quotes carry premiums from an older rate table, as expected. New quotes use the current rates.
- **"Whose cluster broke during the week?"** The shared demo cluster belongs to the platform team, which owns the fix. Our own stack and CI were green. [confirm the platform team's status]
- **"Does the demo depend on the cloud?"** No. Friday's demo runs on our local cluster, so it does not depend on the shared environment or the cloud window.

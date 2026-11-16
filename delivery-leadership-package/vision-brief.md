# Evergreen Quote: Vision Brief

## Product
**Name:** Evergreen Insurance Quote (the launch: full-stack delivery)
**Delivery week:** Final - Week of November 16, 2026
**Delivery Lead:** Ricky Cotton
**Engineering team (represented by):** https://github.com/asc1-student10/evergreen-quote-launch
**GitHub Project board:** https://github.com/users/asc1-student10/projects/7

## Who is the customer?
The first-time insurance shopper on a phone, who wants a believable monthly premium in a few minutes, with no account and no phone call.

## What pain does Evergreen Quote remove?
A shopper who gets an estimate today loses it on reload, and the number they saw can differ from the one that gets saved. Once the page, the app, and the database are connected, a quote they save stays available, and the premium they see is the one we stored. Partners get the same quotes through a GraphQL query, without a separate system.

## What does "good" look like at end of the week?
- A quote saved in the browser shows the same premium after a reload, served from the database through the API.
- The estimate and the saved premium match, because client and API use the same launch rates.
- The bundled sample data is removed from the repo, and the quote list reads from the API.
- Both CI jobs are green on the merged `main`, from a single reviewed PR.
- On the local cluster, three API pods run behind one Service, and a quote saved from the app lands in the cluster database.

## What are we explicitly NOT doing this week?
- Accounts, authentication, payments, or a real rate engine.
- Redesigning the landing page beyond the launch banner and quote links.
- New products, such as renters coverage.
- Cloud spend on the required path. The EKS window happens only if the sponsor opens it.

## How will we know if it worked?
- 1 end-to-end run on Thursday: save a quote, reload, and confirm the same premium is shown.
- 0 mismatches between estimate and saved premium across the six seeded quotes plus three new ones.
- 2 of 2 CI jobs green on the merge commit.

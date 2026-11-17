# Delivery Goal: Evergreen Quote

## Goal

By Thursday, Evergreen Insurance Quote is merged to `main` with a green two-job CI run, and a quote saved in the browser survives a reload with the same premium, served from the database through the API.

## "Done" looks like

- The quote page loads its recent quotes from the API, and a saved quote survives a reload.
- The estimate on screen and the saved premium agree, at the launch rates.
- `npm test` (API) and `npm run type-check` + `npm run build` (client) pass; both CI jobs on the merge commit are **green**.
- The containerized API serves the wired app, and the cluster demo shows three API pods behind one Service.
- The landing page carries the launch banner and points at the app.
- A reviewed PR is merged, branch deleted.
- `delivery-leadership-package/` is complete and committed.

## Out of scope (this week)

- Accounts, authentication, payments, or a real rate engine.
- Redesigning the landing page beyond the launch banner and quote links.
- New products, such as renters coverage.
- Cloud spend on the required path. The EKS window happens only if the sponsor opens it.

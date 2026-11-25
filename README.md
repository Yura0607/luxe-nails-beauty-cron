# Luxe Nails Beauty — CalDAV cron

This repository has **no booking-app source**. It only runs a GitHub Actions
schedule that pings the production CalDAV sync endpoint so two-way iCloud
calendar sync can run every 10 minutes.

The salon app is on the Vercel Hobby plan, which only allows daily crons, so
this workflow is the frequent poller.

- **Endpoint:** `https://luxe-nails-beauty-salon.vercel.app/api/cron/caldav`
- **Schedule:** `*/10 * * * *` (every 10 minutes, UTC). GitHub may delay scheduled workflows when busy.
- **Manual run:** Actions → CalDAV sync → Run workflow
- **Auth:** `Authorization: Bearer` from the repository secret `CRON_SECRET` (never stored in this repo)

If you regenerate `CRON_SECRET`, update it in both this repository’s Actions secrets and the Vercel project’s Production and Preview environment variables, then redeploy.

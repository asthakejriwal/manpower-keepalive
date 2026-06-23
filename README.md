# manpower-keepalive

Keep-alive pinger for the CarDekho SEA **Manpower Cost dashboard**
(<https://manpower-dashboard-mt5r.onrender.com>), which runs on Render's free
tier and spins down after ~15 min idle (cold start ~50-60s).

A GitHub Actions cron (`.github/workflows/keep-alive.yml`) pings the public
`/healthz` endpoint every ~10 minutes during **9am-11pm IST, all 7 days**, so the
instance stays warm during working hours. Outside that window it's allowed to
spin down (conserves Render's free instance-hours).

- **Public repo** so GitHub Actions minutes are free/unlimited.
- Contains **no business data** — only the ping workflow.
- The once-a-day `heartbeat.txt` commit keeps the repo active so GitHub doesn't
  auto-disable the scheduled workflow after 60 days of inactivity.

Adjust the window/days by editing the `cron:` line (it's in UTC; IST = UTC+5:30).

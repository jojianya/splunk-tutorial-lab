# Exploration Searches

Run each search in Splunk's Search & Reporting app with the time range set to **All time**.

| File | Question it answers | What a suspicious result looks like |
| --- | --- | --- |
| `01-top-client-ips.spl` | Which client IPs generate the most web requests? | One IP with a share far larger than every other client |
| `02-http-errors-by-ip.spl` | Which IPs hit the most HTTP errors, and which codes? | A single IP dominated by 403/404s, or many 5xx from one source |
| `03-ssh-failed-by-ip.spl` | Which IPs fail SSH password auth most often? | A non-internal IP with a high failure count |
| `04-ssh-failures-timechart.spl` | How do failed SSH logins look per hour? | A sudden spike or a long flat line of constant failures |
| `05-invalid-usernames.spl` | Which IPs try usernames that do not exist? | One IP with many `unique_users` relative to attempts |

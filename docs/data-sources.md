# Data Sources

Sourcetypes found in the Splunk tutorial dataset (`tutorialdata.zip` plus `Prices.csv.zip`), all indexed into `tutorial`.
Timestamps in this dataset are old, so always search with **All time**.

| Sourcetype | Description | Key fields |
| --- | --- | --- |
| `access_combined_wcookie` | Apache-style web access log, one line per HTTP request, with a cookie value appended. | `clientip`, `status`, `method`, `uri`, `bytes`, `referer`, `useragent`, `JSESSIONID` (verify in Splunk) |
| `secure` | Linux auth/secure log with SSH session activity, including successful and failed logins. | `host`, `user`, `src_ip` / `src` (after `rex`), `action`, `dest` (verify in Splunk) |
| `vendor_sales` | Sales transactions from a fictional vendor, used for the tutorial's reporting examples. | `vendor`, `product_name`, `price`, `sale_price`, `quantity` (verify in Splunk) |
| `cisco_wsa_squid` | Web proxy access log from a Cisco Web Security Appliance in Squid format. | `src_ip` / `src`, `dest`, `status_code`, `url`, `action`, `bytes` (verify in Splunk) |
| `csv` / `prices` (verify in Splunk) | `Prices.csv` product price reference loaded by the tutorial's lookup examples. | `product_name` / `productId`, `price` (verify in Splunk) |

Notes:

- `access_combined*` matches `access_combined_wcookie`; use it when you are unsure of the exact variant.
- Field names for the proxy and CSV data vary by parsing; confirm them with `index=tutorial sourcetype=<name> | fieldsummary` before writing detections.
- Any row marked "verify in Splunk" should be confirmed in a live search rather than trusted from this table.

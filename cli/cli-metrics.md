---

copyright:
  years: 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Metrics

The following `metrics` commands are available:

* Web analytics
* DNS analytics
* Ratelimit analytics

## Web Analytics
**NAME**

   `web-analytics` - Get analytics of the DNS domain.

**USAGE**

   `ibmcloud cis web-analytics DNS_DOMAIN_ID [--recent DURATION] [-t, --table requests | bandwidth | uniques | threats | status_code] [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

**OPTIONS**

   `--recent`  The beginning of the requested time frame. Valid vaules are: 6h (6 hours ago), 12h, 1d (1 day ago), 1w (1 week ago), 1m (1 month ago), 2m, 3m. (default: `1w`)

   `-t, --table`     Output table. Valid values are `requests`, `bandwidth`, `uniques`, `threats` and `status_code`. If not set, it outputs all the tables.

   `-i, --instance INSTANCE_NAME`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.

   `--output FORMAT`    Specify output format, only JSON is supported now.


## DNS analytics
**NAME**

   `dns-analytics` - Get DNS analytics of the domain.

**USAGE**

   `ibmcloud cis dns-analytics DNS_DOMAIN_ID DIMENSION [-i, --instance INSTANCE_NAME] [-s, --since TIME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

   `DIMENSION` is queried dimension. The valid value is either `queries-by-response-code` or `queries-by-type`.

**OPTIONS**

   `-i, --instance INSTANCE_NAME`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.

   `-s, --since` Since time to now. Valid values are: `6h` (6 hours ago), `12h`, `1d` (1 day ago), `1w` (1 week ago)

   `--output FORMAT`  Specify output format, only JSON is supported now.



## Ratelimit Analytics
**NAME**

   `ratelimit-analytics` - Get rate limit analytics for a DNS domain.

**USAGE**

   `ibmcloud cis ratelimit-analytics DNS_DOMAIN_ID [--recent DURATION] [--time-delta SECONDS] [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

**OPTIONS**
   `--recent`             The beginning of the requested time frame. Valid vaules are: 6h (6 hours ago), 12h, 1d (1 day ago), 1w (1 week ago), 1m (1 month ago), 2m, 3m. (default: `1w`)

   `--time-delta`  The time interval (seconds) of each analytic's record. Valid values: `60`, `3600`, `86400`, `2592000`. (default: 3600)

   `-i, --instance INSTANCE_NAME` Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

   `--output FORMAT`   Specify output format, only JSON is supported now.

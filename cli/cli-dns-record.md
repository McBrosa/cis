---

copyright:
  years: 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# DNS Record

The following `dns-record` commands are available:

* Create DNS record
* Update DNS record
* Get DNS record
* Delete DNS record
* List DNS records
* Upload your BIND config
* Export BIND config

## Create DNS record
**NAME**

   `dns-record-create` - Create a DNS record for a given domain of a service instance.

**USAGE**

   `ibmcloud cis dns-record-create DNS_DOMAIN_ID (-s, --json-str JSON_STR | -j, --json-file JSON_FILE) [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

**OPTIONS**

   `-s, --json-str`  The JSON data used to describe a DNS Record.

   Supported DNS Record types are: `A`, `AAAA`, `CNAME`, `NS`, `TXT`, `SPF`, `MX`, `LOC`, `SRV`, `CAA`.

  * For type `A`, `AAAA`, `CNAME`, `NS`, `TXT`, `SPF`:
    * The required fields in JSON data are `name`, `type`, `content`:
    * The optional fields are `ttl`, `proxied`:
      * `proxied` Control whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:


                   {
                       "name": "testA",
                       "type": "A",
                       "content": "127.0.0.1"
                   }

                   {
                       "name": "testAAAA",
                       "type": "AAAA",
                       "content": "2001:0db8:0012:0001:3c5e:7354:0000:5db1"
                   }

                   {
                       "name": "testCNAME",
                       "type": "CNAME",
                       "content": "example.com"
                   }

                   {
                       "name": "testNS",
                       "type": "NS",
                       "content": "ns1.example.com"
                   }

                   {
                       "name": "testTXT",
                       "type":"TXT",
                       "content": "text information"
                   }

                   {
                       "name": "testSPF",
                       "type":"SPF",
                       "content": "v=spf1 a ip:1.2.3.4"
                   }


   * For type `MX`:
     * The required fields in JSON data are `name`, `type`, `content`:
     * The optional fields are `ttl`, `priority`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "name": "testMX",
                       "type": "MX",
                       "content": "smtp.example.com",
                       "priority": 10
                   }


   * For type `LOC`:
     * The required fields in JSON data are `name`, `type`, `data`:

                       "data":
                           "lat_degrees": Degrees of latitude.
                           "lat_minutes": Minutes of latitude
                           "lat_seconds": Seconds of latitude.
                           "lat_direction": Latitude direction.
                           "long_degrees": Degrees of longitude.
                           "long_minutes": Minutes of longitude.
                           "long_seconds": Seconds of longitude.
                           "long_direction": Longitude direction.
                           "altitude": Altitude of location in meters.
                           "size": Size of location in meters.
                           "precision_horz": Horizontal precision of location.
                           "precision_vert": Vertical precision of location.

     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "name": "testLOC",
                       "type": "LOC",
                       "data": {
                            "lat_degrees": 45,
                            "lat_minutes": 0,
                            "lat_seconds": 0,
                            "lat_direction": "N",
                            "long_degrees": 45,
                            "long_minutes": 0,
                            "long_seconds": 0,
                            "long_direction": "E",
                            "altitude": 20,
                            "size": 0,
                            "precision_horz": 0,
                            "precision_vert": 0
                       }
                   }


   * For type `SRV`:
     * The required fields in JSON data are `type`, `data`:

                       "data":
                           "service": A service type, prefixed with an underscore.
                           "proto": A valid protocol.
                           "priority": Priority.
                           "weight": The record weight.
                           "port": The port of the service.
                           "target": A valid hostname.

     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "type": "SRV",
                       "data": {
                            "service": "_ftp",
                            "proto": "_tcp",
                            "name": "testSRV",
                            "priority": 1,
                            "weight": 1,
                            "port": 21,
                            "target": "example.com"
                       }
                   }

   * For type `CAA`:
     * The required fields in JSON data are name, `type`, `data`:
     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "name": "testCAA.yourdomain.com",
                       "type": "CAA",
                       "data": {
                            "tag": "issue",
                            "value": "letsencrypt.org"
                       }
                   }
   `-j, --json-file`  A file contains input JSON data.

   `-i, --instance INSTANCE_NAME`   Instance name. If the name is not set, the context instance specified by `ibmcloud cis instance-set` is used.

   `--output FORMAT`     Specify output format, only JSON is supported now.


## Update DNS record

**NAME**

   `dns-record-update` - Update a DNS record for a given domain of a service instance.

**USAGE**

   `ibmcloud cis dns-record-update DNS_DOMAIN_ID DNS_RECORD_ID (-s, --json-str JSON_STR | -j, --json-file JSON_FILE) [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

   `DNS_RECORD_ID` is the ID of DNS record.

**OPTIONS**

   `-s, --json-str`  The JSON data used to describe a DNS Record.

   Supported DNS Record types are: `A`, `AAAA`, `CNAME`, `NS`, `TXT`, `SPF`, `MX`, `LOC`, `SRV`, `CAA`.

   * For type `A`, `AAAA`, `CNAME`, `NS`, `TXT`, `SPF`:
     * The required fields in JSON data are `name`, `type`, `content`:
     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

  Sample JSON data:


                   {
                       "name": "testA",
                       "type": "A",
                       "content": "127.0.0.1"
                   }

                   {
                       "name": "testAAAA",
                       "type": "AAAA",
                       "content": "2001:0db8:0012:0001:3c5e:7354:0000:5db1"
                   }

                   {
                       "name": "testCNAME",
                       "type": "CNAME",
                       "content": "example.com"
                   }

                   {
                       "name": "testNS",
                       "type": "NS",
                       "content": "ns1.example.com"
                   }

                   {
                       "name": "testTXT",
                       "type":"TXT",
                       "content": "text information"
                   }

                   {
                       "name": "testSPF",
                       "type":"SPF",
                       "content": "v=spf1 a ip:1.2.3.4"
                   }




   * For type `MX`:
     * The required fields in JSON data are `name`, `type`, `content`:
     * The optional fields are `ttl`, `priority`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "name": "testMX",
                       "type": "MX",
                       "content": "smtp.example.com",
                       "priority": 10
                   }




   * For type `LOC`:
     * The required fields in JSON data are `name`, `type`, `data`:

                       "data":
                           "lat_degrees": Degrees of latitude.
                           "lat_minutes": Minutes of latitude
                           "lat_seconds": Seconds of latitude.
                           "lat_direction": Latitude direction.
                           "long_degrees": Degrees of longitude.
                           "long_minutes": Minutes of longitude.
                           "long_seconds": Seconds of longitude.
                           "long_direction": Longitude direction.
                           "altitude": Altitude of location in meters.
                           "size": Size of location in meters.
                           "precision_horz": Horizontal precision of location.
                           "precision_vert": Vertical precision of location.

     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "name": "testLOC",
                       "type": "LOC",
                       "data": {
                            "lat_degrees": 45,
                            "lat_minutes": 0,
                            "lat_seconds": 0,
                            "lat_direction": "N",
                            "long_degrees": 45,
                            "long_minutes": 0,
                            "long_seconds": 0,
                            "long_direction": "E",
                            "altitude": 20,
                            "size": 0,
                            "precision_horz": 0,
                            "precision_vert": 0
                       }
                   }




  * For type `SRV`:
     * The required fields in JSON data are `type`, `data`:

                       "data":
                           "service": A service type, prefixed with an underscore.
                           "proto": A valid protocol.
                           "priority": Priority.
                           "weight": The record weight.
                           "port": The port of the service.
                           "target": A valid hostname.

     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "type": "SRV",
                       "data": {
                            "service": "_ftp",
                            "proto": "_tcp",
                            "name": "testSRV",
                            "priority": 1,
                            "weight": 1,
                            "port": 21,
                            "target": "example.com"
                       }
                   }



   * For type `CAA`:
     * The required fields in JSON data are `name`, `type`, `data`:
     * The optional fields are `ttl`, `proxied`:
       * `proxied` Controls whether traffic should flow through the security and performance functions on CIS. Can be used for update only.

   Sample JSON data:

                   {
                       "name": "testCAA.yourdomain.com",
                       "type": "CAA",
                       "data": {
                            "tag": "issue",
                            "value": "letsencrypt.org"
                       }
                   }
                   
    `-j, --json-file`   A file contains input JSON data.

   `-i, --instance INSTANCE_NAME`   Instance name. If the name is not set, the context instance specified by `ibmcloud cis instance-set` is used.

   `--output FORMAT`     Specify output format, only JSON is supported now.

## Get DNS record

**NAME**

   `dns-record` - Get a DNS record details for a given domain under a service instance.

**USAGE**

   `ibmcloud cis dns-record DNS_DOMAIN_ID DNS_RECORD_ID [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

   `DNS_RECORD_ID` is the ID of DNS record.

**OPTIONS**

   `-i, --instance INSTANCE_NAME`  Instance name. If the name is not set, the context instance specified by `ibmcloud cis instance-set` is used.

   `--output FORMAT`    Specify output format, only JSON is supported now.


## Delete DNS record

**NAME**

   `dns-record-delete` - Delete a DNS record for a given domain of a service instance.

**USAGE**

   `ibmcloud cis dns-record-delete DNS_DOMAIN_ID DNS_RECORD_ID [-i, --instance INSTANCE_NAME]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

   `DNS_RECORD_ID` is the ID of DNS record.

**OPTIONS**

   `-i, --instance INSTANCE_NAME`  Instance name. If the name is not set, the context instance specified by `ibmcloud cis instance-set` is used.


## List DNS Records

**NAME**

   `dns-records` - List all DNS records for a given domain of a service instance.

**USAGE**

   `ibmcloud cis dns-records DNS_DOMAIN_ID (-s, --json-str JSON_STR | -j, --json-file JSON_FILE) [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

**OPTIONS**

   `-s, --json-str`  The JSON data to query DNS records.

The optional fields are `type`, `name`, `content`, `page`, `per_page`, `order`, `direction`,`match`:

  * `type` Type of DNS records to display.      
  * `name` Value of name field to filter by.
  * `content` Value of content field to filter by.
  * `page` Page number of paginated results.
  * `per_page` Maximum number of DNS records per page.
  * `order` Field by which to order list of DNS records. Valid values are `type`, `name`, `content`, `ttl`, `proxied`
  * `direction` Direction in which to order results [ascending or descending order]. Valid values are `asc`, `desc`         
  * `match` Whether to match all or at least one search parameter. Valid values are `any`, `all`.

  Sample JSON data:

                   {
                       "type": "CAA",
                       "page": 1,
                       "per_page": 20
                   }
                   
   `-j, --json-file`  A file contains input JSON data.

   `-i, --instance INSTANCE_NAME`   Instance name. If name is not set, the context instance specified by `ibmcloud cis instance-set` is used.

   `--output FORMAT`     Specify output format, only JSON is supported now.


**Output Table Columns**
   * ID
   * Name
   * Type
   * Content
   * Proxied
   * TTL


## Upload your BIND config

**NAME**

   `dns-records-import` - Upload your BIND config.

**USAGE**

   `ibmcloud cis dns-records-import DNS_DOMAIN_ID (--file FILE) [-i, --instance INSTANCE_NAME] [--output FORMAT]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

**OPTIONS**

  `--file`                BIND config to upload.

   `-i, --instance INSTANCE_NAME`   Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' is used.

   `--output FORMAT`    Specify output format, only JSON is supported now.


## Export BIND config

**NAME**

   `dns-records-export` - Export BIND config.

**USAGE**

   `ibmcloud cis dns-records-export DNS_DOMAIN_ID [--file FILE] [-i, --instance INSTANCE_NAME]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.

**OPTIONS**

  `--file`                The BIND config saves exported DNS records..

   `-i, --instance INSTANCE_NAME`   Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' is used.

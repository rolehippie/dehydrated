# dehydrated

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/dehydrated) [![General Workflow](https://github.com/rolehippie/dehydrated/actions/workflows/general.yml/badge.svg)](https://github.com/rolehippie/dehydrated/actions/workflows/general.yml) [![Readme Workflow](https://github.com/rolehippie/dehydrated/actions/workflows/readme.yml/badge.svg)](https://github.com/rolehippie/dehydrated/actions/workflows/readme.yml) [![Galaxy Workflow](https://github.com/rolehippie/dehydrated/actions/workflows/galaxy.yml/badge.svg)](https://github.com/rolehippie/dehydrated/actions/workflows/galaxy.yml) [![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/dehydrated)](https://github.com/rolehippie/dehydrated/blob/master/LICENSE) [![Ansible Role](https://img.shields.io/ansible/role/57625)](https://galaxy.ansible.com/rolehippie/dehydrated)

Ansible role to install and configure dehydrated acme client.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of content

- [Default Variables](#default-variables)
  - [dehydrated_api](#dehydrated_api)
  - [dehydrated_api_version](#dehydrated_api_version)
  - [dehydrated_auto_cleanup](#dehydrated_auto_cleanup)
  - [dehydrated_ca_name](#dehydrated_ca_name)
  - [dehydrated_challenge_type](#dehydrated_challenge_type)
  - [dehydrated_contact_email](#dehydrated_contact_email)
  - [dehydrated_cron_command](#dehydrated_cron_command)
  - [dehydrated_cron_day](#dehydrated_cron_day)
  - [dehydrated_cron_hour](#dehydrated_cron_hour)
  - [dehydrated_cron_minute](#dehydrated_cron_minute)
  - [dehydrated_cron_month](#dehydrated_cron_month)
  - [dehydrated_cron_weekday](#dehydrated_cron_weekday)
  - [dehydrated_default_bundles](#dehydrated_default_bundles)
  - [dehydrated_dns_config](#dehydrated_dns_config)
  - [dehydrated_dns_provider](#dehydrated_dns_provider)
  - [dehydrated_download_url](#dehydrated_download_url)
  - [dehydrated_download_version](#dehydrated_download_version)
  - [dehydrated_extra_bundles](#dehydrated_extra_bundles)
  - [dehydrated_hook_chain](#dehydrated_hook_chain)
  - [dehydrated_ip_version](#dehydrated_ip_version)
  - [dehydrated_key_algo](#dehydrated_key_algo)
  - [dehydrated_key_size](#dehydrated_key_size)
  - [dehydrated_ocsp_days](#dehydrated_ocsp_days)
  - [dehydrated_ocsp_fetch](#dehydrated_ocsp_fetch)
  - [dehydrated_ocsp_must_staple](#dehydrated_ocsp_must_staple)
  - [dehydrated_preferred_chain](#dehydrated_preferred_chain)
  - [dehydrated_privatekey_renew](#dehydrated_privatekey_renew)
  - [dehydrated_privatekey_rollover](#dehydrated_privatekey_rollover)
  - [dehydrated_renew_days](#dehydrated_renew_days)
  - [dehydrated_request_certs](#dehydrated_request_certs)
  - [dehydrated_wellknown_path](#dehydrated_wellknown_path)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### dehydrated_api

Used acme api version

### dehydrated_api_version

#### Default value

```YAML
dehydrated_api_version: auto
```

### dehydrated_auto_cleanup

Enable automatic cleanup

#### Default value

```YAML
dehydrated_auto_cleanup: false
```

### dehydrated_ca_name

Name or aloas of the acme directory

#### Default value

```YAML
dehydrated_ca_name: letsencrypt
```

### dehydrated_challenge_type

Challenge type used for validating requests

#### Default value

```YAML
dehydrated_challenge_type: dns-01
```

### dehydrated_contact_email

Contact email for cert provider

#### Default value

```YAML
dehydrated_contact_email:
```

#### Example usage

```YAML
dehydrated_contact_email: hostmaster@example.com
```

### dehydrated_cron_command

Command executed by the cronjob

#### Default value

```YAML
dehydrated_cron_command: dehydrated --accept-terms --keep-going --cron
```

### dehydrated_cron_day

Day value for dehydrated cronjob

#### Default value

```YAML
dehydrated_cron_day: '*'
```

### dehydrated_cron_hour

Hour value for dehydrated cronjob

#### Default value

```YAML
dehydrated_cron_hour: '7'
```

### dehydrated_cron_minute

Minute value for dehydrated cronjob

#### Default value

```YAML
dehydrated_cron_minute: '0'
```

### dehydrated_cron_month

Month value for dehydrated cronjob

#### Default value

```YAML
dehydrated_cron_month: '*'
```

### dehydrated_cron_weekday

Weekday value for dehydrated cronjob

#### Default value

```YAML
dehydrated_cron_weekday: '*'
```

### dehydrated_default_bundles

List of default domain bundles to generate certs for

#### Default value

```YAML
dehydrated_default_bundles: []
```

#### Example usage

```YAML
dehydrated_default_bundles:
  - domain: example.com
    aliases:
      - foo.eaxample.com
      - bar.eaxample.com
      - baz.eaxample.com
  - name: service.example.com
    aliases:
      - '*.service.examples.com'
```

### dehydrated_dns_config

Optional configuration for dns providers

#### Default value

```YAML
dehydrated_dns_config: {}
```

#### Example usage

```YAML
dehydrated_dns_config:
  auth_client_id: REDACTED
  auth_client_secret: REDACTED
  auth_tenant_id: REDACTED
  auth_subscription_id: REDACTED
  resource_group: REDACTED
```

### dehydrated_dns_provider

Enable a dns provider supported by lexicon

#### Default value

```YAML
dehydrated_dns_provider:
```

### dehydrated_download_url

URL to the upstream script to download

#### Default value

```YAML
dehydrated_download_url: https://raw.githubusercontent.com/dehydrated-io/dehydrated/v{{
  dehydrated_download_version }}/dehydrated
```

### dehydrated_download_version

Version to download for installation

#### Default value

```YAML
dehydrated_download_version: 0.7.1
```

### dehydrated_extra_bundles

List of extra domain bundles to generate certs for

#### Default value

```YAML
dehydrated_extra_bundles: []
```

#### Example usage

```YAML
dehydrated_extra_bundles:
  - domain: example.com
    aliases:
      - foo.eaxample.com
      - bar.eaxample.com
      - baz.eaxample.com
  - name: service.example.com
    aliases:
      - '*.service.examples.com'
```

### dehydrated_hook_chain

Chain arguments together into one hook call per cert

#### Default value

```YAML
dehydrated_hook_chain: false
```

### dehydrated_ip_version

IP version used by dehydrated commands

#### Default value

```YAML
dehydrated_ip_version: 4
```

### dehydrated_key_algo

Used key algorithm

#### Default value

```YAML
dehydrated_key_algo: secp384r1
```

### dehydrated_key_size

Default key size for private keys

#### Default value

```YAML
dehydrated_key_size: 4096
```

### dehydrated_ocsp_days

Refresh interval for OCSP

#### Default value

```YAML
dehydrated_ocsp_days: 5
```

### dehydrated_ocsp_fetch

Fetch OCSP responses

#### Default value

```YAML
dehydrated_ocsp_fetch: false
```

### dehydrated_ocsp_must_staple

Option to add csr-flag indicating OCSP stapling to be mandatory

#### Default value

```YAML
dehydrated_ocsp_must_staple: false
```

### dehydrated_preferred_chain

Option preferred certificate chain

#### Default value

```YAML
dehydrated_preferred_chain:
```

### dehydrated_privatekey_renew

Regenerate private keys instead of just signing new certificates on renewal

#### Default value

```YAML
dehydrated_privatekey_renew: true
```

### dehydrated_privatekey_rollover

Create an extra private key for rollover

#### Default value

```YAML
dehydrated_privatekey_rollover: false
```

### dehydrated_renew_days

Minimum days before expiration to automatically renew certificate

#### Default value

```YAML
dehydrated_renew_days: 30
```

### dehydrated_request_certs

Request defined certs as part of playbook

#### Default value

```YAML
dehydrated_request_certs: false
```

### dehydrated_wellknown_path

Path used for http-01 challenges

#### Default value

```YAML
dehydrated_wellknown_path: ${BASEDIR}/challenges
```

## Discovered Tags

**_dehydrated_**


## Dependencies

- None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)

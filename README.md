# ansible-role-dns

Add DNS records to a DNS provider

## Connection Type

local

## Requirements

none

## Variables

1. secret variable from credentials\_[development/production].yml (e.g. credentials_development.yml)

```yaml
dns_provider: "cloudflare | route53"
cf_dns_api_token: "cloudflare api token"
route53_access_key: "aws access key"
route53_secret_key: "aws secret key"
```

2. variable from inventory.ini

```yaml
domain: "zone/url in DNS provider. put it in the inventory file."
raw_server: "ip address of server.put it in the inventory file."
```

3. variable from `extra_variable.yml`

```yaml
cred_env: "development | production"
dns_records:
  - { type: "A", sub_domain: "api", ip: "1.2.3.4" }
  - { type: "A", sub_domain: "doc" }
```

**_ dns_record may have ip in it _**

## Dependencies

credentials_development.yml or credentials_production.yml
`ansible-vault create credentials_development.yml` or `ansible-vault create credentials_production.yml`

put credentials's secret variable in file.

```bash
echo "password" > passwordfile
```

## Example Playbook

look at `tests/inventory.ini` and check domain.

`cd tests` and run the playbook with the following command:

```yaml
ansible-playbook -i inventory.ini test.yml --vault-password-file passwordfile --extra-vars "@extra_variable.yml"
```

## License

BSD

## Author Information

telegram: [@Qteam1](https://t.me/Qteam1)

# Useful CLI Commands for Plesk

## Subscription/Site Management

### Domain Aliases

To create a domain alias that only redirects to the main domain without creating
a new site, use the following `domalias` command:

```bash
plesk bin domalias --create aliasdomain.net -domain maindomain.net
```

See [domalias: Domain Aliases for more information](https://docs.plesk.com/en-US/onyx/cli-linux/using-command-line-utilities/domalias-domain-aliases.38962/).

## User Management

### Create an Additional Administrator

```bash
PSA_PASSWORD="$password" plesk bin admin_alias \
  --create $username \
  -passwd '' \
  -contact "$display_name" \
  -comment "$comment" \
  -email "$email"
```

See [admin_alias: Additional Administrator
Accounts](https://docs.plesk.com/en-US/obsidian/cli-linux/using-command-line-utilities/admin_alias-additional-administrator-accounts.72489/)
for more information.

## Server Configuration

### Disable TLSv1 and TLSv1.1

```bash
# /usr/local/psa/bin/server_pref -s | grep ssl-protocols
ssl-protocols: TLSv1 TLSv1.1 TLSv1.2 TLSv1.3

/usr/local/psa/bin/server_pref -u -ssl-protocols "TLSv1.2 TLSv1.3"

# /usr/local/psa/bin/server_pref -s | grep ssl-protocols
ssl-protocols: TLSv1.2 TLSv1.3

## Other Commands

### Fail2Ban Management

```bash
# Show list of trusted IPs
plesk bin ip_ban -t

# Add additional IPs to the trusted list
plesk bin ip_ban --add-trusted "1.2.3.4 5.6.7.8 9.10.11.12"

# Show list of banned IPs
plesk bin ip_ban -b

# Unban an IP
plesk bin ip_ban --unban 1.2.3.4
```

See [ip_ban: IP Address
Banning (Fail2Ban)](https://docs.plesk.com/en-US/obsidian/cli-linux/using-command-line-utilities/ip_ban-ip-address-banning-fail2ban.73594/)
for more information.

# certbot-godaddy


these scripts are for use with certbot manual hooks, for multiple SANs or even MULTIPLE Wildcards. 
These scripts work with python 3 only. 



## USAGE
Get your API key from https://developer.godaddy.com
and either create an ini file located next to validation.py and cleanup.py with the following 
```
[default]
api_key=<APIKEY>
api_secret=<APISECRET>
```

or export the following env vars before running certbot script
```

export GODADDY_API_SECRET=<APIKEY>
export GODADDY_API_KEY=<API_SECRET>
```


## Example
```
cd /directory/with/certbot-godaddy

#example single domain
certbot certonly --manual --preferred-challenges=dns --email=john.doe@example.com --agree-tos --manual-public-ip-logging-ok --manual-auth-hook ./validation.py --manual-cleanup-hook ./cleanup.py -d "testing-certbot.example.com" --dry-run

#example SAN
certbot certonly --manual --preferred-challenges=dns --email=john.doe@example.com --agree-tos --manual-public-ip-logging-ok --manual-auth-hook ./validation.py --manual-cleanup-hook ./cleanup.py -d "testing-certbot.example.com" -d "testing-certbot2.example.com" --dry-run

#example WildCard

certbot certonly --manual --preferred-challenges=dns --email=john.doe@example.com --agree-tos --manual-public-ip-logging-ok --manual-auth-hook ./validation.py --manual-cleanup-hook ./cleanup.py -d "*.example.com" --dry-run

#example WildCard subdomain
certbot certonly --manual --preferred-challenges=dns --email=john.doe@example.com --agree-tos --manual-public-ip-logging-ok --manual-auth-hook ./validation.py --manual-cleanup-hook ./cleanup.py -d "*.testing-certbot.example.com" --dry-run

#example Multiple wildcard
certbot certonly --manual --preferred-challenges=dns --email=john.doe@example.com --agree-tos --manual-public-ip-logging-ok --manual-auth-hook ./validation.py --manual-cleanup-hook ./cleanup.py -d "*.testing-certbot.example.com" -d "*.testing-certbot2.example.com" --dry-run

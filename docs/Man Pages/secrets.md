```
% clamity secrets help
/Users/jj/.clamity/pyvenv/bin/python3 /Users/jj/src/clamity-toolbox/clamity/cmds/secrets.py help
usage: 
    clamity secrets { list | help }
    clamity secrets write --name secret/path/and/name --desc "useful desc" --value "supersecret"
    clamity secrets write --name secret/path/and/name --desc "useful desc" \
                          --type <known-type> --value '{"prop1": "val", "prop2": "val2", ...}'
    clamity secrets { read | details | delete } --name secret/path/and/name
    clamity secrets update --name secret/path/and/name [--desc "updated desc"] [[--type <known-type>] --value "secret-data"]

Manage data in the secrets store (AWS secretsmanager)

synopsis:

    CLI for managing data in AWS secrets manager. Also provides an integration with a
    secrets schema to ensure data is stored in standard locations for tying into CI/CD
    pipelines.

positional arguments:
  {list,types,delete,update,write,read,details,restore,help}
                        action to take

options:
  -h, --help            show this help message and exit
  -d, --debug           debug output
  -v, --verbose         verbose output
  -q, --quiet           surpress output
  -n, --dryrun          dryrun - won't mutate
  -y, --yes             disable interactive prompts in the affirmative
  -of {json,text,csv}, --output-format {json,text,csv}
                        json, text (default) or csv
  --no-truncate         don't truncate column widths
  --no-header           don't display column headers
  --aws-region AWS_REGION
                        AWS region (eg. us-east-1)
  --desc DESC           useful description of the secret (possibly a URL)
  --name NAME           secret's path and name (secret store key)
  --value VALUE         the secret's value
  --type {ssh_key,rds_mysql}
                        add secret validation

actions:

    delete   Delete secrets from the secrets store
    details  Display the AWS API response (in JSON) for secret details
    help     Full help
    list     List the secrets
    read     Return the value of a secret
    update   Update a secret's description or value
    write    Add new secrets to the secrets store

standard storage conventions:

    Secret names follow conventions to integration with IAM policies and CI/CD
    pipelines (such as terraform). They're categorized accordingly. A search
    path is typically used in development to accomodate developers who have
    more restricted write capabilities. The search path defaults to ['devs/', ''].
    Developers can write to 'certs/devs/...', 'secrets/devs/...', etc... but
    can read from the larger scope of 'certs/...', 'secrets/...'.

    TLS Certificates:
        certs/[search-path]<domainName>/{key|crt|ca}

    Secrets for services:
        services/[search-path]<serviceName>/<app-env>/<secretName>

    SSH Keys for services:
        services/[search-path]<serviceName>/<app-env>/ssh-keys/<keyName>/{public|private}

    Providers:
        providers/[search-path]<providerName>/<app-env>/<provider-specific-organization>

    Individual users' secrets:
        users/<aws-user-id>/<anything>

    Individual users' ssh keys:
        users/<aws-user-id>/ssh-keys/<keyName>/{public|private}

examples:
    Need some examples here.
```

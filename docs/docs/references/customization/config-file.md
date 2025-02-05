# Config file

Trivy can be customized by tweaking a `trivy.yaml` file. The config path can be overridden by the `--config` flag.

An example is [here][example].

## Global Options

```
# Same as '--quiet'
# Default is false
quiet: false

# Same as '--debug'
# Default is false
debug: false

# Same as '--insecure'
# Default is false
insecure: false

# Same as '--timeout'
# Default is '5m'
timeout: 10m

# Same as '--cache-dir'
# Default is your system cache dir
cache-dir: $HOME/.cache/trivy
```

## Report Options

```
# Same as '--format'
# Default is 'table'
format: table

# Same as '--report' (available with 'trivy k8s')
# Default is all
report: all

# Same as '--template'
# Default is empty
template: 

# Same as '--dependency-tree'
# Default is false
dependency-tree: false

# Same as '--list-all-pkgs'
# Default is false
list-all-pkgs: false

# Same as '--ignorefile'
# Default is '.trivyignore'
ignorefile: .trivyignore

# Same as '--ignore-policy'
# Default is empty
ignore-policy:

# Same as '--exit-code'
# Default is 0
exit-code: 0

# Same as '--output'
# Default is empty (stdout)
output:

# Same as '--severity'
# Default is all severities
severity:
  - UNKNOWN
  - LOW
  - MEDIUM
  - HIGH
  - CRITICAL
```

## Scan Options
Available in client/server mode

```
scan:
  # Same as '--skip-dirs'
  # Default is empty
  skip-dirs:
    - usr/local/
    - etc/
  
  # Same as '--skip-files'
  # Default is empty
  skip-files:
    - package-dev.json
  
  # Same as '--offline-scan'
  # Default is false
  offline-scan: false
  
  # Same as '--security-checks'
  # Default depends on subcommand
  security-checks:
    - vuln
    - config
    - secret
```

## Cache Options

```
cache:
  # Same as '--cache-backend'
  # Default is 'fs' 
  backend: 'fs'
  
  # Same as '--cache-ttl'
  # Default is 0 (no ttl) 
  ttl: 0
  
  # Redis options
  redis:
    # Same as '--redis-ca'
    # Default is empty
    ca:
    
    # Same as '--redis-cert'
    # Default is empty
    cert:
    
    # Same as '--redis-key'
    # Default is empty
    key:
```

## DB Options

```
db:
  # Same as '--skip-db-update'
  # Default is false
  skip-update: false
  
  # Same as '--no-progress'
  # Default is false
  no-progress: false
  
  # Same as '--db-repository'
  # Default is 'github.com/aquasecurity-trivy-repo'
  repository: github.com/aquasecurity-trivy-repo
```

## Image Options
Available with container image scanning

```
image:
  # Same as '--input' (available with 'trivy image')
  # Default is empty
  input:
  
  # Same as '--removed-pkgs'
  # Default is false
  removed-pkgs: false
```

## Vulnerability Options
Available with vulnerability scanning

```
vulnerability:
  # Same as '--vuln-type'
  # Default is 'os,library'
  type:
    - os
    - library
  
  # Same as '--ignore-unfixed'
  # Default is false
  ignore-unfixed: false
```

## Secret Options
Available with secret scanning

```
secret:
  # Same as '--secret-config'
  # Default is 'trivy-secret.yaml'
  config: config/trivy/secret.yaml
```


## Misconfiguration Options
Available with misconfiguration scanning

```
misconfiguration:
  # Same as '--file-patterns'
  # Default is empty
  file-patterns:
    -
  
  # Same as '--include-non-failures'
  # Default is false
  include-non-failures: false
  
  # Same as '--trace'
  # Default is false
  trace: false
  
  # Same as '--config-policy'
  # Default is empty
  policy:
    - policy/repository
    - policy/custom
    
  # Same as '--config-data'
  # Default is empty
  data:
    - data/
    
  # Same as '--policy-namespaces'
  # Default is empty
  namespaces:
    - opa.examples
    - users
```

## Kubernetes Options
Available with Kubernetes scanning

```
kubernetes:
  # Same as '--context'
  # Default is empty
  context:
  
  # Same as '--namespace'
  # Default is empty
  namespace:
```

## Client/Server Options
Available in client/server mode

```
server:
  # Same as '--server' (available in client mode)
  # Default is empty
  addr: http://localhost:4954
  
  # Same as '--token'
  # Default is empty
  token: "something-secret"
  
  # Same as '--token-header'
  # Default is 'Trivy-Token'
  token-header: 'My-Token-Header'
  
  # Same as '--custom-headers'
  # Default is empty
  custom-headers:
    - scanner: trivy
    - x-api-token: xxx
    
  # Same as '--listen' (available in server mode)
  # Default is 'localhost:4954'
  listen: 0.0.0.0:10000
```

[example]: https://github.com/aquasecurity/trivy/tree/{{ git.tag }}/examples/trivy-conf/trivy.yaml

<div align="center">

# Kipinä ⚡

*Transform monitoring into code. Light the first spark of awareness for your services.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Go Version](https://img.shields.io/github/go-mod/go-version/bashhack/kipina)](https://go.dev)
[![Release](https://img.shields.io/github/v/release/bashhack/kipina?include_prereleases)](https://github.com/bashhack/kipina/releases)

</div>

---

## Monitor Like You Code

Kipinä brings infrastructure-as-code to service monitoring. From localhost to production, manage your monitoring through code, CLI, and a powerful web interface.

```yaml
# services.yaml
services:
  - name: API Gateway
    url: api.example.com
    checks:
      - type: http
        interval: 30s
        match: '"status": "healthy"'
    alerts:
      - type: slack
        channel: #incidents

  - name: Payment Service
    url: payments.internal
    checks:
      - type: tcp
        port: 9000
      - type: ssl
        warn_days: 14

```

``` bash
# Apply your configuration
kipina apply services.yaml

# Watch deployment in real-time
kipina watch --wait-for-ready
```


## ⚡ Quick Start

``` bash
# Install CLI
brew install kipina

# Start monitoring
kipina watch api.example.com

# Your monitoring is now active:
# └─ CLI: Local checks running
# └─ Web: https://app.kipina.dev/dashboard

```

## 🔥 Why Kipinä?

* **Developer-First**: Monitor through code, CLI, and git
* **Hybrid Power**: Local CLI + Cloud dashboard
* **CI/CD Ready**: Native pipeline integration
* **Complete Coverage**: From localhost to production

## 🌟 Core Features

### Local Development

Monitor your services during development:

```bash
# Watch local services
kipina watch localhost:3000 --dev

# Monitor microservices
kipina watch -f docker-compose.yaml

# Quick SSL check
kipina check ssl example.com
```

### CI/CD Integration

Verify deployments automatically:

```yaml
# GitHub Actions
steps:
  - name: Health Check
    run: |
      kipina watch $DEPLOY_URL \
        --wait-for 200 \
        --timeout 5m \
        --match "Ready"
```
        
### Infrastructure as Code

Manage monitoring through version control:

```bash
# Apply monitoring config
kipina apply -f monitoring.yaml

# View status
kipina status

# Update checks
kipina update api --interval 15s
```

### Private Infrastructure

Monitor internal services securely:

```bash
# Internal services
kipina watch internal-api:8080 \
  --private \
  --report-to cloud

# VPC resources
kipina watch vpc-endpoint \
  --region us-east-1 \
  --private
```

## 📦 Installation

``` bash
# Homebrew (macOS & Linux)
brew install kipina

# Direct download
curl -L https://get.kipina.dev | sh

# Docker
docker run kipina/cli watch example.com
```

## ⚙️ Configuration

```yaml
# ~/.kipina.yaml
monitoring:
  interval: 30s
  regions: ["us-east-1", "eu-west-1"]
  private_key: ~/.ssh/kipina

alerts:
  channels:
    slack: https://hooks.slack.com/...
    email: alerts@example.com

status_page:
  title: "Service Status"
  public: true
```

## 🔌 Integration Examples

### Kubernetes

```yaml
apiVersion: monitoring.kipina.dev/v1
kind: ServiceMonitor
metadata:
  name: api-monitor
spec:
  selector:
    matchLabels:
      app: api
  checks:
    - http:
        path: /health
        interval: 30s
```

### Docker Compose

```yaml
services:
  monitor:
    image: kipina/agent
    volumes:
      - ./kipina.yaml:/etc/kipina/config.yaml
    environment:
      KIPINA_TOKEN: ${KIPINA_TOKEN}
```

### Terraform

```hcl
resource "kipina_monitor" "api" {
  name    = "API Monitor"
  url     = aws_alb.api.dns_name
  region  = var.aws_region
  
  check {
    type     = "http"
    interval = "30s"
    match    = "healthy"
  }
}
```

## 📊 Dashboard Access

Free dashboard includes:
* Basic status monitoring
* 24-hour history
* Single user access
* Up to 5 monitors
* 60s check intervals

View your dashboard at https://app.kipina.dev/dashboard

## 🌟 Pro Features

Upgrade to Kipinä Pro:

* 📊 Multi-region monitoring
* 🔒 Private network support
* 👥 Team collaboration and sharing
* 🔧 Custom check types
* 🔗 Full API access
* 📈 30-day history
* ⚡ 30s check intervals
* 💾 Unlimited monitors

[Learn More](https://kipina.pro)

## 🏢 Enterprise Features

Contact us for:
* 🌐 Custom retention periods
* 🔐 SSO integration
* 📞 Priority support
* 🛡️ Custom SLAs
* 🏗️ On-premise deployment

[Contact Sales](https://kipina.dev/enterprise)

## 📜 License

Kipinä's core functionality is available under the MIT License. See the [LICENSE](LICENSE) file for details.

Pro features require a commercial license:

 * [Commercial License](https://kipina.dev/license)
 * [Feature Comparison](https://kipina.dev/compare)
 * [Contact Sales](https://kipina.dev/enterprise)

<hr />

<div align="center">

*"Monitor like you code - with precision, automation, and grace."*

Made with ❤️ by bashhack.
</div>

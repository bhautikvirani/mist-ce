# mist-ce

Managing machines across public clouds, private infrastructure and container hosts means switching between provider-specific tools. mist-ce brings resource visibility and common lifecycle operations into one interface, with a REST API for integration into existing workflows.

## Features

- View resources across connected infrastructure providers and group them by tags.
- Provision machines, volumes and networks on supported providers; start, stop, reboot or resize existing machines.
- Run scripts and open SSH sessions on machines through the browser or CLI, with centralized SSH key management and audit logging.
- Monitor system and custom metrics, and configure rules that trigger notifications, webhooks, scripts or lifecycle actions.
- Schedule scripts and machine lifecycle actions.
- Estimate current infrastructure costs across connected providers.

Provider support determines which operations are available for each resource.

## Installation

mist-ce is based on a Python application packaged as Docker microservices. It supports deployment on a single host with Docker Compose or on Kubernetes with Helm.

**This is a multi-service application, not a standalone Python CLI.** A Python virtual environment does not replace the container deployment.

For Python-side development, create an isolated environment from the repository root:

```sh
python3 -m venv .venv
. .venv/bin/activate
python -m pip install --upgrade pip
```

Install Docker Engine and the Docker Compose plugin for a single-host deployment. Use the deployment configuration supplied with your checkout and review its required environment settings before starting services. The provided donor excerpt does not specify dependency files, service ports or configuration values, so those details must come from the checkout's deployment documentation.

## Usage

From the directory containing the configured Compose file, validate it and start the deployment under the project name `mist-ce`:

```sh
docker compose -p mist-ce config
docker compose -p mist-ce up -d
```

Check service status and inspect logs:

```sh
docker compose -p mist-ce ps
docker compose -p mist-ce logs --tail=100
```

Open the web interface at the address configured by your deployment. Connect an infrastructure provider to inspect its resources, then select a machine to perform a supported lifecycle action.

The upstream project also documents a [REST API](https://mist.io/api/v2) and a separate [CLI](https://github.com/mistio/mist-cli). Check their compatibility with your deployment before use.

## License

mist-ce is licensed under Apache-2.0 and is based on [mistio/mist-ce](https://github.com/mistio/mist-ce). Preserve applicable upstream copyright notices, the license text and any required NOTICE content when redistributing the code.

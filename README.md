# insomnia-issue-4425

Investigating insomnia-issue-4425

## Prerequisites

- [Docker](https://docs.docker.com/engine/install/)
- [DecK](https://github.com/Kong/deck) (for Kong Configuration management)
- [Insomnia](https://github.com/Kong/insomnia/releases) (use version `2022.3.0` and up)

## Setup

Run `inso` to generate kong declarative config:

```bash
inso generate config --src . "issue-4425" -t declarative -f json > kong.json
```

Run Kong Gateway (and needed containers):

```bash
make build
```

Apply configuration to Kong Gateway:

```bash
deck sync -s kong.json
```

> To clean up containers run `make clean`

## Other

### Troubleshooting

- To check connection between [DecK](https://github.com/Kong/deck) and your local Kong instance: `deck ping`

### Useful documentation

- [Installing and running Kong Gateway OSS using Docker](https://docs.konghq.com/gateway/latest/install-and-run/docker/);

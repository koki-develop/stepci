# Integrating with Docker

Create example workflow

**tests/workflow.yml**

```yaml
version: "1.1"
name: Status Check
env:
  host: example.com
tests:
  example:
    steps:
      - name: GET request
        http:
          url: https://${{env.host}}
          method: GET
          check:
            status: /^20/
```

Run your workflow using the [official Docker image](https://github.com/stepci/stepci/pkgs/container/stepci)

```
docker run -v "$(pwd)"/tests:/tests ghcr.io/stepci/stepci tests/workflow.yml
```

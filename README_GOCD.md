# Run GoCD locally

## Start a GoCD server

```
docker run --name angry_feynman -d -p8153:8153 -p8154:8154 gocd/gocd-server:v19.1.0

```

### Ensure the server is up by navigating to [http://localhost:8153](http://localhost:8153)

## Start a GoCD agent

1. Start a container

```
docker run -d -e GO_SERVER_URL=https://$(docker inspect --format='{{(index (index .NetworkSettings.IPAddress))}}' angry_feynman):8154/go gocd/gocd-agent-ubuntu-18.04:v19.2.0

```

2. Ensure the Agent has registered with the server by navigating to [http://localhost:8153/go/agents](http://localhost:8153/go/agents#!/agentState/asc/)

3. Enable the Agent by clicking the checkbox next to the instance name and selecting the "ENABLE" button

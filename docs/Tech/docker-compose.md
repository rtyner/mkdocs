# Docker Compose Notes

<https://dockerswarm.rocks/>
<https://docs.docker.com/engine/swarm/>
<https://geek-cookbook.funkypenguin.co.nz/ha-docker-swarm/design/>
<https://www.smarthomebeginner.com/traefik-2-docker-tutorial/>
<https://www.youtube.com/watch?v=3c-iBn73dDE>
<https://www.youtube.com/c/TechWorldwithNana/videos>

### what is docker swarm

- clustered node of of docker hosts with distributed manager nodes to provide fault tolerance

| **Hostname**                    | **IP**       | **Description**      |
| ------------------------------- | ------------ | -------------------- |
| prod-docker-mgr1.rtynerlabs.io  | 192.168.1.25 | docker swarm manager |
| prod-docker-node1.rtynerlabs.io | 192.168.1.26 | docker swarm node 1  |
| prod-docker-node2.rtynerlabs.io | 192.168.1.27 | docker swarm node 1  |

| **Hostname**    | **IP**          | **Description**      |
| --------------- | --------------- | -------------------- |
| do-docker-mgr1  | 137.184.58.157  | docker swarm manager |
| do-docker-node1 | 143.198.189.109 | docker swarm node 1  |
| do-docker-node2 | 167.99.232.2    | docker swarm node 2  |

`docker swarm init --advertise-addr 192.168.1.25`

output from docker manager showing that some nodes are now rejected

`rt@prod-dock-hf01:~$ docker service ps --no-trunc swarmpit_agent`

ID NAME IMAGE NODE DESIRED STATE CURRENT STATE ERROR PORTS

```ktu9gbsy1a7gjwzjqwfvzaxij \_ swarmpit_agent.hojfizog23pbdyr3iifdbsb2s swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-1 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

456q110qfrxxxuhgdbe4uc4yt \_ swarmpit_agent.hojfizog23pbdyr3iifdbsb2s swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-1 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

s6u35v26dvjqoozq73ykvk736 \_ swarmpit_agent.nymh0inei5jhk3fmxo4v59l9x swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-node1 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

gg9h62jjb4a2tde5jim8skn0s \_ swarmpit_agent.nymh0inei5jhk3fmxo4v59l9x swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-node1 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

pe0501ao1e3w6plwipjpt5e0r \_ swarmpit_agent.ya3ugvz4d9nsk1gcpeo4vhdlg swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-node3 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

lwdywux7by2mckayqhdpzqcmo \_ swarmpit_agent.ya3ugvz4d9nsk1gcpeo4vhdlg swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-node3 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

h7rt5dkwxa03u0pqubiwhw3h7 \_ swarmpit_agent.zlpebejmbatxvsfkq7clz9990 swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-2 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"

qctyh7tieuc8hdbr890o0agw4 \_ swarmpit_agent.zlpebejmbatxvsfkq7clz9990 swarmpit/agent:latest@sha256:f92ba65f7923794d43ebffc88fbd49bfe8cde8db48ca6888ece5747b9ab1375c prod-docker-2 Shutdown Rejected 18 hours ago "assigned node no longer meets constraints"
```

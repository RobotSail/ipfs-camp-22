<h1 align="center">Mastering the Chaos: What K8s Operators do that other deployments do not</h1>
<h3 align="center">By Oleg Silkin (<a href="https://github.com/robotsail">@RobotSail</a>)</h3>
 
<p align="center">
This repository contains scripts and code which was presented at IPFS Camp 2022 in Lisbon.
</p>

<h2>Outline</h2>

<h3>Demo 1: Deploying IPFS in Kubernetes</h3>

1. Create a simple IPFS Pod with the label `name=my-ipfs-node`.
1. Create a service of type LoadBalancer to expose the IPFS node's WebUI. This Service must match pods with the label `name=my-ipfs-node`.
1. Create a PVC named `ipfs-data`.
1. Attach the `ipfs-data` PVC as a `Volume`.
1. Have the Kubo container mount `ipfs-data` at `/data/ipfs`.
1. Generate a base64-encoded IPFS Swarm key by running `./scripts/generate-swarm-key.sh | base64`
1. Place the swarm key into a new secret titled `ipfs-secret`
1. Mount the swarm key as the environment variable `IPFS_SWARM_KEY` in the IPFS Pod


<h3>Demo 2: Scaling our IPFS Network</h3>

1. Convert the Pod into a Deployment
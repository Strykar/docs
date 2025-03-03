---
title: Connect an Orchestrator with Separate Transcoders
---

# Connect an orchestrator with separate transcoders

## Pre-requisites

- Make sure you have
  [activated your orchestrator](/video-miners/getting-started/activation)

## Run a standalone orchestrator

```bash
livepeer \
    -network mainnet \
    -ethURL <ETH_URL> \
    -orchestrator \
    -orchSecret <ORCH_SECRET> \
    -pricePerUnit <PRICE_PER_UNIT> \
    -serviceAddr <SERVICE_ADDR>
```

- `-orchSecret` is used to specify a secret that transcoders can use to connect
  with the orchestrator. The secret can be provided in plaintext or via a file
  (recommended) i.e. `-orchSecret secret.txt`

## Run a standalone transcoder

The following instructions assume that the transcoder is run on a separate
machine from the orchestrator. These instructions can be used to connect as many
transcoders as you want to the orchestrator.

```bash
livepeer -transcoder \
	-nvidia <NVIDIA_GPU_IDs> \ # Only required for transcoding with Nvidia GPUs
	-orchSecret <ORCH_SECRET> \
	-orchAddr <SERVICE_ADDR>
```

- The value for `-orchSecret` should be the same as the value used for your
  orchestrator
- `-orchAddr` is used to specify the publicly accessible address that the
  orchestrator is receiving transcoder registration requests at

On startup, the transcoder will automatically run a test to confirm that it is
able to transcode using the specified GPUs. The transcoder will exit if this
test fails. If the test passes, you should see the following message in the log
output without any additional error messages following it indicating that your
transcoder successfully connected with the orchestrator:

```bash
Registering transcoder to my-orchestrator.com:443
```

When the orchestrator receives a connection from a transcoder, you will see a
message in the orchestrator logs that looks like:

```bash
Got a RegisterTranscoder request from transcoder=10.3.27.1 capacity=10
```

The `transcoder` field indicates the IP of the connecting transcoder and the
`capacity` field indicates the number of simultaneous transcoding jobs that the
transcoder can handle. Once the orchestrator has at least one transcoder
connected, it will be able to send transcoding jobs to the transcoder when it
receives a stream from a broadcaster.

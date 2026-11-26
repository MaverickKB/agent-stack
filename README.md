# agent-stack

Run it yourself or rent it. This is the recipe for the whole thing, and every piece is a real public repo you can clone today.

You do not need a third-party app to sit between you and your coding agents. You do not need someone else deciding which models you run, where your prompts go, or what gets phoned home. You can own the entire stack. This repo is the one stop shop: the map of how the pieces fit, and a pointer to each one.

There is no drama here and no fork war. Just a working stack, built independently, and shipped in public.

## The recipe

Seven layers. Each maps to one or more of the repos below.

### 1. Local inference

Run open models on GPUs you own, without a datacenter.

- **TensorFold** is the engine: Metal, CUDA, Vulkan.
- **qwen38-27b-262k-16gb-tensorfold** and **qwen38-27b-262k-16gb-exl3** are the proof of the ceiling: Qwen 3.8 27B at the full 262,144-token context on a 16GB card.
- **GLM-5.3-Flash-DGX-Sparks-1104** is the high-end lane on a pair of DGX Sparks.
- **sparkDash** watches the serving boxes.

### 2. The gateway

One OpenAI-compatible endpoint in front of every engine.

- **model-router** routes to local and cloud engines, queues per engine instead of dropping work, falls back when an engine is sick, and runs a watchdog that stops a response that loops or stalls. It counts tokens per principal so budgets work before any limit is turned on, gates access by origin, and captures debug payloads only when an operator opts in.

### 3. The agent runtime

One place that holds the session, the tools, and the fanout.

- **hermes-agent-upstream** is the agent.
- **hermes-webui** is the same agent from a browser or a phone.
- **hermes-advanced-profile-manager** gives you full control over profiles, skills, providers, and delegation.
- **ash-skills-hermes-adapt** carries the skill set.

### 4. Companions and harnesses

- **Goblin-agent-for-Mac** and **Goblin-for-Linux** are native companions running local models.
- **Tessera-CT** is a desktop harness with AetherMind memory baked in.

### 5. Continuity and identity

The moat. Whoever holds the agent's memory holds the relationship, so hold it yourself.

- **aethermind** and **aethermind-engine** are project-local, append-only continuity layers.
- **aethermind-primitive** is the harness-free version.
- **aethermind-hermes-plugin** wires it into Hermes.
- **aethermind-first-benchmark-proof** is the redacted benchmark packet, so the claim has receipts.
- **cairn** is the map for building an identity that persists across models and machines without belonging to any vendor.

### 6. Voice

- **VoiceStudio** is a fully local alternative for voice cloning, design, dubbing, dictation, and audiobooks.

### 7. Live model editing (research)

Teaching a serving model new facts without touching its weights, because local inference is only the start.

- **moe-live-learning-tools**
- **tensor-parallel-side-jobs**
- **live-serving-expert-training**
- **glm-moe-viewer3d** for reading MoE routing traces.

## All the repositories

| Repo | What it is |
| --- | --- |
| [TensorFold](https://github.com/MaverickKB/TensorFold) | LLM inference engine, Metal / CUDA / Vulkan |
| [model-router](https://github.com/MaverickKB/model-router) | OpenAI-compatible router and operator console |
| [hermes-agent-upstream](https://github.com/MaverickKB/hermes-agent-upstream) | The agent runtime |
| [hermes-webui](https://github.com/MaverickKB/hermes-webui) | Hermes from the web or your phone |
| [hermes-advanced-profile-manager](https://github.com/MaverickKB/hermes-advanced-profile-manager) | Local profile and delegation control |
| [ash-skills-hermes-adapt](https://github.com/MaverickKB/ash-skills-hermes-adapt) | Hermes adaptation of the skill set |
| [Goblin-agent-for-Mac](https://github.com/MaverickKB/Goblin-agent-for-Mac) | Native Mac companion, local models |
| [Goblin-for-Linux](https://github.com/MaverickKB/Goblin-for-Linux) | Native Linux companion, local models |
| [Tessera-CT](https://github.com/MaverickKB/Tessera-CT) | Desktop harness with AetherMind memory |
| [aethermind](https://github.com/MaverickKB/aethermind) | Continuity layers for every model and session |
| [aethermind-engine](https://github.com/MaverickKB/aethermind-engine) | Project-local append-only continuity layers |
| [aethermind-primitive](https://github.com/MaverickKB/aethermind-primitive) | Harness-free continuity primitive |
| [aethermind-hermes-plugin](https://github.com/MaverickKB/aethermind-hermes-plugin) | AetherMind reference Hermes plugin |
| [aethermind-first-benchmark-proof](https://github.com/MaverickKB/aethermind-first-benchmark-proof) | Redacted benchmark proof packet |
| [cairn](https://github.com/MaverickKB/cairn) | The map for building an identity that persists |
| [VoiceStudio](https://github.com/MaverickKB/VoiceStudio) | Fully local voice clone, dub, transcribe, audiobooks |
| [sparkDash](https://github.com/MaverickKB/sparkDash) | Multi-DGX Spark monitoring dashboard |
| [GLM-5.3-Flash-DGX-Sparks-1104](https://github.com/MaverickKB/GLM-5.3-Flash-DGX-Sparks-1104) | GLM 5.3 Flash on DGX Sparks, TensorFold |
| [qwen38-27b-262k-16gb-tensorfold](https://github.com/MaverickKB/qwen38-27b-262k-16gb-tensorfold) | Qwen 3.8 27B at 262k context on 16GB |
| [qwen38-27b-262k-16gb-exl3](https://github.com/MaverickKB/qwen38-27b-262k-16gb-exl3) | Qwen 3.8 27B at 262k context, EXL3 |
| [moe-live-learning-tools](https://github.com/MaverickKB/moe-live-learning-tools) | Teach an MoE model new facts in live serving |
| [tensor-parallel-side-jobs](https://github.com/MaverickKB/tensor-parallel-side-jobs) | Side jobs in a live tensor-parallel server |
| [live-serving-expert-training](https://github.com/MaverickKB/live-serving-expert-training) | Added experts inside a live MoE server |
| [glm-moe-viewer3d](https://github.com/MaverickKB/glm-moe-viewer3d) | 3D viewer for GLM MoE routing traces |
| [glm-rsi-dream](https://github.com/MaverickKB/glm-rsi-dream) | Experimental learned attention-memory loop |
| [game-theoretic-council-skill](https://github.com/MaverickKB/game-theoretic-council-skill) | Hermes skill for council decision review |
| [wakeword-bridge](https://github.com/MaverickKB/wakeword-bridge) | UDP bridge to Wyoming OpenWakeWord |
| [omarchy-chuck-yeager-nix64](https://github.com/MaverickKB/omarchy-chuck-yeager-nix64) | A user disk on Omarchy with Nix64 |

Each repo carries its own license. This repo is an index and a map; the text here is free to reuse.

## The three properties

This competes on three things an app cannot give you.

1. **No dial-home.** Payloads, logs, and config stay on your hardware. The only outbound traffic is a cloud model you picked.
2. **No lock-in.** Every layer is a replaceable service. Swap the engine, the router holds. Swap the agent, continuity still answers. You can read all of it, so you can fork any of it.
3. **No mystery.** The watchdogs, the accounting, and the access policy are code you can audit, not features behind a sign-in.

## Start here

New to the stack? This is the shortest path that leaves you owning everything:

1. Pick a card and clone a serving recipe (start with the Qwen 262k one if you are on a single consumer card).
2. Put **model-router** in front of it and point one `auto` route at your own box.
3. Run **Hermes** against the router endpoint. You now have the watchdog, the accounting, and the model choice on every agent call.
4. Add **aethermind** beside your projects so continuity stops living in a third party.
5. Open **hermes-webui** on your tailnet when you want it from your phone.

That is the whole loop. No app in the middle, nothing phoning home, and every line of it already public.

# AGENTS.md

## What this repo is

`agent-stack` is an index and a map, not a codebase. There is no runtime here. Its single job is to point at the repositories that make up the stack and to describe how they fit together.

Do not add code to this repo. If a component needs a change, make the change in the component's own repository, then update the relevant line in `README.md` only.

## The stack, one line each

- **TensorFold**: inference engine (Metal / CUDA / Vulkan).
- **model-router**: the OpenAI-compatible gateway: routing, per-engine queues, fallback, runaway watchdog, per-principal token accounting, origin policy, telemetry, operator debug capture. This is the operational heart.
- **hermes-agent-upstream**: the agent runtime with subagent delegation.
- **hermes-webui**: the browser and phone surface.
- **hermes-advanced-profile-manager**: profile, skills, provider, and delegation control.
- **ash-skills-hermes-adapt**: the skill set as a Hermes adaptation.
- **Goblin-agent-for-Mac**, **Goblin-for-Linux**: native local-model companions.
- **Tessera-CT**: desktop harness with AetherMind memory.
- **aethermind**, **aethermind-engine**, **aethermind-primitive**, **aethermind-hermes-plugin**: project-local append-only continuity.
- **cairn**: the identity map: a thread that persists across models and hosts.
- **VoiceStudio**: fully local voice.
- **sparkDash**, **GLM-5.3-Flash-DGX-Sparks-1104**, **qwen38-27b-262k-16gb-tensorfold**, **qwen38-27b-262k-16gb-exl3**: serving and monitoring.
- **moe-live-learning-tools**, **tensor-parallel-side-jobs**, **live-serving-expert-training**, **glm-moe-viewer3d**: live model editing research.

## Where each concern lives

- Routing, admission, watchdogs, accounting, origins: `model-router`.
- Model serving and recipes: the TensorFold and qwen/GLM serving repos.
- Agent behavior and tools: `hermes-agent-upstream` and the skill repos.
- Continuity and memory: `aethermind*`.
- Identity that spans hosts and vendors: `cairn`.

## Rules that apply everywhere in this stack

- Sterility. No hostnames, IPs, account emails, customer names, or secrets belong in any public repo. `state/`, `*.key`, `*.db`, and `.env` are gitignored. Sanitize before publishing.
- Local and public stay in sync. When a feature is built, push it. When a fix exists on the public repo, apply it to the live tree. Do not leave the two to diverge.
- Each repo carries its own license. Respect it.

## Things to keep accurate here

If a repo is added, removed, or renamed, update the table in `README.md` so this index stays the single source of truth for the stack.

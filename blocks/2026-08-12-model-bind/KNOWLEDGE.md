# KNOWLEDGE — Model bind

## Existing pieces
- forge/fabric/bind/openvino_seat.py — NPU brain (observe/judge only)
- forge/fabric/bind/ollama_capsule.py — RTX capsule via local Ollama
- ForgeKernel already accepts seat= in constructor and boot_forge
- HeuristicSeat is the current default fallback

## Intent
Wire one real seat so the “unconcerned” observe-only brain is live. Keep it advisory only.

## Discarded material
Any previous incomplete bind attempts are discarded. Build on the living bind/ files.

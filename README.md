# pod-attack

A pared-down Kubernetes control plane in Rust (`krust`), adversarially tested by a Go simulation harness (`dist-sim`).

## Why?

1. Sims are cool
2. I want to understand how Kubernetes works internally
3. I want to learn Rust and get better at Go

## Structure

```
rust/          # Rust workspace
  raft/        # Phase 1: Raft consensus: becomes krust's state store
  krust/       # Phase 2+: control plane (API server, scheduler, reconciler)
dist-sim/      # Go simulation harness: attacks krust with variable traffic and fault injection
```

## Phases

- **Phase 1** — Toy Raft in Rust + minimal dist-sim harness
- **Phase 2** — krust T1: API server, watch API, reconciliation loop, fake kubelet
- **Phase 3** — krust T2: multi-node Raft, real container runtime, scheduler, service abstraction

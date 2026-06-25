# C-Kyber: A Compressed Post-Quantum Key Exchange Protocol for LoRaWAN

## Overview

C-Kyber is a research project that investigates the feasibility of post-quantum cryptography (PQC) in Low-Power Wide-Area Networks (LPWANs), specifically LoRaWAN Class-A IoT deployments.

The project introduces **C-Kyber (Compressed-Kyber)**, an engineered variant of the NIST-standardized ML-KEM (Kyber-512) key encapsulation mechanism. The protocol is designed to overcome LoRaWAN's strict frame-size and duty-cycle limitations while preserving quantum-safe security guarantees.

This repository contains the source code, simulation environment, hardware implementation, datasets, analysis scripts, and experimental results developed throughout the research project.

---

## Research Motivation

Post-quantum cryptographic algorithms produce significantly larger public keys and ciphertexts than traditional elliptic-curve cryptography. While these algorithms are suitable for conventional Internet infrastructure, they present substantial challenges for constrained LPWAN technologies such as LoRaWAN.

A standard Kyber-512 public key requires multiple fragmented LoRaWAN transmissions, leading to excessive handshake delays, increased energy consumption, and reduced reliability under packet loss conditions.

This project investigates whether protocol-level engineering can make post-quantum key exchange practical for real-world LoRaWAN deployments.

---

## Research Objectives

### Objective 1

Develop and implement **C-Kyber**, a compressed and fragment-aware adaptation of Kyber-512 for LoRaWAN Class-A networks.

### Objective 2

Evaluate the performance of C-Kyber against standard Kyber-512 and ECC-ECDH baselines on ARM Cortex-M hardware.

### Objective 3

Determine the security-performance trade-off required to maintain NIST Level 1 security while satisfying LoRaWAN duty-cycle constraints.

---

## Engineering Contributions

C-Kyber applies three engineering operations to standard Kyber-512:

### [F] Fabricate

Fragment-aware bit-packing module for efficient transmission of Kyber public keys and ciphertexts over 51-byte LoRaWAN frames.

### [M] Modify

Duty-cycle-aware transmission scheduler that aligns packet transmission with LoRaWAN Class-A regulatory constraints.

### [R] Remove

Transmission-only padding elimination to reduce communication overhead without modifying cryptographic operations.

These modifications are applied at the protocol layer and do not alter Kyber's core cryptographic primitives.

---

## Baseline Models

The following baselines are used for comparison:

1. Standard Kyber-512 (ML-KEM)
2. ECC-ECDH (Curve25519)
3. Naively Fragmented Kyber-512

---

## Experimental Environment

### Simulation

* NS-3 (v3.38)
* LoRaWAN module
* Ubuntu 22.04

### Hardware

* STM32L476 Nucleo Boards
* SX1276 LoRa Transceivers
* Otii Arc Power Monitor

### Cryptographic Libraries

* liboqs
* mbedTLS

---

## Evaluation Metrics

The project evaluates:

* Handshake completion time
* Energy consumption per handshake
* Retransmission count
* Handshake success rate
* LoRaWAN frame count
* Flash memory footprint
* Effective security level
* Statistical significance (Wilcoxon Signed-Rank Test)

---

## Repository Structure

```text
c-kyber-lorawan/

docs/
└── proposal/
    └── Quantum_Safe_IoT_Research_Proposal.pdf
```

---

## Reproducibility

All experiments will be conducted using fixed random seeds and documented software versions.

Key outputs include:

* NS-3 simulation logs
* Hardware measurement data
* Statistical analysis notebooks
* Reproducible experiment configurations

---

## Expected Contributions

This work aims to demonstrate that post-quantum cryptography can be deployed on constrained LPWAN devices through protocol co-design rather than cryptographic modification.

The project contributes:

* A novel LoRaWAN-optimised PQC handshake protocol
* An empirical evaluation of PQC under realistic LPWAN constraints
* A reproducible implementation for future IoT security research

---

## Research Status

Current Phase: Proposal and Repository Setup

Planned Journal Targets:

* IEEE Internet of Things Journal
* Computer Networks

---

## Author

**Protus Sanker**
Department of Computer Science
Kwame Nkrumah University of Science and Technology (KNUST)

---

## License

This project is released under the MIT License.

<p align="center">
  <a href="https://attestium.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/attestium/attestium.com/main/assets/logo-dark.svg">
      <img src="https://raw.githubusercontent.com/attestium/attestium.com/main/assets/logo.svg" alt="Attestium, open-source remote attestation" width="420">
    </picture>
  </a>
</p>

<h3 align="center">Open-source remote attestation for Linux servers, containers and Node.js</h3>

<p align="center">
  <a href="https://attestium.com">Website</a> ·
  <a href="https://attestium.com/docs/getting-started/">Getting started</a> ·
  <a href="https://attestium.com/spec/">Evidence specification</a> ·
  <a href="https://attestium.com/attestium-whitepaper.pdf">Whitepaper (PDF)</a> ·
  <a href="https://www.npmjs.com/package/attestium">npm</a>
</p>

Attestium proves what a production server runs. An attester on the machine collects evidence: the deployed files, the installed packages, every running process with its executable, libraries and memory, containers, TPM 2.0 quotes and confidential VM reports. A verifier sends a fresh nonce, fetches its own references and compares the two: the public git commit, the hashes in your lockfile, the signed Debian or Ubuntu archive, the container image digest, a Sigstore attestation.

The report lists every difference it found and the trust level each answer reached.

## What Attestium verifies

| Area | Evidence from the server | Reference the verifier fetches |
| --- | --- | --- |
| Source code | A hash of every deployed file | A public git commit, or an attested release manifest |
| Dependencies | `node_modules`, Python virtual environments, Ruby gems, Composer, Maven and Gradle jars, .NET, Go, Rust and Elixir packages | The lockfile and each package registry's hashes |
| Running code | Each process's executable, shared libraries and executable memory | The files on disk, official runtime releases, the signed distribution archive |
| Containers | Docker, containerd and CRI-O root filesystems | The image, pulled by registry digest |
| Hardware | TPM 2.0 quotes, the Linux IMA measurement log, AMD SEV-SNP and Intel TDX reports | Pinned attestation keys, PCR values, vendor certificate chains |
| Supply chain | Release manifests, npm packages | Sigstore bundles, SLSA build provenance, GitHub artifact attestations |

## Evidence levels

Software evidence catches drift and tampering by anyone without root. Root on the server can forge it. A TPM with IMA backs the files the kernel measured with hardware signatures, and a confidential VM keeps the host operator out. Every report names the level its result reached, so you know which guarantee you hold.

## Projects

* [**attestium.com**](https://github.com/attestium/attestium.com): the Attestium library for Node.js 18 and later, the language-independent evidence format and its JSON Schema, and the technical whitepaper. Install it with `npm install attestium`.
* [**Audit Status**](https://github.com/auditstatus/auditstatus.com): a ready-made attester and verifier built on Attestium. It verifies your servers from GitHub Actions and publishes a report and a status badge. Its public registry checks projects every hour.

## In production

[Forward Email](https://forwardemail.net) verifies its production email servers with Attestium through Audit Status and shows the result on its [status page](https://status.forwardemail.net).

## Contributing and security

Issues and pull requests are welcome in [attestium/attestium.com](https://github.com/attestium/attestium.com). Report security issues at <https://forwardemail.net/security>. Attestium is MIT licensed.

<sub>Attestium is a project by <a href="https://forwardemail.net">Forward Email</a>, the 100% open-source, privacy-focused email service. Topics: remote attestation, runtime integrity, code integrity, software supply chain security, TPM 2.0, Linux IMA, confidential computing, AMD SEV-SNP, Intel TDX, Sigstore, SLSA, reproducible builds, open source transparency.</sub>

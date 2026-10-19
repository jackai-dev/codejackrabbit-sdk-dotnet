# <img src="./favicon.svg" width="28" height="28" alt="CodeJackRabbit" /> CodeJackRabbit .NET / C# SDK (`codejackrabbit-sdk-dotnet`)

Official **.NET / C#** SDK for **CodeJackRabbit** (`v0.2.0`), generated via [OmniWrap](https://github.com/JacquesGariepy/omniwrap) from the CodeJackRabbit OpenAPI 3.1.0 specification.

- **Organization:** [jackai-dev](https://github.com/orgs/jackai-dev)
- **Repository:** [jackai-dev/codejackrabbit-sdk-dotnet](https://github.com/jackai-dev/codejackrabbit-sdk-dotnet)
- **Umbrella SDK Index:** [jackai-dev/codejackrabbit-sdk](https://github.com/jackai-dev/codejackrabbit-sdk)
- **Target Ecosystem:** NuGet / .NET 8.0+
- **Generator:** OmniWrap (`python -m omniwrap.sdk gen --from-openapi openapi.json --mode http_client --renderer dotnet`)

## Installation

```bash
dotnet add package JackAI.CodeJackRabbit.Sdk
```

## Supported CodeJackRabbit v0.2.0 Capabilities

- **5-Stage Autonomous Review (`createReview`)**: AST + Shannon entropy secrets + OSV CVE + Critic verification
- **Multi-File Autofix (`buildAutofixBundle`)**: Conflict-free unified diff remediation patch synthesis
- **6-Axis PR Risk Radar (`computeRiskRadar`)**: Blast radius, security, complexity, test delta, supply-chain & slop telemetry
- **API & Schema Contract Drift (`analyzeContractDrift`)**: SemVer bump advisor and zero-downtime SQL migration guard
- **OASIS SARIF 2.1.0 & Compliance Gates (`exportSarif`, `evaluateComplianceGate`)**: SOC2, PCI-DSS, HIPAA & cryptographic attestation
- **Autonomous Stacked PR Splitter (`planStackedPrSplit`)**: Topological sub-PR decomposition
- **Performance N+1 & LLM FinOps Guard (`analyzePerfFinOps`)**: N+1 loop query and unbounded LLM token cost detection
- **Supply-Chain & CycloneDX 1.5 SBOM (`analyzeSupplyChain`, `generateSbom`)**
- **Multi-Surface SaaS & 3-Phase Metering (`getSaasBlueprint`, `issueSurfaceLease`, `reserveMeteringQuota`, `finalizeMeteringQuota`)**

## License

MIT -- Copyright (c) 2026 JackAI / CodeJackRabbit.

# CodeJackRabbit .NET API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImZlMGYyMjU1OGZiNDM0MTEwODJkZjVlMDc2MmEyM2U5ZWFmOTBhOWM3MTNmZTRlZTljZmQyNzM3OTIyMjgwM2QiLCJvcGVyYXRpb25fY291bnQiOjIyLCJyZW5kZXJlciI6ImRvdG5ldCIsInZlcnNpb24iOiIxLjQuMCJ9 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `fe0f22558fb43411082df5e0762a23e9eaf90a9c713fe4ee9cfd27379222803d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new ClientOptions { Hooks = new RequestHooks { ... } }` registers four callbacks. Every attempt starts with `BeforeRequest` and ends with exactly one of `OnRetry` (another attempt follows), `AfterResponse` (the success the call returns) or `OnError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every context is an immutable `HookContext` record: no hook can change the request.

`new ClientOptions { Tracer = ... }` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `ComplianceGateRequest`
- `FileChange`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJBbmFseXplQ29udHJhY3REcmlmdEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVDb250cmFjdERyaWZ0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9jb250cmFjdC1kcmlmdCIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6IjQ2YWU3YzdkYTRiNzQyYWYzNDRlM2RmZWQ4YTg0NDlkYmQ0NGIyMzdjZDhiMzhmNTc4ZGM0ZGYyZTQ0YTg5ZjQiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjZhNzc3YTg2Y2VhMjdiMjFlODA4ZjMyMmMxMDM3ZTNmMDVjNGEzZWJlMjYzNmNjNmYyNTI4ODAzYjI5YTFhYiJ9 -->
### `client.AnalyzeContractDriftAsync`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  

#### Signature

```csharp
public async Task AnalyzeContractDriftAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJBbmFseXplUGVyZkZpbk9wc0FzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVQZXJmRmluT3BzIiwicGF0aCI6Ii92MS9hbmFseXNpcy9wZXJmLWZpbm9wcyIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6IjU1ZWM0NjU1M2Y3NGE4YWY5MjM3OGI3MmRlNjEzODdlMDJlZmFkZGI5ZjFmZTdhOGRiNjk4MjU2YWNmY2E5ZjkiLCJzaWduYXR1cmVfc2hhMjU2IjoiODJiYzYyY2M0MWJlZTFlOTllYWZiMzZhZTJmYzYwMDAyMjA0NTgzZWQ4ZTA2ZjM2YjM2MDEwYTk0YWNiNDBiMSJ9 -->
### `client.AnalyzePerfFinOpsAsync`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  

#### Signature

```csharp
public async Task AnalyzePerfFinOpsAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJQbGFuU3RhY2tlZFByU3BsaXRBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQiLCJwYXRoIjoiL3YxL2FuYWx5c2lzL3NwbGl0LXByIiwicmVzb3VyY2UiOiJhbmFseXNpcyIsInNlY3Rpb25fc2hhMjU2IjoiMzg5NTA4OTVlODkxYTM1OTZkOThhN2M4OTY2YzlhZjcxMzE4YTc1OWY2OTVkNGE5OThhODMxYmIxM2JkNjMzMSIsInNpZ25hdHVyZV9zaGEyNTYiOiI4ODk3YWIyN2UzYzI1YWVjYzYxNjFlNzkyNjE3MDRiOGEzOTI2NTNhOWEwZjg0YmEyZjdhNTg5YzIzYTlkOTY2In0 -->
### `client.PlanStackedPrSplitAsync`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  

#### Signature

```csharp
public async Task PlanStackedPrSplitAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

## Resource `analytics`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJHZXRBbmFseXRpY3NSb2lBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFuYWx5dGljc1JvaSIsInBhdGgiOiIvdjEvYW5hbHl0aWNzL3JvaSIsInJlc291cmNlIjoiYW5hbHl0aWNzIiwic2VjdGlvbl9zaGEyNTYiOiIyZDUyMmJjNDVhZjE0OGQ2MTVmYTJlYmEzNDA3ZGMzMWQ5ZDk1MDEyNmFmZTdmMjM0NWYwMjhkMzFiMDQyMTIyIiwic2lnbmF0dXJlX3NoYTI1NiI6ImI2MTk2N2I3OTdkZGU4MTQ5M2MzN2E4ODZkOTMyZWRkOTc0YTBkMzFiNWU4MGYxMTEwZmU0ZjQ0NmJkMDQxMmIifQ -->
### `client.GetAnalyticsRoiAsync`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  

#### Signature

```csharp
public async Task GetAnalyticsRoiAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

## Resource `capabilities`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJHZXRDYXBhYmlsaXRpZXNBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldENhcGFiaWxpdGllcyIsInBhdGgiOiIvdjEvY2FwYWJpbGl0aWVzIiwicmVzb3VyY2UiOiJjYXBhYmlsaXRpZXMiLCJzZWN0aW9uX3NoYTI1NiI6IjYxMmE2MDk1MmM3ZjJiMDM3ZTJkNTY0OGI1OThiMjI4MjU5ZGNiZWJkYTM3MWVhNzE5NmNiMGJhNWM2MmJhYTIiLCJzaWduYXR1cmVfc2hhMjU2IjoiYjFlZTJhODRjZTk2YjllMDM5NTFhNzRhOGNhOWEyZTUwN2Q4ZmQ5YmY3YjllNWRmNWViZDVjZWU2MGIzYTEwYyJ9 -->
### `client.GetCapabilitiesAsync`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  

#### Signature

```csharp
public async Task GetCapabilitiesAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

## Resource `compliance`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJFdmFsdWF0ZUNvbXBsaWFuY2VHYXRlQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXZhbHVhdGVDb21wbGlhbmNlR2F0ZSIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9nYXRlIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI0YWM5OGI1NzM4YmYyZjkzYWE3Y2U4YzY3MzI4YWE1MjE4YjgzNTQ3OTkwYWRmNTdhM2I4ODVmNmYzMGE1YjI5Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjE3MDhkYjA3ZjEyNmY5ZDIzMTZlYzU2YjM0NmZjOTVmMWU5YTJmZDY5Njk1ZTc5YzllMDhlNWRiM2YyNjQwMzcifQ -->
### `client.EvaluateComplianceGateAsync`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  

#### Signature

```csharp
public async Task EvaluateComplianceGateAsync(
ComplianceGateRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJFeHBvcnRTYXJpZkFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImV4cG9ydFNhcmlmIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL3NhcmlmIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJjMjE2Mzc4YjRiNDFlMzI2YjljMTFiZWM0YzgyODhkZDgxMGI5YTQyYWM5OTM3MjUzNGIzN2U5ZGQwNDNiMWMzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjcyYjcxMWY3MGY2ZDYxYTA4NDUwNzg3ODI5MmU2ZjNjMzUyNjEyZDU0NDE5ZWI0MDVjYmY0YTcxNGMxZDNhYTgifQ -->
### `client.ExportSarifAsync`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  

#### Signature

```csharp
public async Task ExportSarifAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJHZXRIZWFsdGhBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhlYWx0aCIsInBhdGgiOiIvaGVhbHRoIiwicmVzb3VyY2UiOiJoZWFsdGgiLCJzZWN0aW9uX3NoYTI1NiI6IjM3ZWZlZjViMjZmMTE3ZjU4MGY2NThmYTNhY2EyNTYyMmZmMTc1OWIzMjllZmYwODg4NzI5MTZkMDBlNzFjYTYiLCJzaWduYXR1cmVfc2hhMjU2IjoiMzFlMjA1OWUxNGM2NThlYjViNzY3NWEzODFhMjdlZjAzMWE5NjlmMTZiZTllOWU2NGE5N2JlZGFiM2MyNmFlMiJ9 -->
### `client.GetHealthAsync`

Operation ID: `getHealth`  
Route: `GET` `/health`  

#### Signature

```csharp
public async Task GetHealthAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `reviews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJCdWlsZEF1dG9maXhCdW5kbGVBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUiLCJwYXRoIjoiL3YxL3Jldmlld3MvYXV0b2ZpeCIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiYzg0MzQ0NzM5M2QyYzJjMDRhMDg4MzlkNmVhYzM3NWIwZDg0MjgxZjllNGJjZGI0YzVjMDg3NGM3N2ZjMWNhYiIsInNpZ25hdHVyZV9zaGEyNTYiOiI5MDlmM2VlMmU1ZWU2N2U5MzU0ODUzNzQ1NDU2NmU1NmEyYjYzNjlkOWJjN2EzNWY2ZDlmMDBhZTgzZjY2YzcyIn0 -->
### `client.BuildAutofixBundleAsync`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  

#### Signature

```csharp
public async Task BuildAutofixBundleAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJDb21wdXRlUmlza1JhZGFyQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29tcHV0ZVJpc2tSYWRhciIsInBhdGgiOiIvdjEvcmV2aWV3cy9yaXNrLXJhZGFyIiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiIyNDY4MmU5NjBlOTA3NzlkNmQwNjM3NDY2NDljYzU5MWFlZGRhMTg4MDQyMGE5OTViYzI3ODk5ZTA0M2EzZDNjIiwic2lnbmF0dXJlX3NoYTI1NiI6ImRlNTc3NzY1NWZjYWQ5ZjZjZGM3YTczM2RkMmU1ZmQzY2I4OTgzZjZlNjNiNTRiYmU5Yzc5OWQyZjc1ODg1MmYifQ -->
### `client.ComputeRiskRadarAsync`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  

#### Signature

```csharp
public async Task ComputeRiskRadarAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJDcmVhdGVSZXZpZXdBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6IjllZjljYWQ1YTE5ZTk0MTU3ZWQwMjYxY2I4MThlNjMzMDNmYjEyMmQyZThiMjYxZjRhMmEzY2M4OGJmM2ZhMDEiLCJzaWduYXR1cmVfc2hhMjU2IjoiNDEzNjg5ODdiNmNjNDY4YjE1ZDNhYzdiNzk4MjhlMjg1MGQxYjNhMjNiMDkwMDlmNmExYzFmYjk2ZWU2MDc4MiJ9 -->
### `client.CreateReviewAsync`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  

#### Signature

```csharp
public async Task CreateReviewAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

## Resource `saas`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJGaW5hbGl6ZU1ldGVyaW5nUXVvdGFBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvZmluYWxpemUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6ImIwODJmNWU1NGJkMWNkMmUyMWI3YzRlNGRjMTc5ZWQ3MzAyOGEwNGNkN2EyNDdmNjliNDcxNGYyMDlmZWVkMTEiLCJzaWduYXR1cmVfc2hhMjU2IjoiZGQxY2E4NmEwMDdmODg3ZmFjNjUxYTY4NGQxMGY0NTE1MTNhM2QwMWY5NTJiZTcwODgwNDg5NjE3MjJhNDdlNiJ9 -->
### `client.FinalizeMeteringQuotaAsync`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  

#### Signature

```csharp
public async Task FinalizeMeteringQuotaAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJHZXRTYWFzQmx1ZXByaW50QXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50IiwicGF0aCI6Ii92MS9zYWFzL2JsdWVwcmludCIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiMWIzMzhhOGQ4ODk5YjM3NzdiYTc5MjRhNmE0YzAwNjEwYjlmNzNiYmZmYWQ5OTFiZWVjYzk1ODFkZjdiYzM3ZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI4NzljZTgyYTgyMmM1NWQ5OTE3YmFjOTU4Yzc0YzhhZmIxODBmOGM5MGQyMDQ1YTBiYTgxNzE0MmI2OTYwZmVhIn0 -->
### `client.GetSaasBlueprintAsync`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  

#### Signature

```csharp
public async Task GetSaasBlueprintAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJJc3N1ZVN1cmZhY2VMZWFzZUFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Imlzc3VlU3VyZmFjZUxlYXNlIiwicGF0aCI6Ii92MS9zYWFzL3N1cmZhY2UtbGVhc2UvaXNzdWUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjkwN2YwNjlhNTI4MTg1YjdkMjhlODA4ZTQ5YTQ0MzE2MThmZGY5ODAxMTFiMTM5ODAyYzBiZTVhMzZiZTI5MDQiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWUxYWQ2YTdjYmVmNTQ4MmNkYjZkZjMyOTJkMzIwMmZjNTU5NzlhM2ZjMzI4MzNlMjUxNzRkZDQ1MGNmYjhkMCJ9 -->
### `client.IssueSurfaceLeaseAsync`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  

#### Signature

```csharp
public async Task IssueSurfaceLeaseAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJSZXNlcnZlTWV0ZXJpbmdRdW90YUFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlc2VydmVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL3Jlc2VydmUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjNiZjNiNzQxY2MzNDk1OGRmYmJiMTEyNGMxZDkwNTIzYzZjNjUyNzFjZDEzOWNiNGRmNzE4MmY2ZmMxMjk1NjYiLCJzaWduYXR1cmVfc2hhMjU2IjoiY2I2NmZiMmE5NmJkOWIwNDJmZWFkYjNiZGE2Zjg3MWE4Nzg3ZTJmN2Q1NzFiMjUwYjUwYWZkODAyNTUwYWJiYSJ9 -->
### `client.ReserveMeteringQuotaAsync`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  

#### Signature

```csharp
public async Task ReserveMeteringQuotaAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

## Resource `sbom`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJHZW5lcmF0ZVNib21Bc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20iLCJwYXRoIjoiL3YxL3Nib20iLCJyZXNvdXJjZSI6InNib20iLCJzZWN0aW9uX3NoYTI1NiI6ImM0YzNiYTNlZTRlZTZjOTdlMzhhZDg1ZWFlNjRlNzhmNWUxODg3Yzk4NWE1MWM3ZDBlM2U3MTk1OGI2NjA0NmEiLCJzaWduYXR1cmVfc2hhMjU2IjoiMTFkMWNjNjQ1MjMyZGYyNTdmMDZmNmQ2MjgyZmQ0ZTkzYzQ4NjkwN2U0OWVmMDczZGRiMWI5YmYzYTk3YmNjZiJ9 -->
### `client.GenerateSbomAsync`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  

#### Signature

```csharp
public async Task GenerateSbomAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

## Resource `supply_chain`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJBbmFseXplU3VwcGx5Q2hhaW5Bc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4iLCJwYXRoIjoiL3YxL3N1cHBseS1jaGFpbi9hbmFseXplIiwicmVzb3VyY2UiOiJzdXBwbHlfY2hhaW4iLCJzZWN0aW9uX3NoYTI1NiI6ImY5ZTkxNDc5ZWM3Y2Y4ZTExMzc4MDQ5MTA1ODgzYTIwY2Y4ZWJjNjcwMzc2OGIyMWUwYmJlMmMwYTRmNWUwMjciLCJzaWduYXR1cmVfc2hhMjU2IjoiMWJlZjhlM2UwMzY3MmQ1OGY4YjdhYjExNTA0OGMyZTkyN2MzYjIxZGQ1MTc1MTFhOWY4Mzc2YjdkZDZmNWJiYyJ9 -->
### `client.AnalyzeSupplyChainAsync`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  

#### Signature

```csharp
public async Task AnalyzeSupplyChainAsync(
ReviewRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

## Resource `tasks`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJDcmVhdGVDb2RpbmdUYXNrQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ29kaW5nVGFzayIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiIxODA2ODUzMmM2MTdkMWRiZGYwNDYxZmU5ZTdiOTBmM2U3ZjRiNmRjMjUzNDVhNWQ2MTA2ODVlM2Y0NGUxNTNhIiwic2lnbmF0dXJlX3NoYTI1NiI6IjU1YjhhNDgyMzZjM2NkMzY0MWI5ZDNiZGNjN2UxNWZkNjU3NzRjM2JmMjRlODcwMmE5MmZjODIwMGYwZjBjMzAifQ -->
### `client.CreateCodingTaskAsync`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  

#### Signature

```csharp
public async Task CreateCodingTaskAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJMaXN0Q29kaW5nVGFza3NBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RDb2RpbmdUYXNrcyIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiJjYzQ1MzViYzQzY2JmNGFiMjJhMWQ3NjhkMzE3MzY0MWIxM2VkMjA4NmE4MDFiMGMyNGViNGE1M2I5Mjk4ZmM3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjJlYTQzYTU3NzdlMGE4YTNjODA2ZDQ0Mzc3MjY2MDMwMGMzNjRiMWQ4Mzk5NTU2YmMyODNhZmEyM2NkYWUzY2QifQ -->
### `client.ListCodingTasksAsync`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  

#### Signature

```csharp
public async Task ListCodingTasksAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

## Resource `triage`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJHZXRUcmlhZ2VRdWV1ZUFzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0VHJpYWdlUXVldWUiLCJwYXRoIjoiL3YxL3RyaWFnZSIsInJlc291cmNlIjoidHJpYWdlIiwic2VjdGlvbl9zaGEyNTYiOiIzMGM4ZTk3ZDBmZDZiNjFlYzE5ZDE3OGRmMWY2NTM4MTEwMjgzYzAwODcwY2I5Y2Q0NWRlZTk1NjkzYWE1ZTJhIiwic2lnbmF0dXJlX3NoYTI1NiI6IjZmMTdiNDRkMWVhMmNlZmNmMDM4MGZmMTRmYWY0MDUyZjdiOGMyNTE4ZWQyMGJmMDA3ZDQzZjY1OWYzOWQ4MzgifQ -->
### `client.GetTriageQueueAsync`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  

#### Signature

```csharp
public async Task GetTriageQueueAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJMaXN0V2FpdGxpc3RBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RXYWl0bGlzdCIsInBhdGgiOiIvdjEvd2FpdGxpc3QiLCJyZXNvdXJjZSI6IndhaXRsaXN0Iiwic2VjdGlvbl9zaGEyNTYiOiI5ZjAzNmE1M2U2MWNjZDE5YTIwZjEwZGIyNGY2ODhhYjQxYTUzM2RkNDEwNzg0ODViMDExNzNkYTY2YjFiMzVlIiwic2lnbmF0dXJlX3NoYTI1NiI6IjZmNzUwNDZhYWY2ZWNjYmYxOWNjZmMyNmE1NTljYjQ1YTYyY2YyYzEyMzdjNTc0ZjM1NTg5ODBkMWEzNjlkMGYifQ -->
### `client.ListWaitlistAsync`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  

#### Signature

```csharp
public async Task ListWaitlistAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJSZWdpc3RlcldhaXRsaXN0QXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVnaXN0ZXJXYWl0bGlzdCIsInBhdGgiOiIvdjEvd2FpdGxpc3QiLCJyZXNvdXJjZSI6IndhaXRsaXN0Iiwic2VjdGlvbl9zaGEyNTYiOiI3MGUyM2VmYThlNDljYmUxNzhjOTA1MmQyN2JhMzAzMDA4Yzk0ZTg5ZTgzZGJmNGMwYTZlYjdiOWNlZmE3YjA3Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImRlMGNlM2ZlZjhmNzllNmU2MTkxOTk1ZmQ1MGEzMjdkZmI4ZDhkYmE4MDFhMmViNWMyMzFiM2FkOTIwZWZkMWMifQ -->
### `client.RegisterWaitlistAsync`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  

#### Signature

```csharp
public async Task RegisterWaitlistAsync(
WaitlistRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->


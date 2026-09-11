# EU CBAM & Carbon Tax Calculation Engine — TypeScript / JavaScript SDK

[![npm version](https://img.shields.io/npm/v/@stanzaapi/cbam-carbon.svg)](https://www.npmjs.com/package/@stanzaapi/cbam-carbon)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> EU CBAM Scope 1/2 embedded emissions and EU ETS carbon tax liability calculator across Iron, Steel, Aluminum, Cement, Fertilizers, and Hydrogen.

Official, zero-dependency Node.js and TypeScript client for **EU CBAM & Carbon Tax Calculation Engine**, powered by the [Stanza Micro-API Network](https://stanzaapi.com). Delivers deterministic, sub-5ms V8 isolate execution directly to your application without 3rd-party proxies.

* 🌐 **Live Web Sandbox:** [Try interactive queries online](https://stanzaapi.com/tools/cbam-carbon)
* 📚 **API Reference:** [Read complete OpenAPI specification](https://stanzaapi.com/tools/cbam-carbon)
* ⚡ **Platform Overview:** [Discover the Stanza Edge Portfolio](https://stanzaapi.com)

---

## 📦 Installation

```bash
npm install @stanzaapi/cbam-carbon
# or
pnpm add @stanzaapi/cbam-carbon
# or
yarn add @stanzaapi/cbam-carbon
```

---

## 🚀 Quickstart

```typescript
import { CbamCarbonClient } from '@stanzaapi/cbam-carbon';

// Initialize client (API key optional for sandbox tier evaluation)
const client = new CbamCarbonClient({
  apiKey: process.env.STANZA_API_KEY,
});

async function main() {
  const result = await client.parse({
  "goods_category": "iron_and_steel",
  "production_country": "TR",
  "quantity_tonnes": 500
});

  if (result.success) {
    console.log('Verification Success:', result.data);
  } else {
    console.error('Validation Error:', result.error, result.code);
  }
}

main().catch(console.error);
```

---

## 📄 Example JSON Response

```json
{
  "success": true,
  "data": {
    "goods_category": "iron_and_steel",
    "direct_emissions_tco2e": 950,
    "estimated_ets_liability_eur": 71250
  }
}
```

---

## ⚙️ Client Configuration Options

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `apiKey` | `string` | `process.env.STANZA_API_KEY` | Your [Stanza API Key](https://stanzaapi.com). Required for high-throughput production tiers. |
| `baseUrl` | `string` | `https://api.stanzaapi.com/cbam-carbon` | Public edge API base URL. |
| `timeoutMs` | `number` | `15000` | Request timeout in milliseconds (uses native `AbortSignal.timeout`). |


---

## 🛡️ Response Envelope & Error Handling

All responses return a typed envelope:

```typescript
export interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
  code?: 'VALIDATION_ERROR' | 'UNAUTHORIZED' | 'PAYLOAD_TOO_LARGE' | 'RATE_LIMITED' | 'INTERNAL_ERROR';
}
```

---

## 🔗 Related Resources

* [EU CBAM & Carbon Tax Calculation Engine Interactive Playground](https://stanzaapi.com/tools/cbam-carbon)
* [Stanza Microservices Directory](https://stanzaapi.com)
* [Report an Issue on GitHub](https://github.com/StanzaAPI/cbam-carbon-typescript/issues)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).

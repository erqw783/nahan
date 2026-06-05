# Project Nahan (پروژه نهان)

**Nahan** (Persian for *Hidden/Concealed*) is a secure, lightweight, and customizable network gateway designed to run entirely on Cloudflare Workers. It acts as an obfuscated reverse proxy (VLESS / Trojan over WebSocket) configured via an intuitive, embedded web dashboard.

By disguising its web interface as an "IoT Telemetry Gateway," unauthorized requests or active network probes are seamlessly proxied to maintenance hosts (like ubuntu.com), ensuring your gateway remains hidden.

## 🚀 Features

*   **Fully Embedded Dashboard:** Update settings, scan QR codes, and generate client subscription links on the fly.
*   **Dual Protocol Support:** Run in `Alpha mode` (VLESS) or `Beta mode` (Trojan) configuration profiles.
*   **Dynamic KV Storage:** State configurations survive worker upgrades by saving to Cloudflare KV storage (`IOT_DB`).
*   **Browser-Side Latency Diagnostics:** Verify connection routing speeds directly from your browser to targeted endpoints.
*   **Configuration Backup & Restore:** Export and import gateway setting sets as `.json` configuration files locally.
*   **Camouflage Redirection:** Seamlessly redirects unauthorized network scans to legitimate sites (`ubuntu.com`, `docker.com`).
*   **Dual-Language UI:** Built-in English and Persian (Farsi) translation layouts with automatic dark/light mode toggle.

## 🛠️ Deployment Instructions

### 1. Create a KV Namespace
1. Go to your Cloudflare Dashboard.
2. Navigate to **Workers & Pages** -> **KV**.
3. Create a new namespace and name it `IOT_DB`.

### 2. Deploy the Worker
1. Go to **Workers & Pages** -> **Overview** -> **Create Application** -> **Create Worker**.
2. Name your worker (e.g., `nahan-gateway`) and deploy it.
3. Click **Edit code** and paste the provided `index.js` script.
4. Click **Deploy**.

### 3. Bind the KV Namespace
1. In your Worker's settings page, go to **Settings** -> **Variables**.
2. Under **KV Namespace Bindings**, add a new binding:
   * **Variable name:** `IOT_DB`
   * **KV namespace:** Select the `IOT_DB` namespace you created in step 1.
3. Save and deploy again.

## ⚙️ Configuration

Once deployed, access the dashboard to configure your gateway. See the [HELP.md](HELP.md) guide for a full walkthrough of properties.

# TTSSorcery Extension - Local API Fixed Version

## What was fixed

This version fixes the original extension to work properly with local Zonos API servers without requiring an API key.

### Changes made:

1. **API Key Validation Fix**: Modified the API key validation logic to only require an API key when using cloud API (`use_local_api: false`). When using local API (`use_local_api: true`), no API key is required.

2. **Default Settings Update**: Changed the default `local_api_url` to `http://localhost:8181` to match the Docker compose port mapping.

3. **Version Update**: Updated manifest to version 1.1 and disabled auto-update to prevent overwriting the fix.

### Files changed:
- `index.js`: Lines 782-791 and 956-963 - Modified API key validation
- `index.js`: Line 28 - Updated default local API URL  
- `manifest.json`: Updated version and display name

## How to use

1. Copy this entire `SillyTavern-TTSSorcery-Fork-Fixed` folder to your SillyTavern `scripts/extensions/third-party/` directory
2. In SillyTavern extension settings:
   - ✅ Check "Use Local Zonos API"
   - Set "Local API URL" to: `http://localhost:8181`
   - Leave "Zyphra API Key" field empty (no longer required for local API)
3. Make sure your Zonos API container is running on port 8181

## Original vs Fixed behavior

**Original**: Always required API key, even for local usage
**Fixed**: Only requires API key for cloud API usage (`use_local_api: false`)

This allows you to use the extension with your local Zonos API server without needing to put dummy values in the API key field.
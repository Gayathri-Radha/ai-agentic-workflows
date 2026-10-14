---
on:
  workflow_dispatch:

permissions:
  contents: read
  copilot-requests: write

engine:
  id: copilot
  model: gpt-4.1-mini
  env:
    COPILOT_PROVIDER_BASE_URL: https://ghaw-apim-spike.azure-api.net/foundry/openai/v1
    COPILOT_PROVIDER_WIRE_API: responses
    COPILOT_PROVIDER_TYPE: azure

network:
  allowed:
    - defaults
    - ghaw-apim-spike.azure-api.net
---

# APIM to Foundry connectivity smoke test

Respond with exactly:

`GH_AW_APIM_FOUNDRY_SUCCESS`

Do not modify repository files and do not use any tools. This workflow exists only to prove that the gh-aw runtime can send an inference request through Azure API Management to the Azure Foundry model and receive a response.

---
on:
  workflow_dispatch:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  contents: read
  copilot-requests: write
  id-token: write

engine:
  id: copilot
  model: gpt-4.1-mini
  auth:
    type: github-oidc
    azure-tenant-id: 950a3fad-34b5-415a-8bec-8074b03aabaa
    azure-client-id: 5395fdb9-8066-4006-9f8b-f56563579808
    azure-scope: api://5d503f85-f79b-490a-bebf-217f77e0da51/.default
  env:
    COPILOT_PROVIDER_BASE_URL: https://ghaw-apim-spike.azure-api.net/foundry/openai/v1
    COPILOT_MODEL: gpt-4.1-mini
    COPILOT_PROVIDER_WIRE_API: responses

tools:
  bash: ["echo"]
  github:
    toolsets: [repos]
    allowed: [get_file_contents, list_commits]

network:
  allowed:
    - defaults
    - ghaw-apim-spike.azure-api.net
    - login.microsoftonline.com
---

# APIM to Foundry connectivity smoke test

Call these three tools, in this order, through the model. Do not modify repository files.

1. Run `echo GH_AW_APIM_FOUNDRY_SUCCESS`.
2. Read `README.md` with the GitHub `get_file_contents` tool.
3. List one commit with the GitHub `list_commits` tool.

After all three tool calls succeed, reply with exactly:

`GH_AW_APIM_FOUNDRY_SUCCESS`

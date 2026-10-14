---
on:
  workflow_dispatch:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  contents: read
  copilot-requests: write

engine:
  id: copilot
  model: gpt-4.1-mini
  env:
    COPILOT_PROVIDER_BASE_URL: https://ghaw-apim-spike.azure-api.net/foundry/openai/v1
    COPILOT_PROVIDER_API_KEY: ${{ secrets.AZURE_FOUNDRY_API_KEY }}
    COPILOT_MODEL: gpt-4.1-mini
    COPILOT_PROVIDER_WIRE_API: completions

tools:
  bash: ["echo"]
  github:
    toolsets: [repos]
    allowed: [get_file_contents, list_commits]

network:
  allowed:
    - defaults
    - ghaw-apim-spike.azure-api.net
---

# APIM to Foundry connectivity smoke test

Call these three tools, in this order, through the model. Do not modify repository files.

1. Run `echo GH_AW_APIM_FOUNDRY_SUCCESS`.
2. Read `README.md` with the GitHub `get_file_contents` tool.
3. List one commit with the GitHub `list_commits` tool.

After all three tool calls succeed, reply with exactly:

`GH_AW_APIM_FOUNDRY_SUCCESS`

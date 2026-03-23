---
description: Local server setup required before taking Playwright screenshots of local HTML files
---

Playwright MCP blocks `file://` URLs. Always serve local files over HTTP before screenshotting:

```bash
npx --yes serve -p 3456 . &>/tmp/serve.log &
sleep 2
```

Then navigate to `http://localhost:3456/index.html`.

**Cleanup:** Kill the server when done with `kill $(lsof -ti:3456)`.

**Port conflict:** If port 3456 is busy, use 3457 or check with `lsof -i:3456`.

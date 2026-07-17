<h3 align="center">Midjourney API Skill for RunAPI</h3>

<div align="center">

[![skills.sh](https://www.skills.sh/b/runapi-ai/midjourney)](https://www.skills.sh/runapi-ai/midjourney/midjourney)
[![ClawHub](https://img.shields.io/badge/ClawHub-runapi--midjourney-111827)](https://clawhub.ai/runapi-ai/runapi-midjourney)
[![License](https://img.shields.io/github/license/runapi-ai/midjourney)](https://github.com/runapi-ai/midjourney/blob/main/LICENSE)

</div>
<br/>

Use Midjourney through the RunAPI CLI for one-off image generation, image editing, image-to-video, prompt analysis, and seed lookup. The canonical agent file is `skills/midjourney/SKILL.md`.

## Variants

- V8.1 text to image: generate an image grid from a text prompt with `runapi midjourney text-to-image`.
- Image editing: transform a source image with a prompt using `runapi midjourney edit-image`.
- Image to video: animate a source image with `runapi midjourney image-to-video`.

## Install

Install for Codex, Claude Code, Gemini CLI, Cursor, and other supported agents:

```bash
npx skills add runapi-ai/midjourney -g
```

Or paste this prompt to your AI agent:

```text
Install the midjourney skill for me:

1. Clone https://github.com/runapi-ai/midjourney
2. Copy the skills/midjourney/ directory into your
   user-level skills directory.
3. Verify that SKILL.md is present.
4. Confirm the install path when done.
```

Claude Code can also install the repository skill directory into its user skills directory. Codex and Gemini CLI should use their user-level skills directories and keep `SKILL.md` at `skills/midjourney/SKILL.md`.

## Commands

```shell
runapi midjourney text-to-image --input-file text-to-image.json
runapi midjourney edit-image --input-file edit-image.json
runapi midjourney image-to-video --input-file image-to-video.json
runapi midjourney image-to-prompt --input-file image-to-prompt.json
runapi midjourney get-seed --input-file get-seed.json
```

The first three commands create asynchronous tasks. `image-to-prompt` and `get-seed` return synchronously.

## Links

- Model page: https://runapi.ai/models/midjourney
- Product docs: https://runapi.ai/docs#midjourney
- SDK repository: https://github.com/runapi-ai/midjourney-sdk
- Provider page: https://runapi.ai/providers/midjourney
- Full catalog: https://runapi.ai/models

## License

Licensed under the Apache License, Version 2.0.

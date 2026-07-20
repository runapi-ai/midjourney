---
name: midjourney
description: Generate and edit images, create video from images, derive or shorten prompt suggestions, and look up seeds with Midjourney through RunAPI. Use the RunAPI CLI for one-off work and the language SDKs for application integration.
documentation: https://runapi.ai/models/midjourney.md
provider_page: https://runapi.ai/providers/midjourney.md
catalog: https://runapi.ai/models.md
metadata:
  openclaw:
    homepage: https://runapi.ai/models/midjourney
    requires:
      bins:
      - runapi
    install:
    - kind: brew
      formula: runapi-ai/tap/runapi
      bins:
      - runapi
    envVars:
    - name: RUNAPI_API_KEY
      required: false
      description: Optional RunAPI API key; prefer environment auth or saved CLI config.
---

# Midjourney On RunAPI

Use the RunAPI CLI for one-off requests and manual verification. Use the target language SDK for applications, workers, libraries, and production integrations; never shell out to the CLI as an application runtime.

## Critical: Integration Runtime

- Integration work (app, backend, worker, library, Rails service, Node service, Go service, webhook pipeline, or production codebase) uses the **SDK integration path** for the target language.
- One-off generation, editing, transformation, manual smoke tests, debugging, or user-requested CLI runs use the **CLI path** with the `runapi` binary. For full CLI-specific agent guidance, see https://github.com/runapi-ai/cli-skill.
- Never shell out to the `runapi` CLI as the production runtime integration layer.

## SDK integration path

When integrating Midjourney into an app, backend, worker, library, Rails service, Node service, Go service, webhook pipeline, or production workflow, check the current SDK package and official usage. Confirm install commands, client methods (`create`, `get`, `run`), request fields, response shape, and error classes before using CLI help or raw HTTP examples. Use a RunAPI SDK package:

- JavaScript / TypeScript: `@runapi.ai/midjourney`
- Python: `runapi-midjourney`
- Ruby: `runapi-midjourney`
- Go: `github.com/runapi-ai/midjourney-sdk/go`
- Java: `ai.runapi:runapi-midjourney`
- PHP: `runapi-ai/midjourney`

## Variants

- V8.1 text to image: generate an image grid from a text prompt.
- Image editing: transform a source image with a prompt.
- Image to video: animate a source image.

## CLI path

The `runapi` binary is the one-off and manual testing runtime dependency. For full CLI-specific agent guidance, see https://github.com/runapi-ai/cli-skill. Run `runapi auth status` first. Prefer `RUNAPI_API_KEY` or import a token with `printf '%s' "$RUNAPI_API_KEY" | runapi auth import-token --token -`. Use browser login only when the user explicitly requests an interactive login.

Inspect current fields before creating a request:

```shell
runapi midjourney --help
runapi midjourney text-to-image --help
runapi midjourney edit-image --help
runapi midjourney image-to-video --help
runapi midjourney image-to-prompt --help
runapi midjourney shorten-prompt --help
runapi midjourney get-seed --help
```

## Asynchronous Requests

`text-to-image`, `edit-image`, and `image-to-video` are asynchronous. Run them directly to create and poll, or add `--async` and wait separately.

```shell
runapi midjourney text-to-image --input-file text-to-image.json
runapi midjourney edit-image --async --input-file edit-image.json
runapi wait <task-id> --service midjourney --action edit-image
runapi midjourney image-to-video --input-file image-to-video.json
```

Use `midjourney-v8.1` for text-to-image, `midjourney-edit-image` for edits, and `midjourney-image-to-video` for image-to-video. Image and video input URLs must be publicly fetchable.

## Synchronous Helpers

`image-to-prompt`, `shorten-prompt`, and `get-seed` return in one request. Do not add `--async` and do not call `runapi wait` for them.

```shell
runapi midjourney image-to-prompt --input-file image-to-prompt.json
runapi midjourney shorten-prompt --input-file shorten-prompt.json
runapi midjourney get-seed --input-file get-seed.json
```

`get-seed` accepts only an `image_id` returned by a completed Midjourney text-to-image or edit-image task owned by the current account.

## Result Handling

Completed image tasks return `images` and may return `image_id`, `actions`, and `progress`. Completed video tasks return `videos` and may return `video_id` and `progress`. Generated media URLs are temporary; download and store them in durable storage.

## References

- Model overview: https://runapi.ai/models/midjourney.md
- V8.1 text-to-image: https://runapi.ai/models/midjourney/v8.1.md
- Image editing: https://runapi.ai/models/midjourney/edit-image.md
- Image to video: https://runapi.ai/models/midjourney/image-to-video.md
- Provider page: https://runapi.ai/providers/midjourney.md
- Full catalog: https://runapi.ai/models.md

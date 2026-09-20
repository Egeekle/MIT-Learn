# Canonical workflow

- Status flow is `draft → review → approved` (definition in `00-System/Conventions.md`). Only the user's explicit approval sets `approved`.
- Never overwrite an approved note in place. Follow the archive procedure in Conventions: copy to `99-Archive/versions/<name>@v<N>.md`, bump `version`, add a `## Version history` line, set `status: review`.
- New content goes in as `draft`. When handing to the user, set `review` and list what needs checking.
- Check for an existing note before creating one; extend rather than duplicate. Link with wikilinks.

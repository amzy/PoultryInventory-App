# Website Source Rule

## Canonical source

The `website/` directory in `amzy/PoultryInventory-App` is the **single source of truth** for the OvalOasis marketing website.

## Required rules

1. Never replace, regenerate, or reconstruct `website/` from an older project ZIP, build artifact, or the public website repository.
2. Existing website files and design changes must be preserved exactly unless the private source repository contains an intentional website update.
3. App-only changes (Flutter, Firebase, functions, sync, categories, etc.) must **not** modify or reset any file under `website/`.
4. `amzy/PoultryInventory-Website` is a deployment mirror only. Do not use it as the source for future website changes.
5. The publish workflow may copy `website/` to the public repository only when website source changes are intentionally committed to this private repository.
6. When creating project ZIPs, always copy the current `website/` directory from the private repository/project working tree into the ZIP. Do not source website files from an older ZIP.
7. If there is no website change, a project update must leave the website directory byte-for-byte unchanged.

## Website update procedure

When a website change is requested:

- Edit the files under `website/` in this repository.
- Review the complete website directory.
- Commit the website change.
- The publish workflow then mirrors that exact directory to the public website repository.

This rule protects the latest website design from being lost during unrelated application fixes.

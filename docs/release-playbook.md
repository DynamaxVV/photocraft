# Release playbook

The release playbook shared by every crafting app lives in craftrules:
`../craftrules/release/playbook.md`
(`storytold/craftrules`, a sibling checkout; the repository is not public). It is the canonical copy; don't duplicate it here. If you do not have access to that checkout, use the public [PhotoCraft release guide](releasing.md) and ask a maintainer for any shared rules relevant to your change.

PhotoCraft is its reference implementation (`.github/workflows/release.yml`, `packaging/`,
`cargo xtask version`). PhotoCraft-specific details are in [releasing.md](releasing.md).

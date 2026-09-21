# AGENTS.md

## Cursor Cloud specific instructions

This repository is SumUp's organization-level `.github` repository. It contains **only GitHub community-health documentation** and the org profile page:

- `README.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `LICENSE`
- `profile/README.md` — the org profile page, which is a link directory to SumUp's actual product/SDK repositories (each of which lives in its own separate repo).

There is **no application code, package manifest, dependency, build system, test suite, or runnable service** here. As a result:

- There is nothing to install, lint, build, or run. No update/setup script is needed (a no-op is sufficient).
- The only meaningful validation is confirming the Markdown renders and that the outbound links in `profile/README.md` resolve. You can sanity-check the links with, e.g.:

```bash
for url in $(grep -oE 'https?://[^) ]+' profile/README.md | sort -u); do
  echo "$(curl -s -o /dev/null -w '%{http_code}' -L --max-time 20 "$url")  $url"
done
```

- The actual SumUp products (Node/Python/Java/Go/PHP/Rust/.NET SDKs, mobile SDKs, developer tools, and open-source projects under `sumup-oss`) live in the separate repositories linked from `profile/README.md`. Any code-level development work belongs in those repos, not this one.

# AWS Django example (retired)

This repository preserves a historical Django/Fabric/Docker tutorial. It is no longer deployed. Dependency versions and tutorial behavior are retained for reference.

## Local configuration

The Django signing key is supplied through `DJANGO_SECRET_KEY`. Generate your own value before running Django or the deployment helper:

```sh
export DJANGO_SECRET_KEY="$(python3 -c 'import secrets; print(secrets.token_urlsafe(48))')"
```

Both Compose files pass this variable into the web container and report an error if it is missing. For repeatable local use, store your generated value in an ignored `.env` file; Compose reads that file automatically. Export the same variable into your shell before running Django or Fabric directly. Retain a stable private key between restarts when persistent sessions or signed data matter.

The database credentials (`awsdemo`) and administrator credentials (`demo` / `demo@demo.com`) in the tutorial are deliberate public sample values, not private deployment credentials. Replace them before adapting this example for a real deployment.

The historical Fabric helper reads its target hostname from `AWS_DEMO_HOST` and defaults to the non-routable example hostname `example.invalid`. It expects your own local SSH key at `~/.ssh/aws.pem`. Its clone URL points to this sanitized repository, and the initial stack deployment passes `DJANGO_SECRET_KEY` from your local environment. No old EC2 instance is configured or contacted by default.

Recreate Python environments from the retained Pipfiles/lockfiles. Virtualenvs, IDE state, local environment files, private SSH keys and downloaded database backups belong outside Git.

## History cleanup

Sensitive configuration and personal material were removed from all fetched branch and pull-request histories in October 2026. Author email was normalized to the owner's GitHub noreply identity. Existing dependency-update branches retain their original dependency changes.

After this history rewrite, use a fresh clone. Do not merge or push an old clone into the cleaned repository: that can restore the removed history. GitHub-managed PR refs and cached old commits require separate server-side handling; a branch rewrite alone does not purge those copies.

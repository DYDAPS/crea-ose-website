# Project maintenance guidance

Use `$dydaps-wordpress-maintenance` for inventory, updates, risk-based validation, Git and release procedures. Use the commercial spelling **CREA...OSE** exactly; preserve the technical repository slug and identifiers.

## Project structure

- WordPress core is tracked at the repository root. Preserve `hello-elementor-child`, which extends Hello Elementor, and all DYDAPS-maintained plugins.
- The database contains page content, activation state and plugin settings; do not infer these from files or change production data during maintenance.

## Durable constraints

- PHP 8.4 is the DYDAPS compatibility target. Validate locally and never change hosting PHP settings automatically.
- Keep local configuration, uploads, generated media, caches, logs and backups outside Git.

## Deployment

- Verify the current OVH deployment trigger and target before release. A push to `main` may redeploy production; check the deployed result after an authorized push.

## Git conventions

Use `$dydaps-wordpress-maintenance` for commit creation and promotion. Every commit is UTF-8 and exactly one English line: one valid Gitmoji, one space, and a concise title. Do not add a body, description, source reference, cherry-pick note, or trailer.

Create one code-update commit per component. Independent translations use one separate commit per component per campaign, including every language, text domain, file, and PO/MO/JSON/`.l10n.php` format. Never split translations by language, file, or format; combine components; or create empty translation commits. Use `🌐 Update WordPress translations`, `🌐 Update [Plugin name] translations`, or `🌐 Update [Theme name] translations`, without a language name. Translations inseparable from an official component distribution may remain in its update commit.

Install and run the Skill's Git policy hooks before commits and pushes. Maintenance `AGENTS.md` belongs only on `develop`. History rewrites and force pushes require explicit authorization for the specific task.

# Repository Guidelines

## Project Overview

Piwigo is open-source PHP web software for managing photo libraries as a web gallery.
The runtime uses a web server, PHP, MySQL or MariaDB, and ImageMagick or PHP GD.
The current checkout is the personal fork of the upstream Piwigo repository.

## Fork & Upstream Contribution Intent

- Official upstream: [Piwigo/Piwigo](https://github.com/Piwigo/Piwigo).
- This checkout is the [MikeeI/Piwigo](https://github.com/MikeeI/Piwigo) fork, not an independently owned product.
- The goal is to support upstream with evidence-backed issues, comments, and pull requests.
- `ISSUES.md` provides the compact finding overview and global ID allocator.
- `issues/ISSUE-NNN.md` owns the complete durable record for one root cause.
- `FORMAT.md` owns research, drafting, implementation authorization, approval, and publication rules.
- Apply `skill-fork-contribution-tracking` for ledger, lifecycle, personal-branch, and upstream handoff work.
- Apply `skill-maintainer-communication` before external issues, pull requests, reviews, comments, or discussions.
- Follow the upstream contribution guide in `docs/CONTRIBUTING.md`.
- Piwigo contributions target the upstream `master` branch.
- Piwigo security reports go to `security@piwigo.org`; the project has no bug bounty program.
- Never choose `Authorized-Work` or `Publication-Target` on the user's behalf.
- Base upstream contribution branches on current `upstream/master`.
- Keep fork-only context, ledgers, configuration, and personal commits out of upstream contribution diffs.
- Reproduce claimed bugs against current upstream and run the narrowest conclusive verification.
- Publish one coherent root cause per issue, comment, or pull request.

## Finding and Contribution Ledger

- At the start of every agent session, agents MUST read root `ISSUES.md` before repository work.
- `ISSUES.md` owns the global `Next finding ID` allocator and compact cross-finding overview.
- Each `issues/ISSUE-NNN.md` owns one finding's state, evidence, drafts, and next action.
- `FORMAT.md` is authoritative for research, drafting, implementation boundaries, and publication format.
- Before adding a finding, search the index and every relevant issue record for the same symptom or root cause.
- New findings MUST use `Next finding ID`.
- Create the issue file, add its index row, and increment the allocator together.
- Finding IDs use `ISSUE-NNN`, start at `ISSUE-001`, and remain permanent.
- Update the issue file and `ISSUES.md` together after state, authorization, target, priority, next action, or reference changes.
- Every issue record MUST use the field and section contract in `FORMAT.md`.
- New findings start with `State: Investigating`, `Authorized-Work: Not-Selected`, and `Publication-Target: Not-Selected`.
- Run the read-only validator bundled with `skill-fork-contribution-tracking` after every ledger mutation.
- Keep `FORMAT.md`, `ISSUES.md`, `issues/`, and fork-only `AGENTS.md` changes out of upstream contribution diffs.

### Architecture & Data Flow

- Root PHP files are public and administrative web entry points.
- `include/` owns bootstrap code, configuration, database access, templates, users, and web-service plumbing.
- `include/ws_functions/` and `include/ws_protocols/` implement the web-service API and encoders.
- `admin/` contains authenticated administration pages and administrative helpers.
- `install/` and `install.php` implement installation, upgrade, and database migration flows.
- `plugins/`, `themes/`, and `language/` provide extension, presentation, and localization surfaces.
- `local/` contains instance-specific configuration and local overrides and must not enter upstream diffs.
- User requests enter public PHP entry points, load `include/common.inc.php`, then reach page, admin, or web-service handlers.
- Database schema changes are represented by numbered files under `install/db/`.

### Key Directories

- `admin/` — administrative pages and administration helpers.
- `include/` — shared runtime, database, template, user, and API code.
- `install/` — installer, upgrade handlers, and schema migrations.
- `plugins/` — installed or bundled extension surface.
- `themes/` — gallery presentation and templates.
- `language/` — translated message catalogs.
- `local/` — deployment-specific configuration and overrides.
- `tools/` — maintenance, release, translation, and web-service utilities.
- `docs/` — contribution documentation.

### Development Commands

- Install manually with a supported web server, PHP, MySQL or MariaDB, and ImageMagick or GD.
- Follow `docs/CONTRIBUTING.md` for fork, branch, commit, push, and pull-request conventions.
- Run `php -l <path>` for focused syntax validation of changed PHP files.
- No root package manifest, CI workflow, or project-wide automated test command was present in this checkout.

### Code Conventions

- Preserve the existing procedural PHP structure and established include/bootstrap order.
- Keep changes narrow and preserve supported PHP, database, plugin, theme, and localization behavior.
- Use the existing Piwigo validation, access-checking, database, template, and web-service helpers.
- Do not place deployment secrets or instance configuration in tracked upstream changes.
- Follow Piwigo's existing issue-linked commit convention when preparing an upstream contribution.

### Important Files

- `include/common.inc.php` — shared request bootstrap.
- `include/config_default.inc.php` — default runtime configuration.
- `include/ws_core.inc.php` — web-service server, validation, dispatch, and response core.
- `install.php` — installation entry point.
- `admin.php` — administration entry point.
- `SECURITY.md` — vulnerability reporting and supported-version policy.
- `docs/CONTRIBUTING.md` — upstream contribution workflow.

### Runtime, Tooling, and QA

- The supported baseline is the current `master` source with PHP 7.4 or newer and MySQL or MariaDB.
- PHP 7.0 through 7.3 are no longer maintained by the project and must not be treated as secure deployment baselines.
- Security findings require the affected Piwigo, PHP, and MySQL or MariaDB versions in the report.
- Do not publish security details in public issues before responsible disclosure to `security@piwigo.org`.
- Use focused syntax checks and a targeted reproduction when the affected behavior is changed.

### External publication approval

Only an external issue, comment, review, discussion, or pull request write is approval-gated.
Fork commits, pushes, tracking updates, and source implementation follow the active repository contract.

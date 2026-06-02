# AGENTS.md

## Cursor Cloud specific instructions

### Product

Single legacy PHP app: **webSPELL 4.2.3a** (clan/gaming CMS). No Composer, npm, or Docker in-repo. Stack is **PHP + MariaDB/MySQL** only.

### System services (not in update script)

Install once on the VM image or manually:

- `php7.4-cli`, `php7.4-mysqli`, `php7.4-mbstring`, `php7.4-gd` (PHP **8.x** loads the site but breaks login/language handling; use **7.4** for dev)
- `mariadb-server`

Start database before working:

```bash
sudo service mariadb start
```

### Database (local dev defaults)

After setup, `_mysql.php` points at:

- Host: `localhost`
- Database: `webspell`
- User: `webspell` / password: `webspell_dev`
- Table prefix: `ws_`

Admin user: `admin` / `admin123` (created by installer).

Fresh install: browse `http://127.0.0.1:8080/install/` (restore `install/` from `install.bak/` if removed), complete the wizard, then **remove the `install/` directory** (required when `DEBUG` is `OFF` in `_settings.php`).

If CLI install is used, run `fullinstall()` plus all `update*` functions from `install/functions.php` (see setup notes in cloud agent history). Partial migrations cause `Query failed!` on sidebar includes.

### Run the app (development)

```bash
mkdir -p /tmp/php-sessions && chmod 777 /tmp/php-sessions
php7.4 -d session.save_path=/tmp/php-sessions -S 127.0.0.1:8080 -t /workspace
```

Homepage: `http://127.0.0.1:8080/index.php`  
Forum: `http://127.0.0.1:8080/index.php?site=forum`  
Admin (after login): `http://127.0.0.1:8080/admin/admincenter.php`

Login flow: load homepage first (sets session), then submit the sidebar form to `checklogin.php` (`ws_user` / `pwd` fields).

### Writable paths

Installer and uploads need write access on `tmp/`, `demos/`, `downloads/`, `images/` subtrees, and `_mysql.php` during install. See `readme.en.txt` for the full list.

### Lint / tests

No project test suite or linter config. Sanity check:

```bash
find /workspace -maxdepth 1 -name '*.php' -print0 | xargs -0 php7.4 -l
```

### Gotchas

- `install/` must not exist after production install (blocked by `_settings.php` when `DEBUG` is off).
- Built-in PHP server: use a writable `session.save_path` (see command above) so login sessions persist.
- No automated CI; validate by loading pages and logging in as admin.

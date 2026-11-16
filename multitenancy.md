Making the GloggiBox multitenant
===

The same database and same settings are used for all tenants (gloggi as well as Abteilungen).
The only difference between tenants is that we select a different theme based on the domain on which the user accesses
nextcloud. So visiting https://box.gloggi.ch will use the `gloggi` Theme, visiting https://cloud.pfadi-laegern.ch will
use the `laegern` Theme and so on.

- Deploy the contents of the `themes` directory of this repository into the `themes` directory on the server.
- Create `config/theming.config.php` with the following content. Do **not** put this code into `config/config.php`:
  `occ` rewrites `config.php` whenever it changes a setting (e.g. `occ maintenance:mode`) and drops any custom code in it.
  Nextcloud additionally loads all `config/*.config.php` files and merges them over `config.php`, so this file wins.
  ```php
  <?php
  $host = $_SERVER['HTTP_HOST'] ?? 'gloggi.ch';
  $themes = [
    'box.gloggi.ch' => 'gloggi',
    'cloud.gryfensee.ch' => 'gryfensee',
    'cloud.pfadi-laegern.ch' => 'laegern',
  ];
  $CONFIG = [
    'theme' => $themes[$host] ?? 'gloggi',
  ];
  ```
- Give it the same permissions as `config.php` (`chmod 640 theming.config.php`).

## Adding a new domain

1. Ask peaknetworks support to add the domain.
2. Add it to the trusted domains: `$occ config:system:set trusted_domains <next free index> --value=<new-nextcloud-url>`
   (check the existing entries with `$occ config:system:get trusted_domains`).
3. Add a theme to the `themes` directory and map the domain to it in `$themes` in `config/theming.config.php`.
4. In hitobito, ask PBS to add `https://<new-nextcloud-url>/apps/hitobitologin/login/oauth` as an additional redirect URI of the OAuth application.

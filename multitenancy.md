Making the GloggiBox multitenant
===

The same database and same settings are used for all tenants (gloggi as well as Abteilungen).
The only difference between tenants is that we select a different theme based on the domain on which the user accesses
nextcloud. So visiting https://box.gloggi.ch will use the `gloggi` Theme, visiting https://cloud.pfadi-laegern.ch will
use the `laegern` Theme and so on.

- Deploy the contents of the `themes` directory of this repository into the `themes` directory on the server.
- Edit `config/config.php` as follows:
  - Add the following to the top:
    ```php
    $host = $_SERVER['HTTP_HOST'] ?? 'gloggi.ch';
    $themes = [
      'box.gloggi.ch' => 'gloggi',
      'cloud.gryfensee.ch' => 'gryfensee',
      'cloud.pfadi-laegern.ch' => 'gloggi',
    ];
    ```
  - Change the `'theme'` line in the body of `$CONFIG` to the following:
    ```php
    'theme' => $themes[$host] ?? 'gloggi',
    ```

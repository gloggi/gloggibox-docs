# Apps Konfiguriren
- Deaktivierte Apps:
    - File reminders
    - User status
    - Recommendations
    - Forum
    - Office
    - Two-Factor TOTP Provider

- Aktivierte Apps:
    - Team Folders
    - Mail
    - Forms
    - External sites
    - Announcement Banner
    - Hitobito Login
    - Calendar
    - Deck

# Apps Konfiguriren
- Hitobito Login auf der Hitobito instanz redirect URLs als https://<your-nextcloud-instance-url>/apps/hitobitologin/login/oauth ainrichten
- Hitobito Login braucht die "with-Roles" (Optional "event-participations") Scopes die freigegeben sind auf der Hitobito instanz
- Hitobito Login das es richtig funktioniert muss man noch folgendes machen;
    /index.php aus allen URLs entfernen (nötig bevor die Redirect URLs fürs hitobito Login Plugin funktionieren)
    Auf peaknetworks Server mit SSH einloggen
    ~/web/nextcloud/config/config.php bearbeiten und Zeile einfügen: `'htaccess.RewriteBase' => '/',`
    occ="/opt/peak/php85/bin/php /storage/web/<user>/web/nextcloud/occ"
    $occ maintenance:update:htaccess
- Hitobito Login Base-URL, Client-ID & Client-Secret ausfüllen und Login-Button Text auf "Login mit [Deinen Hitobito Name]"
- Hitobito Login optionen Aktivieren:
    - Automaticlly remove groups fram user
    - Block users without mapped group/role match
    - Enable event mapping (needs event_participations scope)
    - Use hitobito as default login
- Hitobito Login Group mapping (& Event mapping) eingeben welche man braucht
- Skeleton dateien mit diesem command deaktivieren:
    $occ config:system:set skeletondirectory –value=""
- Administrator einstellungen:
    - Groupware -> Example content deaktivieren
    - External sites ecamp und MiData link hinzufügen und die icons dazu auch, Die redirect checkbox auch aktivieren sonst funktioniert es nicht
        - ecamp - ecamp_V3_logo.svg - https://app.ecamp3.ch/camps
        - MiData - MiData_logo.svg - https://db.scout.ch/de/users/sign_in
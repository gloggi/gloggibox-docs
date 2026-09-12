Gloggibox + Gloggi Container Hosting Setup
===

## Nextcloud Hosting bei peaknetworks
- https://www.peaknetworks.ch/server-cloud/nextcloud-hosting
- Nextcloud Hosting Small
- Angabe, dass wir externen S3 Speicherplatz verwenden werden
- Darauf warten, dass der peaknetworks Support die Applikation erstellt und sich via Mail meldet

## Container Hosting bei peaknetworks
- blabla

## S3 Speicher bei infomaniak
- https://www.infomaniak.com/en/hosting/public-cloud/prices
- Get started for free
- Public Cloud bestellen, Name `gloggi`
- Identität verifizieren mit infomaniak Check App
- OpenStack Projekt erstellen, Name `gloggi`, OpenStack access password speichern
- Nach Erstellung des Projekts Usernamen `PCU-...` ebenfalls merken
- [openstack CLI client installieren und Credentials einrichten](https://docs.infomaniak.cloud/getting_started/first_project/connect_project/#__tabbed_4_1) (cloud.yaml geht)
- [S3 Credentials erstellen](https://docs.infomaniak.cloud/object_storage/s3/) und speichern
- Um zu S3 zu verbinden:
  - S3 compatible Storage
  - https://s3.pub1.infomaniak.cloud/
  - Region: us-east-1
  - Access Key und Secret Key aus den Credentials
- Mit S3 Client der Wahl ein Bucket erstellen, Name `gloggibox`
- Obige S3 Angaben und Bucket an peaknetworks Support mitteilen

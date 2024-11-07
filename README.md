# Steam Library Updater

Ein Java-basiertes Tool, um die Steam-Bibliothek regelmäßig zu aktualisieren und auf einem zentralen NAS-Speicher zu synchronisieren. Die Anwendung nutzt SteamCMD und die Steam Web API, um alle Spiele eines oder mehrerer Accounts zu laden und auf dem aktuellen Stand zu halten. Das Tool bietet ein Caching-System für die App-IDs, um API-Anfragen zu minimieren und die Anwendung effizient zu gestalten.

## Funktionen

- Synchronisiert die gesamte Steam-Bibliothek eines oder mehrerer Accounts auf einen angegebenen NAS-Pfad.
- Nutzt ein flexibles Update-Intervall für die Bibliotheksaktualisierung.
- Cacht App-IDs lokal und aktualisiert die Liste in einem konfigurierbaren Intervall.

## Voraussetzungen

- **SteamCMD**: Stelle sicher, dass SteamCMD installiert und der Pfad bekannt ist.
- **Java**: Die Anwendung läuft auf Java und benötigt mindestens Java 8.

## Installation

1. **Release herunterladen**  
   Lade die neueste Version des Tools von der [Releases-Seite](https://github.com/yourusername/steam-library-updater/releases) herunter. Das Release enthält:
   - Das ausführbare `.jar`-Dateiformat
   - Die Beispielkonfigurationsdatei `config.yaml`

2. **SteamCMD installieren**  
   Lade SteamCMD herunter und installiere es, falls noch nicht geschehen. [SteamCMD-Download](https://developer.valvesoftware.com/wiki/SteamCMD).

3. **Konfigurationsdatei anpassen**  
   - Öffne die heruntergeladene `config.yaml` und bearbeite sie nach deinen Anforderungen.
   - Füge für jeden Account den Benutzernamen, das Passwort, den API-Key und die Steam-ID hinzu.

   Beispiel für die `config.yaml`:

   ```yaml
   config:
     nas_path: "/path/to/nas/games"
     update_interval_hours: 24
     appid_update_interval_hours: 168  # Aktualisierung der App-ID-Liste alle 7 Tage

   accounts:
     - username: "account1"
       password: "password1"
       api_key: "API_KEY_FOR_ACCOUNT_1"
       steam_id: "STEAM_ID_FOR_ACCOUNT_1"
     - username: "account2"
       password: "password2"
       api_key: "API_KEY_FOR_ACCOUNT_2"
       steam_id: "STEAM_ID_FOR_ACCOUNT_2"
   ````

## Konfiguration

- **nas_path:** Der Pfad, in dem die Steam-Bibliothek gespeichert und aktualisiert wird. Dieser Pfad sollte auf den NAS-Speicher zeigen.

- **update_interval_hours:** Das Intervall für das regelmäßige Bibliotheksupdate in Stunden.

- **appid_update_interval_hours:** Das Intervall für die App-ID-Liste in Stunden. Um API-Beschränkungen zu umgehen, sollte dieses Intervall nicht zu niedrig gewählt werden (siehe Hinweis weiter unten).


## API-Keys und Steam-ID besorgen

1. Steam Web API Key anfordern

- Melde dich bei Steam an.

- Rufe die Steam API Developer Page auf und generiere deinen API-Key.

- Kopiere den API-Key in die config.yaml für jeden Account, der synchronisiert werden soll.



2. Steam-ID des Accounts finden

- Melde dich bei Steam an und öffne dein Profil.

- Kopiere die Steam-ID (eine lange Zahl in der Profil-URL) und füge sie in die config.yaml ein.



## Nutzung

1. Anwendung starten

Doppelklicke auf die heruntergeladene .jar-Datei, um die Anwendung zu starten. Die Anwendung verwendet die Einstellungen aus der config.yaml, um die Steam-Bibliotheken der angegebenen Accounts automatisch zu synchronisieren und regelmäßig zu aktualisieren.



2. Automatische Updates

Das Tool wird regelmäßig im festgelegten Intervall ausgeführt, um die Bibliotheken zu aktualisieren.

Die App-IDs werden ebenfalls im festgelegten appid_update_interval_hours-Intervall aktualisiert.



## Hinweise

**Intervall für App-ID-Cache-Aktualisierung (appid_update_interval_hours):** Der Cache verhindert unnötige API-Anfragen und hilft, API-Beschränkungen zu vermeiden. Ein zu niedriges Intervall könnte dazu führen, dass die API aufgrund zu vieler Anfragen gesperrt wird. Ein Wert von 168 Stunden (eine Woche) wird empfohlen.

**Datensicherheit:** Die Zugangsdaten werden in der Konfigurationsdatei gespeichert. Stelle sicher, dass diese Datei geschützt ist und nicht öffentlich zugänglich gemacht wird, um Missbrauch zu verhindern.

**Fehlerbehebung bei SteamCMD:** Wenn das Tool Probleme hat, sich bei SteamCMD anzumelden, verifiziere die Zugangsdaten und überprüfe, ob SteamCMD ordnungsgemäß installiert ist.


## Lizenz

Dieses Projekt steht unter der MIT-Lizenz.


---
icon: Konsole
---

# Binäre Bereitstellung

Für die Bereitstellung auf einem einzelnen Knoten kann die Ginster-in-One-Einzelbinärdatei verwendet werden.

::: Warnung Für das Szenario mit mehreren Knoten wird die binäre Bereitstellung nicht empfohlen. :::

## Voraussetzungen

Gorse ist von folgender Software abhängig:

- Cache-Speicherdatenbank, eine von *MySQL* , *PostgreSQL* , *MongoDB* oder *Redis* .
- Datenspeicherdatenbank, eine von *MySQL* , *PostgreSQL* , *ClickHouse* oder *MongoDB* .

Die Mindestversionen der abhängigen Software sind wie folgt:

Software | Minimale Version | Kompatibles Produkt
--- | --- | ---
Redis | 5.0 |
MySQL | 5.7 | MariaDB &gt;= 10.2
PostgreSQL | 10.0 |
ClickHouse | 21.10 |
MongoDB | 4.0 |

## Führen Sie Gorse-in-One aus

1. Laden Sie Gorse-in-One von GitHub Release herunter.

::: Code-Tabs#download

@tab:aktives Linux

```bash
# For amd64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_linux_amd64.zip

# For arm64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_linux_arm64.zip
```

@tab macOS

```bash
# For amd64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_amd64.zip

# For arm64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_arm64.zip
```

@tab Windows

```powershell
# For amd64 CPU:

Invoke-WebRequest https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_amd64.zip -OutFile gorse.zip

# For arm64 CPU:

Invoke-WebRequest https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_arm64.zip -OutFile gorse.zip
```

:::

1. Ginster-in-One installieren.

::: Code-Tabs#download

@tab:aktives Linux

```bash
unzip gorse.zip

sudo cp gorse/gorse-in-one /usr/local/bin/gorse
```

@tab macOS

```bash
unzip gorse.zip

sudo cp gorse/gorse-in-one /usr/local/bin/gorse
```

@tab Windows

```powershell
Expand-Archive gorse.zip -DestinationPath gorse
```

:::

1. Erstellen Sie eine Konfigurationsdatei `config.toml` basierend auf [config.toml.template](https://github.com/gorse-io/gorse/blob/release-0.4/config/config.toml.template) .

2. Führen Sie Gorse-in-One aus.

```
gorse -c config.toml
```

### Ginster-in-One-Flaggen

Es gibt Befehlszeilen-Flags für Gorse-in-One:

 | Flagge | Standardwert | Beschreibung
--- | --- | --- | ---
`-c` | `-c,--config` |  | Pfad der Konfigurationsdatei.
 | `--debug` |  | Debug-Protokollmodus.
`-h` | `--help` |  | Hilfe für Ginster-in-One.
 | `--log-path` |  | Pfad der Protokolldatei.
 | `--master-cache-path` | `master_cache.data` | Cache-Pfad des Master-Knotens.
 | `--playground` |  | Spielplatzmodus.
`-v` | `--version` |  | Ginster-Version.
 | `--worker-cache-path` | `worker_cache.data` | Cache-Pfad des Worker-Knotens.
 | `--worker-jobs` | `1` | Arbeitsaufträge des Worker-Knotens.

## Systemd einrichten

1. Kopieren Sie die Gorse-in-One-Binärdatei nach `/usr/local/bin` und die Konfigurationsdateien nach `/etc/gorse` :

```bash
sudo cp ./gorse-in-one /usr/local/bin/gorse
sudo cp config.toml /etc/gorse/
```

1. Erstellen Sie die systemd-Konfigurationsdatei unter `/etc/systemd/system/gorse.service` :

```systemd
[Unit]
Description=Gorse, an open source recommender system service written in Go.
After=network.target

[Service]
Type=simple
Restart=always
ExecStart=/usr/local/bin/gorse -c /etc/gorse/config.toml

[Install]
WantedBy=multi-user.target
```

1. Danach sollten Sie systemd neu laden:

```bash
sudo systemctl daemon-reload
```

1. Starten Sie Gorse-in-one beim Systemstart mit:

```bash
sudo systemctl enable gorse
```

1. Starten Sie Gorse-in-One sofort mit:

```bash
sudo systemctl start gorse
```

1. Überprüfen Sie den Zustand und die Protokolle von Gorse-in-One mit:

```bash
systemctl status clash
```

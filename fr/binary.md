---
icon: console
---

# Binary Deployment

Pour le déploiement d'un nœud unique, le binaire unique Gorse-in-one peut être utilisé.

::: avertissement Pour le scénario multi-nœuds, le déploiement binaire n'est pas recommandé. :::

## Conditions préalables

Gorse dépend des logiciels suivants :

- Cache storage database, one of *MySQL*, *PostgreSQL*, *MongoDB* or *Redis*.
- Base de données de stockage de données, parmi *MySQL* , *PostgreSQL* , *ClickHouse* ou *MongoDB* .

Les versions minimales des logiciels dépendants sont les suivantes :

Logiciel | Version minimale | Produit compatible
--- | --- | ---
Redis | 5.0 |
MySQL | 5.7 | MariaDB &gt;= 10.2
PostgreSQL | 10.0 |
CliquezMaison | 21.10 |
MongoDB | 4.0 |

## Exécutez Gorse en un

1. Téléchargez Gorse-in-one depuis GitHub Release.

::: code-tabs#download

@tab:Linux actif

```bash
# For amd64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_linux_amd64.zip

# For arm64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_linux_arm64.zip
```

@onglet macOS

```bash
# For amd64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_amd64.zip

# For arm64 CPU:

wget -O gorse.zip https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_arm64.zip
```

@onglet Fenêtres

```powershell
# For amd64 CPU:

Invoke-WebRequest https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_amd64.zip -OutFile gorse.zip

# For arm64 CPU:

Invoke-WebRequest https://github.com/gorse-io/gorse/releases/latest/download/gorse_darwin_arm64.zip -OutFile gorse.zip
```

:::

1. Installez Gorse-en-un.

::: code-tabs#téléchargement

@tab:Linux actif

```bash
unzip gorse.zip

sudo cp gorse/gorse-in-one /usr/local/bin/gorse
```

@onglet macOS

```bash
unzip gorse.zip

sudo cp gorse/gorse-in-one /usr/local/bin/gorse
```

@onglet Fenêtres

```powershell
Expand-Archive gorse.zip -DestinationPath gorse
```

:::

1. Créez un fichier de configuration `config.toml` basé sur [config.toml.template](https://github.com/gorse-io/gorse/blob/release-0.4/config/config.toml.template) .

2. Exécutez Gorse-en-un.

```
gorse -c config.toml
```

### Drapeaux d'Ajoncs-en-un

Il existe des drapeaux de ligne de recommandation pour Gorse-in-one :

 | Drapeau | Valeur par défaut | La description
--- | --- | --- | ---
`-c` | `-c,--config` |  | Chemin du fichier de configuration.
 | `--debug` |  | Mode journal de débogage.
`-h` | `--help` |  | Aide pour l'ajonc en un.
 | `--log-path` |  | Chemin du fichier journal.
 | `--master-cache-path` | `master_cache.data` | Chemin du cache du nœud maître.
 | `--playground` |  | Mode aire de jeux.
`-v` | `--version` |  | Version ajonc.
 | `--worker-cache-path` | `worker_cache.data` | Chemin d'accès au cache du noeud worker.
 | `--worker-jobs` | `1` | Tâches de travail du nœud de travail.

## Configurer Systemd

1. Copiez le binaire Gorse-in-one dans `/usr/local/bin` et les fichiers de configuration dans `/etc/gorse` :

```bash
sudo cp ./gorse-in-one /usr/local/bin/gorse
sudo cp config.toml /etc/gorse/
```

1. Créez le fichier de configuration systemd dans `/etc/systemd/system/gorse.service` :

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

1. Après cela, vous êtes censé recharger systemd :

```bash
sudo systemctl daemon-reload
```

1. Lancez Gorse-in-one au démarrage du système avec :

```bash
sudo systemctl enable gorse
```

1. Lancez Gorse-in-one immédiatement avec :

```bash
sudo systemctl start gorse
```

1. Vérifiez la santé et les journaux de Gorse-in-one avec :

```bash
systemctl status clash
```

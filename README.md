# Leadtrunk Claude — marketplace publique

Marketplace publique de plugins Claude Code / Claude Desktop de Leadtrunk.

## Installation

```
claude plugin marketplace add Leadtrunk/Leadtrunk-Claude-Public
```

Ou dans une session interactive : `/plugin marketplace add Leadtrunk/Leadtrunk-Claude-Public`

Puis installer un plugin du catalogue :

```
claude plugin install ltk@leadtrunk-claude
```

## Plugins

| Plugin | Description |
|---|---|
| `ltk` | Rituels de session : ouvrir (`ltk-start`), garder le cap (`ltk-focus`), affûter une demande (`ltk-prompt`), clore par un handoff durable (`ltk-exit`). |
| `ltk-hello` | Plugin de test : commande `/hello-ltk` pour vérifier que l'installation fonctionne. |

## Structure

```
.claude-plugin/marketplace.json   ← catalogue de la marketplace (name: leadtrunk-claude)
plugins/
└── <nom-du-plugin>/
    ├── .claude-plugin/plugin.json
    └── commands/ | skills/
```

## Contribuer un plugin

1. Créer un dossier sous `plugins/<nom-du-plugin>/` avec son `.claude-plugin/plugin.json`.
2. L'ajouter dans la liste `plugins` de `.claude-plugin/marketplace.json`.
3. Commiter et pousser.

## Synchronisation

Ce dépôt est une **publication** : la source de vérité du plugin `ltk` reste le dépôt de
développement. Les corrections descendent toujours dans le sens développement → public,
jamais l'inverse.

⚠️ Ce dépôt est **public** : n'y mettre aucun secret, aucun chemin interne, aucune donnée personnelle.

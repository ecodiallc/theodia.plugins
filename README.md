# theodia.plugins

Official plugin catalog for the Theodia app.

This repository hosts plugin packages (`.plugin.zip`) and a `plugins.json` catalog
so the app can discover and download plugins on demand. No plugins are
pre-bundled in production builds at this time.

## Layout

```
/
├── README.md
├── plugins.json          # Catalog of available plugins
└── <plugin-id>.plugin.zip   # Plugin package zip (latest version)
```

## Catalog

The catalog is published at:

```
https://raw.githubusercontent.com/ecodiallc/theodia.plugins/main/plugins.json
```

Each entry contains:

- `id` — plugin identifier
- `name` — display name
- `version` — latest semver version (from the manifest inside the zip)
- `downloadUrl` — absolute URL to the `.plugin.zip` package
- `minAppVersion` — minimum Theodia app version required
- `description` — short description
- `icon` — URL to the plugin icon (optional)

## Current catalog

| ID | Name | Version | Description |
|---|---|---|---|
| `theodia.test.ai.chapter-sermon` | Sermon Outlines (Test) | 0.1.0 | Generate sermon and teaching outlines from Bible passages |
| `theodia.test.ai.verse-prayer` | Prayer Generator (Test) | 0.1.0 | Generate prayers inspired by Bible passages |
| `theodia.test.chapter` | Test Chapter | 0.2.0 | A test plugin demonstrating chapter-level data and a Theoscript statistics page via the chapter toolbar |
| `theodia.test.db` | Test DB | 0.1.0 | A test plugin with CRUD database |
| `theodia.test.detail` | Test Detail | 0.1.0 | A test plugin demonstrating the detail screen type |
| `theodia.test.flashcards` | Test Flashcards | 0.1.0 | A test plugin providing flashcard data from the legacy flashcards database |
| `theodia.test.html` | Test HTML | 0.1.0 | A minimal test HTML plugin |

## Plugin packages

A `.plugin.zip` file is a zip archive containing the plugin directory contents at
its root: `plugin.json`, `content.json` (for capability plugins), referenced
assets, databases, etc. The plugin version lives only in `plugin.json` and the
`plugins.json` catalog, not in the zip filename.

Set `"active": false` in `plugin.json` to keep a plugin in local development
without publishing it. Inactive plugins are skipped by the packaging script.

## Authoring plugins

See the [plugin manifest schema documentation](https://github.com/ecodiallc/theodia.plugins/wiki) in the repo wiki.

Local development plugins live in the main Theodia repo under
`assets/data/plugins_dev/` and are packaged with:

```bash
# Package all dev plugins (regenerates the full catalog)
npm run package-plugins

# Package only a single plugin (merges its entry into the existing catalog)
npm run package-plugins -- <plugin-id>
```

This produces `.plugin.zip` files and `plugins.json` at the root of the local
clone of this repo, ready to be committed and pushed manually.

To delete a plugin from dev, the clone, and the catalog:

```bash
npm run delete-plugin-dev -- <plugin-id>
```

## Theodia app

Download the app:

- [App Store](https://apps.apple.com/us/app/theodia/id6783143344)
- [Google Play](https://play.google.com/store/apps/details?id=com.ecodia.theodia)

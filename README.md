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
| `test.chapter` | Test Chapter | 0.1.0 | A test plugin demonstrating chapter-level data via the chapter header menu |
| `test.db` | Test DB | 0.1.0 | A test plugin with CRUD database |
| `test.detail` | Test Detail | 0.1.0 | A test plugin demonstrating the detail screen type |
| `test.flashcards` | Flashcards | 0.1.0 | A simple flashcard plugin for testing memory verses |
| `test.html` | Test HTML | 0.1.0 | A minimal test HTML plugin |
| `test.verse` | Test Verse | 0.1.0 | A test plugin demonstrating verse-level data without a database |
| `theodia.prayer` | Prayer Generator | 0.1.0 | Generate prayers inspired by Bible passages |
| `theodia.reading-plans` | Reading Plans | 0.1.0 | Create and manage personalized Bible reading plans |
| `theodia.sermon` | Sermon Outlines | 0.1.0 | Generate sermon and teaching outlines from Bible passages |
| `theodia.study-plans` | Study Plans | 0.1.0 | Create and manage topical Bible study plans |
| `theodia.playlist-starter` | Playlist Starter | 0.1.0 | Starter plugin for the playlist feature |
| `theodia.theoscript-starter` | Theoscript Starter | 0.1.0 | Starter plugin for the theoscript feature |

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
npm run package-plugins
```

This produces `.plugin.zip` files and `plugins.json` at the root of the local
clone of this repo, ready to be committed and pushed manually.

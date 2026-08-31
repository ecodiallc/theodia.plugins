# theodia.plugins

Official plugin catalog for the Theodia app.

This repository hosts plugin packages (`.theoplugin.zip`) and a `plugins.json` catalog
so the app can discover and download plugins on demand. No plugins are
pre-bundled in production builds at this time.

## Layout

```
/
├── README.md
├── plugins.json          # Catalog of available plugins
└── <plugin-id>.theoplugin.zip   # Plugin package zip (latest version)
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
- `downloadUrl` — absolute URL to the `.theoplugin.zip` package
- `minAppVersion` — minimum Theodia app version required
- `description` — short description
- `icon` — URL to the plugin icon (optional)

## Plugin packages

A `.theoplugin.zip` file is a zip archive containing the plugin directory contents at
its root: `plugin.json`, `content.json` (for capability plugins), referenced
assets, databases, etc. The plugin version lives only in `plugin.json` and the
`plugins.json` catalog, not in the zip filename.

## Authoring plugins

See the [plugin manifest schema documentation](https://github.com/ecodiallc/theodia.plugins/wiki) in the repo wiki.

Local development plugins live in the main Theodia repo under
`assets/data/plugins_dev/` and are packaged with:

```bash
npm run package-plugins
```

This produces `.theoplugin.zip` files and `plugins.json` at the root of the local
clone of this repo, ready to be committed and pushed manually.

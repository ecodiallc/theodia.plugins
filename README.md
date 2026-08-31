# theodia.plugins

Official plugin catalog for the Theodia app.

This repository hosts plugin packages (`.theoplugin`) and a `plugins.json` catalog
so the app can discover and download plugins on demand. No plugins are
pre-bundled in production builds at this time.

## Layout

```
/
├── README.md
├── plugins.json          # Catalog of available plugins
└── packages/
    └── <plugin-id>-<version>.theoplugin
```

## Catalog

The catalog is published at:

```
https://raw.githubusercontent.com/ecodiallc/theodia.plugins/main/plugins.json
```

Each entry contains:

- `id` — plugin identifier
- `name` — display name
- `version` — latest semver version
- `downloadUrl` — absolute URL to the `.theoplugin` package
- `minAppVersion` — minimum Theodia app version required
- `description` — short description
- `icon` — URL to the plugin icon (optional)

## Plugin packages

A `.theoplugin` file is a zip archive containing the plugin directory contents at
its root: `plugin.json`, `content.json` (for capability plugins), referenced
assets, databases, etc.

## Authoring plugins

See the [plugin manifest schema documentation](https://github.com/ecodiallc/theodia.plugins/wiki) in the repo wiki.

Local development plugins live in the main Theodia repo under
`assets/data/plugins_dev/` and are packaged with:

```bash
npm run package-plugins
```

This produces `packages/` and `plugins.json` in the local clone of this repo,
ready to be committed and pushed manually.

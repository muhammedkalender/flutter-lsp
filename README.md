# flutter-lsp

**English** | [Türkçe](README.tr.md)

Dart/Flutter language server plugin for [Claude Code](https://claude.com/claude-code). It connects Claude to the Dart analysis server that ships with the Dart and Flutter SDKs, giving it real-time diagnostics, hover, go to definition, find references and symbol search for `.dart` files.

> **Unofficial.** This is a community plugin. It is not made, endorsed or supported by Anthropic, and it is not part of the official Claude Code plugin marketplace.

## Requirements

- Claude Code with plugin support
- The Dart SDK or the Flutter SDK, with `dart` on your `PATH`

Check that the language server is reachable:

```bash
dart language-server --help
```

No extra download is needed: the plugin runs `dart language-server --protocol=lsp` from the SDK you already have.

## Installation

Add this repository as a marketplace, then install the plugin:

```bash
claude plugin marketplace add muhammedkalender/flutter-lsp
```

```bash
claude plugin install flutter-lsp@muhammedkalender
```

Or from inside Claude Code:

```
/plugin marketplace add muhammedkalender/flutter-lsp
/plugin install flutter-lsp@muhammedkalender
```

Restart Claude Code afterwards so the language server is picked up.

## Usage

Nothing to configure. Open a Dart or Flutter project in Claude Code and work as usual:

- After Claude edits a `.dart` file, analyzer errors and warnings are reported back to it automatically.
- Claude can use hover, go to definition, find references, document symbols and workspace symbols instead of text search.

Analysis follows the project's own `analysis_options.yaml` and `pubspec.yaml`. Run `flutter pub get` (or `dart pub get`) first, otherwise unresolved package imports show up as errors.

## Supported extensions

`.dart`

## Troubleshooting

| Problem | Fix |
| --- | --- |
| `Executable not found in $PATH` in the `/plugin` Errors tab | Add the SDK's `bin` directory (for example `flutter/bin`) to `PATH` and restart Claude Code. |
| `server is starting` on the first request | The analysis server needs a few seconds to boot on a cold start. Retry the request. |
| Every `package:` import is an error | Run `flutter pub get` in the project. |
| First analysis of a large project is slow | The server indexes the workspace once; later requests are fast. |

## Updating and removing

```bash
claude plugin marketplace update muhammedkalender
```

```bash
claude plugin uninstall flutter-lsp@muhammedkalender
```

## Repository layout

```
.claude-plugin/marketplace.json            marketplace definition
plugins/flutter-lsp/.claude-plugin/plugin.json   plugin manifest
plugins/flutter-lsp/.lsp.json              language server configuration
```

## License

[MIT](LICENSE). Dart and Flutter are trademarks of Google LLC; Claude is a trademark of Anthropic, PBC. This project is not affiliated with either.

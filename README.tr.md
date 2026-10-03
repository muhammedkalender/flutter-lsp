# flutter-lsp

[English](README.md) | **Türkçe**

[Claude Code](https://claude.com/claude-code) için Dart/Flutter dil sunucusu eklentisi. Claude'u Dart ve Flutter SDK'larıyla birlikte gelen Dart analiz sunucusuna bağlar; `.dart` dosyalarında anlık hata/uyarı bildirimi, hover, tanıma gitme, referans bulma ve sembol araması sağlar.

> **Resmi değildir.** Bu bir topluluk eklentisidir. Anthropic tarafından geliştirilmemiş, onaylanmamış ve desteklenmemektedir; resmi Claude Code eklenti marketinde yer almaz.

## Gereksinimler

- Eklenti desteği olan Claude Code
- Dart SDK veya Flutter SDK (`dart` komutu `PATH` üzerinde olmalı)

Dil sunucusuna erişilebildiğini kontrol edin:

```bash
dart language-server --help
```

Ek bir indirme gerekmez: eklenti, kurulu SDK'daki `dart language-server --protocol=lsp` komutunu çalıştırır.

## Kurulum

Bu depoyu market olarak ekleyin, ardından eklentiyi kurun:

```bash
claude plugin marketplace add muhammedkalender/flutter-lsp
```

```bash
claude plugin install flutter-lsp@muhammedkalender
```

Ya da Claude Code içinden:

```
/plugin marketplace add muhammedkalender/flutter-lsp
/plugin install flutter-lsp@muhammedkalender
```

Dil sunucusunun devreye girmesi için Claude Code'u yeniden başlatın.

## Kullanım

Ayar gerekmez. Bir Dart veya Flutter projesini Claude Code'da açıp normal şekilde çalışın:

- Claude bir `.dart` dosyasını düzenlediğinde analiz hataları ve uyarıları otomatik olarak kendisine bildirilir.
- Claude metin araması yerine hover, tanıma gitme, referans bulma, dosya sembolleri ve çalışma alanı sembollerini kullanabilir.

Analiz, projenin kendi `analysis_options.yaml` ve `pubspec.yaml` dosyalarına göre yapılır. Önce `flutter pub get` (veya `dart pub get`) çalıştırın; aksi halde çözümlenemeyen paket importları hata olarak görünür.

## Desteklenen uzantılar

`.dart`

## Sorun giderme

| Sorun | Çözüm |
| --- | --- |
| `/plugin` Errors sekmesinde `Executable not found in $PATH` | SDK'nın `bin` klasörünü (örn. `flutter/bin`) `PATH`'e ekleyip Claude Code'u yeniden başlatın. |
| İlk istekte `server is starting` hatası | Analiz sunucusunun ilk açılışı birkaç saniye sürer. İsteği tekrarlayın. |
| Tüm `package:` importları hata veriyor | Projede `flutter pub get` çalıştırın. |
| Büyük projede ilk analiz yavaş | Sunucu çalışma alanını bir kez indeksler; sonraki istekler hızlıdır. |

## Güncelleme ve kaldırma

```bash
claude plugin marketplace update muhammedkalender
```

```bash
claude plugin uninstall flutter-lsp@muhammedkalender
```

## Depo yapısı

```
.claude-plugin/marketplace.json            market tanımı
plugins/flutter-lsp/.claude-plugin/plugin.json   eklenti manifesti
plugins/flutter-lsp/.lsp.json              dil sunucusu yapılandırması
```

## Lisans

[MIT](LICENSE). Dart ve Flutter, Google LLC'nin; Claude ise Anthropic, PBC'nin ticari markasıdır. Bu projenin ikisiyle de bir bağı yoktur.

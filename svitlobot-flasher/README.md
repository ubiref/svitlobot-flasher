# SvitloBot Flasher (дві прошивки)

Цей сайт прошиває ESP32‑C3 **з браузера через USB** (WebSerial) за допомогою ESP Web Tools.

## Файли
- `index.html` — сторінка з двома кнопками "Встановити"
- `svitlobot-manifest.json` — маніфест для прошивки SvitloBot
- `healthchecks-manifest.json` — маніфест для прошивки Healthchecks.io
- `svitlobot-merged.bin` — ваш merged binary (покласти в цей каталог)
- `healthchecks-merged.bin` — ваш merged binary (покласти в цей каталог)

## Як підготувати merged .bin
Найзручніше зробити **merged** файл через `esptool.py merge_bin`.

Типовий приклад для ESP32‑C3 (часто так у Arduino/PlatformIO, але перевірте офсети у вашій збірці):
```bash
esptool.py --chip esp32c3 merge_bin -o svitlobot-merged.bin \
  0x0000 bootloader.bin \
  0x8000 partitions.bin \
  0x10000 firmware.bin
```

Аналогічно зробіть `healthchecks-merged.bin`.

## Деплой
Потрібен HTTPS:
- GitHub Pages / Netlify / Cloudflare Pages.

Просто завантажте весь вміст цієї папки на хостинг.

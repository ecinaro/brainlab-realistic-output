# BR(AI)N Lab Realistic Output

Yapay zeka görsellerini "AI gibi durmayan", gerçekten çekilmiş bir fotoğraf gibi gösteren image prompt skill'i. Sinema kadrajı kurmaz, birinin telefonla yakaladığı anı kurar.

Varsayılan cihaz son model iPhone (iPhone 17 Pro). Üç ana sütun: **detay** (ten, el, kıyafet aşınması, nesne ve dolu ortam), **ışık** (tek gerçek kaynak, yön, bounce) ve **kamera** (13 cihazlık banka). Üstüne **opsiyonel kusur katmanı** eklenir: flare, odak kaçması, kadraj hatası, flaş, WhatsApp sıkıştırması gibi 97 fotoğraf kusuru ve 12 hazır paket.

Sadece görseldir: video ve ses yoktur.

## İçindekiler

| Klasör | Ne yapar |
|---|---|
| `brainlab-realistic-output/` | Ana skill: modlar, pipeline, kamera bankası, ışık, detay, an kütüphanesi, gerçeklik hamleleri |
| `brainlab-gercekci-kusurlar/` | Opsiyonel kusur alt-skill'i: fotoğraf kusur kataloğu, cihaz profilleri, paketler |

## Kurulum

İki klasörü de Claude Code skill dizinine kopyala:

```
~/.claude/skills/brainlab-realistic-output
~/.claude/skills/brainlab-gercekci-kusurlar
```

## Kullanım

```
/brainlab-realistic-output yağmurlu akşam otobüs durağında bekleyen kadın
```

Çıktı: Türkçe SHOT BRIEF, DETAY ENVANTERİ, İngilizce PROMPT (60-110 kelime), ardından KUSUR TEKLİFİ. Kusur eklemek için paket adını yaz ("Yağmurlu sokak paketi") ya da `/brainlab-gercekci-kusurlar`. Skill her seferinde numaralı menüyle sorar, sen onaylarsın.

Ayrıntılı kullanım için `brainlab-realistic-output/README.md`.

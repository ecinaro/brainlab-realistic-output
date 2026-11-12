# BR(AI)N Lab Realistic Output

Gerçekten çekilmiş gibi görünen image (görsel) prompt'ları üreten skill. Sadece görsel: video ve ses yok. `brainlab-cinematic-output`'un gerçekçi versiyonu.

## Bu nedir

Cinematic Output bir sinema karesi kurar: kompozisyon kuralları, sinema lensleri, film stock, grade. Realistic Output ise birinin cebinden çıkardığı telefonla yakaladığı anı kurar: o ışıkta, o mesafeden, o insan ve o eşyalarla. Amaç "AI gibi durmayan" kare.

Dört sütun üzerinde çalışır:

| Sütun | Ne yapar |
|---|---|
| **Detay** | Kişisel insan detayı (ten, saç, el, kıyafet aşınması, mikro ifade), nesne detayı, dolu ortam. "Çarpı iki detay" kuralı. |
| **Işık** | Tek ana kaynak, saat, hava, yön, bounce. Işık hep bir yerden gelir ve bir şeye çarpar. |
| **Kamera** | Varsayılan son model iPhone (şu an iPhone 17 Pro, ana 24mm). Bankada Android, kompakt dijital, tek kullanımlık, 35mm film, instax, aynasız, eylem kamerası, bodycam, CCTV, dron, webcam, dashcam (hepsi tek kare olarak). |
| **Kusur** (opsiyonel ek) | `brainlab-gercekci-kusurlar` alt-skill'i: cihaz, lens ve insan kusurları (focus hunting, flare, el titremesi vb.). |

İlk üçü ana skill'dir. Kusur, üstüne istenirse eklenen bir katmandır.

## Ne zaman kullanılır

- Telefonla çekilmiş, candid, UGC, belgesel hissi istediğinde
- "AI gibi durmuyor mu" kaygısı olduğunda, plastik ten ve boş arka plan görüyorsan
- Günlük hayat, sokak, ev, ofis, araç içi, mutfak gibi sıradan ortamlarda
- Bir fotoğrafı tersine mühendislik yapıp aynı gerçeklikte yeniden kurmak istediğinde

Kurulu sinema kadrajı, anamorphic, film stock grade istiyorsan `brainlab-cinematic-output` kullan.

## Nasıl çağrılır

```
/brainlab-realistic-output
```

veya doğal dilde: "gerçekçi prompt yaz", "iPhone ile çekilmiş gibi", "candid", "AI gibi durmasın", "daha gerçekçi görsel".

## Girdiler

| Girdi | Sonuç |
|---|---|
| Sahne, script satırı, fikir | **Mod 1:** metinden prompt'a |
| Yüklenen görsel | **Mod 2:** görselden prompt'a (kamera, ışık, detay, kusur okunur, yeniden kurulur) |
| İsteğe bağlı: cihaz, saat, hava, kim çekiyor | Verilmezse skill kendisi seçer ve brief'te nedenini yazar |

## Çalışma akışı

1. **An:** sahnede ne oluyor, kim çekiyor, neden orada
2. **Kamera:** varsayılan iPhone ana kamera, sahne başka cihaz çağırıyorsa bankadan
3. **Işık:** tek ana kaynak, yön, kalite, renk sıcaklığı, bounce, atmosfer
4. **Detay envanteri:** insan en az 5, nesne en az 3, ortam en az 6, prompt'a en güçlü 6-9
5. **Prompt:** tek blok İngilizce
6. **Kusur teklifi:** tek satır, zorlama yok

## Çıktı

```
SHOT BRIEF          (Türkçe, 3-4 satır)
DETAY ENVANTERİ     (İnsan / Nesne / Ortam, prompt'a girenler kalın)
PROMPT              (İngilizce, tek blok, image için 60-90 kelime)
KUSUR TEKLİFİ       (tek satır)
```

Prompt formülü:

```
[device + lens + grip + height], [moment], [personal human details], [object details], [environment layers], [light: source + direction + quality + bounce + atmosphere], [device processing tells], [aspect ratio]
```

## Kusur alt-skill'i (opsiyonel ek)

`brainlab-gercekci-kusurlar` bu skill'e bağlı ek modüldür.

- **Ana skill onsuz tam çalışır.** Kusur, gerçekçiliği bir kademe daha yükseltmek isteyen için.
- Çağırma: skill çıktısından sonra `/brainlab-gercekci-kusurlar`, "kusur ekle" ya da önerilen paketin adını yaz ("Karşı ışık paketi", "A paketi"). Baştan istenirse "kusurlu olsun".
- **Nasıl görünür:** temiz prompt'un altında KUSUR TEKLİFİ çıkar (3 uygun paket). Evet dersen numaralı menü açılır: PAKETLER (A, B, C) ve TEK TEK maddeler (kod, yoğunluk, neden). "A paketi", "1, 3, 5", "B ama 4'ü çıkar", "5 pronounced olsun" gibi cevap verirsin, kusurlu prompt döner ve Türkçe brief hangi kodların eklendiğini söyler.
- Fotoğraf kusur kataloğunda 9 grup var: PA optik, PB sensör ve işleme, PC odak, PD pozlama, PE operatör ve kadraj, PF çevre ve lens kirliliği, PG flaş, PH çekim sonrası medya (WhatsApp, ekran, basılı fotoğraf), PI cihaz imzaları (film, instax, CCD, IR).
- Kusur skill'i **her seferinde sorar**, madde madde onaylatır, yoğunluğu (`subtle` / `moderate` / `pronounced`) kullanıcı belirler. Bu skill sadece görsel olduğu için ses kusurları (grup K) hiç sorulmaz ve eklenmez.
- Kamera bankasındaki cihaz, kusur kataloğunun kamera tipi profiline otomatik eşlenir (iPhone = Telefon).
- **Fotoğraf modu:** tek karede focus hunting, crash zoom, reframing gibi zaman gerektiren kusurlar önerilmez. Fotoğrafta flare, chromatic aberration, vignetting, motion blur, noise, highlight clipping, lens smudge, imperfect framing gibi olanlar kullanılır.
- Sınır: kıyafet aşınması, ten pürüzü, dağınık oda **detaydır** (ana skill). Cihazın ve operatörün hataları **kusurdur** (alt-skill).

## Dosyalar

| Dosya | İçerik |
|---|---|
| `SKILL.md` | Skill'in kendisi: modlar, pipeline, çıktı formatı, kurallar |
| `references/details.md` | İnsan, nesne ve ortam detay rehberi, hikâye uyumu, plastik görünümü öldüren liste |
| `references/light.md` | Işık senaryoları, karışık ışık, ışık entegrasyonu, telefonun ışığı yorumlaması |
| `references/camera-bank.md` | Kamera bankası ve hızlı cihaz seçim tablosu |
| `references/moments.md` | Kim çekiyor (arkadaş, aile, yabancı, selfie, iş, gözlemci, basın), hangi an yakalandı (20 an tipi), bakış yönü kuralları |
| `references/realism-moves.md` | Gerçeklik hamleleri: yakalanmış kadraj, ölçek, zaman/mevsim, malzeme, gölge tutarlılığı, yazı kuralı, anatomi, yerellik, 10 soruluk plastik kontrol listesi |
| `references/examples.md` | Üç örnek: metinden kare, görselden kare, fotoğraf + kusur katmanı |
| `brainlab-gercekci-kusurlar/references/catalog-still.md` | Fotoğraf kusur kataloğu (PA-PI, ~100 kusur), cihaz profilleri, 12 hazır paket, yoğunluk, çakışma kuralları, soru formatı |
| `README.md` | Bu dosya |

## Kurallar özeti

- Prompt İngilizce, brief Türkçe
- Boş buzzword yok: "8k", "ultra realistic", "masterpiece", "photorealistic"
- Güzelleştirme dili yok: "flawless skin", "airbrushed", "perfect face"
- **Neon yok.** Işık doğal ya da motive edilmiş
- Her detayın hikâyede görevi var
- Tek net odak noktası
- Ekranda yazı, logo, filigran sadece istenirse
- Em dash yok

## Cinematic ile farkı

| | Cinematic Output | Realistic Output |
|---|---|---|
| Rol | Görüntü Yönetmeni | Belgesel fotoğrafçısı ve set giydirmeci |
| Kamera | Arri, RED, IMAX, anamorphic | iPhone varsayılan, bankadan seçim |
| Kompozisyon | Kurulu (üçte bir, simetri, frame-in-frame) | Yakalanmış (kayık, aceleyle, yarım nesne) |
| Işık | Sinema kurulumu (key, fill, rim) | Gerçek tek kaynak, saat ve hava |
| Renk | Grade, film stock | Cihaz işlemesi |
| Doku | Halation, bloom, film grain | HDR kaldırılmış gölge, gürültü azaltma izi |
| Detay | Tabanda | Skill'in kalbi |
| Kusur | Yok | Opsiyonel alt-skill |

## Kurulum

İki klasörü de Claude Code'un skill dizinine kopyala: `~/.claude/skills/brainlab-realistic-output` ve `~/.claude/skills/brainlab-gercekci-kusurlar`. Kusur alt-skill'i aynı dizinde yan yana durur. Windows'ta `~` kullanıcı klasörüdür (`%USERPROFILE%`).

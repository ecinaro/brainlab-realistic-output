# Kamera bankası

Varsayılan cihaz **son model iPhone'un ana kamerası**. Doğrulanan en son model **iPhone 17 Pro** (24mm eşdeğeri ana kamera). Kullanıcı daha yeni bir model söylerse o model yazılır, söylemedikçe 17 Pro. Sahne başka bir cihaz çağırıyorsa aşağıdan seç. Banka açık uçludur: yeni bir cihaz eklenmek istenirse aynı şablonla (Karakter, Lens, Işık davranışı, Tipik izler, Prompt cümlesi) buraya eklenir.

Seçim sorusu: bu anı kim, hangi cihazla, neden çekmiş olabilir? Cihaz seçimi sahnenin sosyal bağlamından çıkar (ev anısı, güvenlik, haber, tatil, iş). Bu skill sadece görseldir, her cihaz tek kare olarak yazılır.

---

## 1. iPhone 17 Pro (varsayılan, son model)

Cihazın işleme karakteri hangi lensi kullanırsan kullan geçerlidir: çoklu kare birleştirme (Smart HDR, Photonic Engine, Deep Fusion) gölgeleri kaldırır, parlak alanları bastırır, yerel kontrastı artırır, dokuyu hafif aşırı keskinleştirir. Ten sıcağa kayar. Karanlıkta gürültü silinir ve yüzey sulu boya gibi yağlanır. Dosya HEIC, ekranda parlak ve doygun görünür.

17 Pro'da üç arka kameranın üçü de 48MP.

| Lens | Eşdeğer odak | Ne zaman | Karakter |
|---|---|---|---|
| **Ultra wide** | ~13mm, f/2.2, 48MP | Dar mekân, araba içi, kalabalık, selfie çubuğu | Kenarlarda gerilen yüzler, güçlü perspektif, hafif barrel distortion, kenarlarda yumuşama, yakın odak (makro) mümkün |
| **Ana (1x)** | ~24mm, f/1.78, 48MP | Varsayılan her şey | Derin alan, doğal perspektif, çok hafif arka plan düşüşü sadece yakın mesafede |
| **2x (ana sensör kırpması)** | ~48mm | İnsan portresi, sokak | Daha az distorsiyon, hâlâ derin alan, optik kalitede kırpma |
| **Tele 4x** | ~100mm, f/2.8, 48MP | Uzaktan candid, sahne, spor | Sıkışmış arka plan, daha dar diyafram yüzünden loş ışıkta gürültü ve yumuşaklık |
| **8x (tele kırpması)** | ~200mm | Çok uzaktan çalınmış kare | Belirgin yumuşaklık, ince dokuda yağlanma, hafif titrek netlik |
| **Selfie (ön, 18MP)** | geniş, kol boyu mesafe | Selfie | Hafif geniş yüz, ten düzleştirme, arkada genelde fazla aydınlık |

Model sorulursa: "iPhone 17 Pro". Daha yeni model verilirse lens eşdeğerlerini doğrula, emin değilsen sadece "iPhone main camera" yaz.

**Tipik izler (gerçeklik işaretleri):**
- Pencere ya da güneş yönünde patlayan highlight, yanında yumuşak halka
- Parlak kaynağa dönükken ekranın karşı tarafında soluk yeşil ya da mor hayalet orb flare
- Portre modunda saç ve gözlük kenarında yanlış blur maskesi
- Night modunda uzun pozlama yumuşaklığı, hareket eden elde hayalet iz

**Prompt cümlesi:**
`candid handheld photo shot on iPhone 17 Pro, main camera 24mm equivalent, chest height, Smart HDR lifted shadows`

Lens varyantları: `iPhone 17 Pro ultra wide 13mm equivalent`, `iPhone 17 Pro 2x, 48mm equivalent`, `iPhone 17 Pro 4x telephoto 100mm equivalent`, `iPhone 17 Pro 8x crop, 200mm equivalent`, `iPhone 17 Pro front camera selfie`.

---

## 2. Android amiral gemisi (Pixel, Samsung)

- **Karakter:** iPhone'dan daha agresif HDR ve keskinlik, doygun gökyüzü ve yeşil, Samsung'da sıcak/parlak ten, Pixel'de nötr ve kontrastlı.
- **Lens:** ana ~23-24mm, ultra wide ~13-15mm.
- **Tipik izler:** halo çevresinde keskinleştirme, gökyüzünde bant ve kontrast, kenarlarda beauty yumuşatma (selfie).
- **Prompt cümlesi:** `candid Android flagship phone photo, main camera, aggressive HDR and punchy local contrast, slight over-sharpening`

## 3. 2000'ler kompakt dijital (Canon IXUS, Casio Exilim, Sony Cyber-shot)

- **Karakter:** küçük CCD sensör, düşük dinamik aralık, flaşla düz aydınlatma, sert gölge arkaya yapışır.
- **Lens:** ~35-105mm zoom, f/2.8-f/5.6.
- **Tipik izler:** doğrudan flaşla parlayan alın ve burun, kırmızı göz, patlayan arka plan, mor fringe, JPEG sıkıştırma, doygun kırmızı, çözünürlük düşük.
- **Prompt cümlesi:** `2000s compact digital camera snapshot, on-camera flash flattening the face, dark background falling off, CCD color, JPEG compression`

## 4. Tek kullanımlık film kamerası (Kodak FunSaver, Fuji QuickSnap)

- **Karakter:** sabit plastik lens (~27-34mm, f/10 civarı), yerleşik flaş, sıcak ve doygun renk, iri grain.
- **Tipik izler:** flaşın aydınlattığı özne ile kararan arka plan, vignette, yumuşak köşeler, ışık sızması, tarama yapılmış baskı hissi.
- **Prompt cümlesi:** `disposable film camera snapshot, direct flash on subject with dark falloff behind, soft plastic lens corners, coarse color grain, light vignette`

## 5. 35mm film SLR/rangefinder (Canon AE-1, Pentax K1000, Leica M)

- **Karakter:** 50mm f/1.8 ya da 35mm f/2, stok seçimi belirleyici: Portra 400 (doğal ten, sıcak), Kodak Gold (sarı-sıcak, nostalji), Tri-X (siyah beyaz, kontrast), Ektar (doygun).
- **Tipik izler:** hafif odak kaçırma, doğal grain, tarama tozu, kırmızı halation parlak noktalarda, ışık sızması kenarda.
- **Prompt cümlesi:** `35mm film photograph, 50mm f/1.8, Kodak Portra 400, natural grain, slight focus miss, scan dust`

## 6. Instax / Polaroid

- **Karakter:** sabit lens, otomatik flaş, düşük kontrast, kayık renk, kare ya da dikdörtgen çerçeve ve kenar.
- **Tipik izler:** yumuşak odak, patlayan highlight, mavi-yeşil ya da sarı kayma, kenarda kimyasal leke.
- **Prompt cümlesi:** `instant film snapshot, direct flash, soft focus, faded color shift, chemical edge`

## 7. DSLR/aynasız belgesel (Sony A7, Canon R, Nikon Z)

- **Karakter:** 35mm f/1.8 ya da 24-70 f/2.8, RAW'dan çıkmış nötr doku, gerçek sığ alan, doğal bokeh. Haber, düğün, etkinlik.
- **Tipik izler:** gerçek odak düzlemi, yüz keskin kulak yumuşak, ayrı ayrı flaş (bounce flaş tavandan), ISO gürültüsü, tavan lambası vurmuş WB.
- **Prompt cümlesi:** `documentary mirrorless photo, 35mm f/1.8, shallow natural depth of field, bounce flash from ceiling, high-ISO noise in shadows`

## 8. Eylem kamerası (GoPro, DJI Action), tek kare

- **Karakter:** ~16-24mm ultra geniş, güçlü barrel distortion, sonsuz odak derinliği.
- **Tipik izler:** balıkgözü kenar, yağmur damlası, lens üstü su, çok doygun renk.
- **Prompt cümlesi:** `action camera still, ultra-wide lens, strong edge distortion, deep focus`

## 9. Bodycam

- **Karakter:** göğüs hizası sabit, geniş açı, düşük çözünürlük, sert sıkıştırma, zaman damgası (sadece istenirse).
- **Tipik izler:** hareketli kadraj, yukarı doğru kesilen yüzler, karanlıkta macroblocking, patlayan far ışığı.
- **Prompt cümlesi:** `bodycam still frame, chest-height wide angle, heavy compression, blown headlight highlights, low resolution`

## 10. CCTV / güvenlik kamerası / kapı zili (Ring)

- **Karakter:** tepeden ya da köşeden sabit, geniş açı, düşük bit hızı, gece IR modunda siyah beyaz.
- **Tipik izler:** yüz küçük, hareket bulanık, gece gri yeşil, tavan lambası altında patlama, geniş distorsiyon.
- **Prompt cümlesi:** `fixed high-corner security camera still, wide-angle distortion, low bitrate compression, grainy night IR`

## 11. Dron (DJI Mavic/Mini)

- **Karakter:** ~24mm eşdeğeri, küçük sensör, sabit f/2.8.
- **Tipik izler:** yukarıdan yatık ufuk, rüzgârlı sallantı, yüksek kontrast gökyüzü, pervane gölgesi nadiren.
- **Prompt cümlesi:** `aerial drone photo, 24mm equivalent small sensor, slightly clipped sky`

## 12. Webcam / laptop kamera (ekran görüntüsü karesi)

- **Karakter:** 720p-1080p, sabit geniş, ekran ışığı yüz düzeltici, arkada aşırı pozlanmış pencere.
- **Tipik izler:** ten düşük kontrast ve soluk, kenarlarda gürültü, ekrandan düz mavi ışık, kafa kesilmiş kadraj.
- **Prompt cümlesi:** `laptop webcam frame, 1080p, flat blue-white screen light on the face, blown window behind, slight noise`

## 13. Araç kamerası (dashcam), tek kare

- **Karakter:** ön cam arkasında sabit, geniş, düşük bit hızı, WDR.
- **Tipik izler:** cam yansıması, kontrast değişimi, far parlaması, yağmur silecek.
- **Prompt cümlesi:** `dashcam frame, wide fixed lens, windshield reflection at the bottom, WDR contrast shift, low bitrate`

---

## Cihaz seçim tablosu (hızlı)

| Sahne | Önerilen cihaz |
|---|---|
| Günlük hayat, sokak, kafe, ev | iPhone ana kamera |
| Selfie | iPhone ön / webcam |
| Gece, parti, flaşlı | Kompakt dijital / tek kullanımlık / iPhone flaş |
| Nostalji, aile albümü | 35mm film / tek kullanımlık / instax |
| Haber, etkinlik, düğün | Aynasız belgesel |
| Spor, risk, hareket | Eylem kamerası |
| Güvenlik, delil, korku | CCTV / bodycam / kapı zili |
| Manzara, gayrimenkul | Dron / iPhone ultra wide |

## Kusur alt-skill'iyle eşleşme

`brainlab-gercekci-kusurlar` kataloğundaki kamera tipi profilleri bu bankanın üstüne oturur: iPhone ve Android = **Telefon**, bodycam = **Bodycam**, eylem kamerası = **GoPro**, CCTV ve kapı zili = **CCTV**, dron = **Drone**, aynasız ve 35mm = **Sinema kamerası** profilinin odak ve lens kısımları (hareket kusurları fotoğrafa uygulanmaz). Kompakt dijital, tek kullanımlık ve instax için katalogda ayrı profil yok: Telefon profilinin D, E, G grupları ve aşağıdaki izler kullanılır.

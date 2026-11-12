# Örnek çıktılar

Bu dosya doğru çıktı seviyesini kalibre etmek için. Kopyalamak için değil, seviye ölçmek için oku.

---

## Örnek 1: Mod 1, tek kare (metinden prompt'a)

**Girdi:** "Gece vardiyasından çıkan hemşire sabah otobüs durağında bekliyor."

**SHOT BRIEF**
An: vardiya çıkışı, kimse onu çekmeye hazırlamıyor. Kamera: iPhone ana kamera, göğüs hizası, durakta yanında bekleyen birinin aceleyle çektiği kare. Işık: sabah 7'nin alçak kış güneşi, durak camından soldan. Kilit detaylar: pili bitmiş yüz, yarım kalmış simit, buruşuk forma. Bunlar karakterin gününü tek bakışta anlatıyor.

**DETAY ENVANTERİ**
- İnsan: **buruşuk teal forma**, **soyulan fotoğraflı hastane kartı**, **kaçan tutamlı gevşek toka**, **yanağında yastık izi**, kuru dudak, **soyulmuş oje**
- Nesne: **kâğıt bardak kahve**, **peçeteye sarılı yarım simit**, çizik zaman çizelgesi
- Ortam: **ıslak sticker kaplı bank**, **durak camında parmak izleri**, **kaldırımda su birikintisi**, arkada geçen servis, afiş köşesi kıvrık, çöp kutusu taşmış

**PROMPT**
```
Candid handheld iPhone photo, main camera 24mm equivalent, chest height, a night-shift nurse in her thirties waiting at a bus stop at 7 a.m., creased teal scrubs under an open grey parka, hospital lanyard with a peeling badge photo, loose hair clip with flyaway strands, faint pillow crease on one cheek, chipped nail polish around a paper coffee cup, half-eaten simit in a napkin, sticker-covered wet bench and fingerprinted shelter glass behind her. Low winter sun from camera-left through the glass, cool pavement bounce under her chin, visible breath in the cold air, Smart HDR lifting the shadow side, 4:5
```

**KUSUR TEKLİFİ**
İstersen /brainlab-gercekci-kusurlar ile iPhone'a özgü hataları da ekleyebiliriz (hafif flare, imperfect framing).

---

## Örnek 2: Mod 2 (görselden prompt'a)

**Girdi:** Kullanıcı, gece arabada yan koltuktan çekilmiş, direksiyondaki bir adamın fotoğrafını yüklüyor.

**OKUNAN KATMANLAR**
- Kamera: iPhone ultra wide ya da ana, yakın mesafe, hafif barrel distortion, yüzde hafif genişleme. Elde, göğüs hizası altı.
- Işık: torpido ekranından gelen soğuk mavi-beyaz tek kaynak aşağıdan, sokak lambası ön camdan kesik şeritler.
- Detay: adamın yanağında tıraş kaçığı, alnında ter parlaması, gömlek yakasında leke, aynada asılı tespih, torpidoda makbuz yığını.
- Kusur (zaten var): ön camda yansıma, sağ üstte yumuşak yeşil flare orb, bulanık hareket.
- Duygusal etki: yorgunluk ve yalnızlık. Mavi ekran ışığı yüzü çürümüş gösteriyor, yansımalar adamı dünyadan ayırıyor.

**PROMPT**
```
Candid iPhone photo from the passenger seat at night, wide camera at hip height, a man in his forties gripping the steering wheel, unevenly shaved jaw with a missed patch under the ear, sweat shine on the forehead, stained shirt collar, a wooden prayer-bead strand swaying from the mirror, crumpled receipts piled on the dashboard. Cold blue-white light from the dashboard screen below his chin, sodium streetlight cutting broken stripes across the windshield, faint reflection on the glass, phone HDR lifting the shadows into a grey noise, 4:5
```

---

## Örnek 3: Fotoğraf + kusur katmanı

**Girdi:** "Meydanda keman çalan sokak sanatçısı, uzaktan çekilmiş."

**SHOT BRIEF**
Kamera: iPhone 5x tele, meydanın karşısından, göğüs hizası. Işık: alçak kış güneşi sağdan, direğin arkasında. Detay: eldivende yama, kemanda reçine tozu, açık kemanlıkta bozuk paralar.

**PROMPT (temiz)**
```
Candid handheld iPhone photo, 5x telephoto 120mm equivalent, from across a plaza, a street violinist in a worn wool coat mid-bow, rosin dust on the strings, fingerless gloves with a darned thumb, open instrument case with scattered coins and a thermos, pigeons on the cobbles, a tram stop pole behind him. Low winter sun from camera-right behind a lamppost, cold shadow side filled by pale stone bounce, visible breath, 4:5
```

**KUSUR KATMANI (kullanıcı onayladı)**

Kusur skill'inin akışı çalıştı. Fotoğraf modunda geçerli olanlar onaylandı:
1. A7 imperfect framing, moderate: sanatçı ortada değil.
2. E2 foreground occlusion, subtle: bir yabancının omzu sol kenarı kapatıyor.
3. B5 odak kayması, subtle: odak yay elinde, yüz hafif yumuşak.
4. C4 flare, subtle: güneşin karşısında soluk yeşil orb.
5. D6 highlight clipping, moderate: gökyüzü beyaza patlıyor.

**PROMPT (kusurlu)**
```
Candid handheld iPhone photo, 5x telephoto 120mm equivalent, from across a plaza, a street violinist in a worn wool coat mid-bow, rosin dust on the strings, fingerless gloves with a darned thumb, open instrument case with scattered coins and a thermos, pigeons on the cobbles, a tram stop pole behind him. Low winter sun from camera-right behind a lamppost, cold shadow side filled by pale stone bounce, visible breath. Slightly off-center framing with a stranger's shoulder partly covering the left edge, focus resting a touch on the bow hand with the face slightly soft, a faint green flare orb opposite the sun, the pale sky clipping to white, 4:5
```

---

## Kalibrasyon notları

- Her prompt'ta ışık yönü açıkça bir kaynağa bağlanmış olmalı. "Soft light" yazmak başarısızlıktır.
- Bounce cümlesi olmayan prompt eksiktir.
- Envanter brief'te tam, prompt'ta seçilmiş. Prompt 60-90 kelime civarı (görselde).
- Her detay karakterin gününü anlatır. Rastgele "ilginç" detay yok.
- Kusur sütunu ana skill'e karışmaz, ayrı katmandır ve her zaman sorulur.
- Neon, güzelleştirme dili ve boş buzzword yok.

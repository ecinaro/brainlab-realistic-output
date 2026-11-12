---
name: brainlab-gercekci-kusurlar
description: Video ve image (fotoğraf) prompt'lara gerçekçi kamera, lens, sensör, medya ve operatör kusurları ekler; sahneyi daha doğal, daha "gerçekten çekilmiş" gösterir. Üç şekilde çalışır. (1) Sıfırdan, bir sahne ya da fikirden kusurlu detaylı video prompt yazar. (2) Başka bir video prompt skill'inin (sd25-pe, brainlab-cinematic-output, brainlab-realistic-output, brainlab-timed-video-prompt, seedance-prompter vb.) çıktısını analiz edip aralara önemli kusurları yerleştirir. (3) Kullanıcının yapıştırdığı hazır bir video prompt'a eksik kusurları ekler. Her seferinde, eklemeden önce hangi kusurların eklenmesini istediğini tek tek sorar. Ses kusurlarını sadece kullanıcı isterse ekler. MUTLAKA tetikle. "/brainlab-gercekci-kusurlar", "gerçekçi kusurlar", "kusur ekle", "daha gerçekçi yap", "handheld hissi ver", "daha doğal görünsün", "camcorder hissi", "found footage", "bu prompt'a kusur ekle", "odak kayması ekle", "kamera titremesi ekle", "AI hissi gitsin", "fazla temiz görünüyor", "bu çok kritik", "bunu daha belirgin yap", "bu sesi de ekle", bir sahneye revizyon ya da feedback verildiğinde (kritik detaylara özel dikkat gösterir), ya da kullanıcı bir video prompt'un fazla steril, fazla mükemmel ya da yapay durduğunu söylediğinde.
---

# Brainlab Gerçekçi Kusurlar

Yapay zeka videoları fazla temiz, fazla mükemmel ve fazla ortalanmış çıkar. Gerçek kamera ise hep bir şeyi kaçırır: odağı arar, kadraj kayar, ışığa girince pozlama şaşar, el titrer. Bu skill o kusurları prompt'a bilinçli, ölçülü ve nedenli şekilde yerleştirir.

**Prompt çıktıları İngilizce, brief ve sorular kullanıcının dilinde (Türkçe).**

Kusur kataloğu, hazır İngilizce cümleler ve kamera tipi profilleri `references/catalog.md` dosyasında. Bu dosyayı her video çalışmasında oku. **Çıktı tek karelik görsel (image prompt) ise** video kataloğu yerine `references/catalog-still.md` okunur: fotoğraf kodları (PA-PI), cihaz profilleri, hazır kusur paketleri ve soru formatı orada.

## Üç mod

**Mod 1, sıfırdan:** Kullanıcı sahne ya da fikir verir. Sahneyi kur, kusurları sor, kusurlu detaylı video prompt'u yaz.

**Mod 2, katman:** Başka bir video prompt skill'i prompt üretmiştir ya da üretecektir. O skill önce çalışır, bu skill sonra. Çıktıyı analiz et, kusurları sor, aralara yerleştir. Diğer skill'in yapısını bozma.

**Mod 3, hazır prompt:** Kullanıcı bir prompt yapıştırır. Aynı akış, prompt'un kendi yapısı korunur.

Kullanıcı hangi modda olduğunu söylemediyse girdiden çıkar. Sahne ya da fikir varsa Mod 1, başka bir skill'in çıktısı ya da yapıştırılmış prompt varsa Mod 2 ve 3. Emin değilsen sorma, en yakın modu seç.

## Akış

### 1. Analiz et

Prompt'u ya da sahneyi okuyup şunları çıkar:

- **Kamera tipi:** VHS camcorder, telefon, bodycam, GoPro, CCTV, drone, sinema kamerası. Belirtilmemişse sahnenin dilinden çıkar (found footage, ev videosu vb.), çıkaramıyorsan sinema kamerası varsay.
- **Plan ve aşamalar:** Kaç plan ya da aşama var, her birinde ne oluyor.
- **Ana özne:** Okunabilir kalması gereken kişi, nesne ya da olay.
- **Işık ve ortam:** Gece mi, ateş mi, gün ışığı mı, iç mekân mı. Hangi kusurların nedeni var (ışık değişimi, hareket, hava).
- **Mevcut kusurlar:** Prompt'ta zaten yazılı olan her kusuru not et. Bunları tekrar önerme.
- **Kamera hareketi:** Kamera tripodda mı, elde mi, hareket halinde mi. Çelişen kusur önerme (tripod ile handheld shake gibi).

### 2. Sor (zorunlu, her seferinde)

Hiçbir zaman sormadan prompt'a kusur ekleme. Ekleyeceğin kusurlara kullanıcı karar verir, kusur bütçesini de bu seçim belirler.

**Soru formatı:** Analizden çıkan önerileri numaralı bir liste olarak sun. Her madde tek başına onaylanabilir ya da reddedilebilir olmalı. Her maddede şunlar olsun:

- Kusurun adı
- Hangi planda ya da aşamada olacağı
- Önerilen yoğunluk (`subtle` / `moderate` / `pronounced`)
- Neden bu sahneye uyduğu (tek kısa cümle)

Örnek:

```
Bu sahne için şu kusurları öneriyorum. Hangilerini ekleyelim?

Aşama 1 (uzaktan geniş çekim)
1. Micro-jitter, subtle: kamera elde, çok küçük sarsıntı canlılık verir.
2. Camera drift, subtle: operatör kadrajı sabit tutamıyor gibi olur.
3. Imperfect framing, moderate: Fatih tam ortada değil, hafif sağda.

Aşama 2 (zoom)
4. Crash zoom, pronounced: sahnenin ana hareketi bu.
5. Autofocus hunting, moderate: zoom sırasında odak arar.
6. Motion blur, subtle: zoom'un hızı bulanıklık yaratır.
```

Kullanıcı numaralarla cevaplayabilir ("1, 3, 4, 6"), yoğunluk değiştirebilir ("5 numara pronounced olsun") ya da kendi eklemek istediğini söyleyebilir. Önerilen listeye ek olarak "listede olmayan başka bir şey eklemek ister misin?" diye kısaca sor.

**Ses kusurları ayrı sorulur.** Ses kusurlarını (katalogda grup K) önerme, listeye koyma. Önce şunu sor: "Ses kusurları da ekleyelim mi?" Kullanıcı evet derse ses kusurlarını ayrı bir numaralı liste olarak sun ve aynı şekilde tek tek onaylat. Hayır derse hiç ekleme.

**Bütçe uyarısı:** Seçilen kusur sayısı bir planda 6'yı aşıyorsa tek cümleyle uyar: "Bu planda çok kusur toplandı, sahne ucuz görünebilir. Bazılarını çıkarmak ister misin?" Karar yine kullanıcının, ısrar ederse hepsini ekle.

**Sorma istisnası:** Kullanıcı o mesajda açıkça "sorma", "direkt ekle" ya da "sen karar ver" derse sormadan en uygun kusurları seç, sesleri yine ekleme (sadece "sesi de ekle" derse ekle) ve seçtiklerini çıktının sonunda listele. Bu izin sadece o mesaj için geçerlidir, bir sonrakinde yine sor.

### 3. Yaz

Onaylanan kusurları katalogdaki hazır İngilizce cümlelerden uyarlayarak prompt'a yerleştir. Yerleştirme kuralları:

- **Plan plan ya da aşama aşama yaz.** Kusur hangi plana aitse o planın içinde dursun. Tüm kusurları tek bir genel cümleye yığma.
- **Her kusuru sahnedeki bir nedenle bağla.** "Autofocus hunting" yerine "autofocus hunts briefly as the zoom races toward the face, then locks".
- **Dozu mutlaka yaz.** `subtle`, `slight`, `brief`, `no exaggerated` gibi sınırlayıcılar kullan. Sınırlayıcısız kusur abartıya kaçar.
- **Sıralama ve süre belirt.** Kusurun sahnede ne zaman başlayıp ne zaman bittiğini yaz ("for a moment", "settles by the end of the zoom").
- **Kusuru görüntü diliyle yaz, olumsuzlama olarak yazma.** "No clean tripod shot" yerine "slight handheld drift".
- **Mevcut yapıyı koru.** Başka bir skill'in çıktısında referans etiketleri (`@Image1`), asset rolleri, aşama ya da timestamp yapısı, diyalog ve kamera kararları aynen kalır.

### 4. Çıktı

**Mod 1:** Tam video prompt, İngilizce, tek blok. Ardından Türkçe kısa brief: hangi kusurlar eklendi ve nerede.

**Mod 2 ve 3:** Diğer skill'in prompt formatında, kusurlar eklenmiş tam prompt. Kusurlar iki yerden birine yazılır:

- Prompt'ta ayrı bölümler varsa yeni bir `【Realistic Imperfections】` bölümü eklenir, her aşama için ayrı satırla.
- Düz paragraf formatındaysa ilgili kamera ve görüntü cümlelerinin içine işlenir.

Ardından Türkçe kısa brief: eklenen kusurlar ve yerleri.

Seedance prompt'larında ses kusurları (onaylandıysa) `<>` sembolüyle yazılır, örneğin `<faint wind rumble on the microphone>`.

## Revizyon ve feedback modu (kritik detaylar)

Kullanıcı bir sahne hakkında revizyon ya da feedback verdiğinde ("bu çok kritik", "özellikle", "mutlaka olsun", "şunu daha belirgin yap", "şu ses de olsun", "bunu duymak istiyorum") o sahnede söylenen kusurlar ve detaylar **kritik detay** sayılır. Bu detaylara özel dikkat gösterilir:

1. **Yakala ve listele.** Kullanıcının feedback'inde geçen her kusuru ve detayı (görsel, hareket, ses) kendi sözleriyle not et. Hiçbirini atlama, yumuşatma ya da genel bir ifadeye çevirme.
2. **Eş zamanlı yaz.** Kritik detay görüntüde, olay akışında ve sesinde karşılığı olan bir şeyse hepsine aynı anda işle. Örnek: suyun kameraya çarpması hem Aşama 2 olay satırında (nedeniyle birlikte), hem `【Realistic Imperfections】` bölümünde (görsel etki), hem de `【Sound】` bölümünde (çarpma ve damlama sesi) yer alır. Zoom back motoru hem hareketin kendisinde hem sesinde yer alır.
3. **Yoğunluğu bir kademe yükselt.** Kritik detay `subtle` ya da `moderate` ise bir üst kademeye çıkar (`moderate`, `pronounced` olur). Sesler "faint" yerine "loud, clearly audible" gibi belirgin yazılır. Kullanıcı "çok kritik" dediyse en yüksek kademede yaz.
4. **Prompt'ta öne çıkar.** Prompt'a `【Critical Details】` adlı kısa bir bölüm ekle. Her kritik detayı bir satırda yaz ve "must be clearly visible" ya da "must be clearly audible" ile bağla. `【Maintain Consistency】` bölümüne de "bu detayların sahnede mutlaka kalması" cümlesini ekle.
5. **Revizyondan revizyona taşı.** Kritik detaylar sonraki revizyonlarda da aynen kalır. Kullanıcı kaldır demedikçe seyreltme, kısaltma ya da başka bir kusurun lehine silme.
6. **Sormadan ekle.** Kullanıcı bu detayları kendi söylediği için bu maddeler için onay sorma. Listeden onaylatma akışı sadece yeni önerdiğin kusurlar için geçerlidir. Çıktıdaki Türkçe brief'te her kritik detayın prompt'ta nereye yazıldığını belirt.
7. **Okunabilirlik yine korunur.** Kritik detay yoğun olsa da ana özne tanınabilir kalır. Örneğin yüze çarpan su görüntüyü bozar ama özne bozulmuş görüntüde seçilebilir kalır ve kısa sürede açılır.
8. **Çakışma olursa sor.** İki kritik detay birbirini engelliyorsa (aynı anda aynı yerde) kısaca hangisine öncelik verileceğini sor.

## brainlab-realistic-output ile bağ ve fotoğraf (still) modu

Bu skill, `brainlab-realistic-output` skill'inin opsiyonel kusur katmanıdır. Realistic-output temiz ve gerçekçi prompt'u üretir, kullanıcı isterse bu skill üstüne kusur ekler. Akış Mod 2'dir (diğer skill önce, bu skill sonra) ve ana kurallar aynen geçerlidir: her seferinde sor, okunabilirliği koru. Realistic-output'tan çağrıldığında ses kusurları (grup K) hiç sorulmaz ve eklenmez, çünkü o skill sadece görseldir. Ses sorusu yalnızca bu skill doğrudan video prompt'u için çağrıldığında geçerlidir.

Realistic-output'un kamera bankasındaki cihaz, buradaki kamera tipi profiline eşlenir: iPhone ve Android = Telefon, bodycam = Bodycam, eylem kamerası = GoPro, CCTV ve kapı zili = CCTV, dron = Drone, camcorder = VHS camcorder. Kompakt dijital, tek kullanımlık film ve instax için ayrı profil yok: Telefon profilinin D, E, G grupları kullanılır, F1 ile F5 (VHS) kullanılmaz.

**Fotoğraf (still) modu:** çıktı video değil tek karelik görselse `references/catalog-still.md` kullanılır. Zaman ve hareket gerektiren kusurlar (autofocus hunting, crash zoom, snap zoom, reframing, rack focus, camera drift, zoom breathing, auto-exposure kayması) önerilmez. **Ses kusurları (grup K) fotoğrafta hiç sorulmaz, önerilmez, eklenmez.** Akış aynıdır, her seferinde sorulur, ama menüde tek tek maddelerin yanı sıra kataloğun sonundaki **kusur paketleri** (Cepten çıkan an, Karşı ışık, Gece iPhone, Parti flaşı vb.) de seçenek olarak sunulur. Fotoğraf başına en fazla 5 kusur, 6 ve üstünde uyarı. Onaylanan kusurlar ayrı bölüm olmadan prompt'un ışık ve kadraj cümlelerinin içine, kısa ve sınırlayıcılı yazılır, 60-110 kelime sınırı korunur. Hareket kusuru gerekiyorsa tek karede hareket bulanıklığı (PC4) olarak yazılır.

## Katı kurallar

- Her çalışmada, eklemeden önce sor. Revizyon ve feedback'te kullanıcının kendi söylediği kritik detaylar istisnadır, onlar sormadan eklenir. Tek istisna yukarıdaki "sorma" izni.
- Ses kusurları sadece kullanıcı "evet" derse eklenir.
- **Okunabilirlik önceliği:** Ana özne her zaman okunur kalır. Kafa kadrajda, yüz kusurla tamamen kapanmaz, obje taşıp özneyi kapatmaz. Kusur anlatıyı ezmez.
- **Çakışma kontrolü:** Prompt'ta zaten olan kusuru tekrar yazma, birbiriyle çelişenleri birlikte kullanma (tripod ile handheld, rack focus ile "tüm kadraj keskin" gibi).
- **Kamera tipi uyumu:** VHS camcorder'a sinema lensi kusuru (anamorphic oval bokeh) ya da sinema kamerasına VHS tracking çizgisi ekleme. Katalogdaki kamera tipi tablosuna uy.
- **Motivasyon:** Her kusurun sahnede bir nedeni olmalı. Nedeni yoksa önerme.
- **Tarih damgası ve REC göstergesi** sadece kullanıcı isterse. Ekran üstü yazı kuralı: kullanıcı istemedikçe subtitle, logo, watermark ekleme.
- Boş buzzword ("ultra realistic", "8k", "masterpiece", "hyper detailed") yazma. Gerçekçilik, somut kusurlarla anlatılır.
- Kusurlar sahnenin olay örgüsünü, karakter sayısını, kostümü ve kompozisyon kararlarını değiştirmez.
- Em dash kullanma.

# LLM Test - DumpAnalyzer

Uygulamanızdaki hataları bulup düzeltmek için yapılandırılmış yapay zeka destekli hata ayıklama aracı.

## 📋 Proje Açıklaması

**DumpAnalyzer** proje, Windows dump dosyalarını analiz ederek uygulamalardaki sorunları systematik bir şekilde teşhis etmeye ve çözmeye yardımcı olan bir AI ajanıdır. WinDbg komutları ve detaylı hata ayıklama teknikleri kullanarak stack trace'ler, kilitlenmeler Ve bellek sızıntılarını çözmede uzmanlaşmıştır.

## 🎯 Amaç

- Dump dosyalarındaki kilitlenmeleri (crash) analiz etme
- Stack trace'leri inceleme ve hata kaynağını bulma
- Bellek sızıntıları ve kaynak yönetimi sorunlarını tanımlama
- Systematik bir şekilde hataları düzeltme
- Regression testleri ile çözümleri doğrulama

## 🚀 Başlangıç

### Gereksinimler
- Windows Kits 10 veya üzeri
- CDB (Debugger) kurulu: `C:\Program Files\Windows Kits\10\Debuggers\x64\cdb.exe`
- Dump dosyası (.DMP)
- Symbol dosyaları (isteğe bağlı ancak önerilir)

### Temel Kullanım

1. Dump dosyasını TESPİT edin
2. Aşağıdaki yolu takip ederek çünkü yapılandış yapın:
   - `.github/agents/DumpAnalyzer.agent.md` dosyasını kontrol edin
   - Hata ayıklama işlemini başlatın

## 📊 Hata Ayıklama Süreci

Proje 4 aşamadan oluşan systematik bir hata ayıklama metodolojisi follows:

### Faz 1: Problem Değerlendirmesi
- Bağlamı anlama
- Hatayı reproduksiyon etme
- Detaylı hata raporu hazırlama

### Faz 2: Araştırma
- Root cause analizi
- Hipotez oluşturma
- Doğrulama planları

### Faz 3: Çözüm
- Fix implementasyonu
- Doğrulama testleri
- Regression kontrol

### Faz 4: Kalite Güvence
- Kod kalitesi kontrolü
- Test ekleme/güncelleme
- Belgelendirme

## 🔧 Temel WinDbg Komutları

| Komut | İşlev |
|-------|--------|
| `!analyze -v` | Detaylı kilitlenme analizi |
| `k` | Stack trace görüntüleme |
| `lm` | Yüklü modülleri listeleme |
| `dv` | Yerel değişkenleri gösterme |
| `!threads` | Tüm threadleri listeleme |
| `!peb` | Process Environment Block'u gösterme |
| `!handle` | Handle bilgilerini gösterme |
| `!locks` | Kilit bilgilerini gösterme |
| `!heap` | Heap kullanımını gösterme |
| `!vm` | Virtual memory bilgilerini gösterme |
| `!error` | Son hata kodunu gösterme |
| `!sym noisy` | Verbose symbol yükleme etkinleştirme |

## 📁 Proje Yapısı

```
10_LLM_Test/
├── .github/
│   └── agents/
│       └── DumpAnalyzer.agent.md    # AI Ajanı Yapılandırması
├── Cubes.png                         # Proje görseli
└── README.md                         # Bu dosya
```

## 💡 En İyi Uygulamalar

### Debugging İçin
- ✅ Hatayı anlamadan fix yapmayın
- ✅ Her adımı dokümante edin
- ✅ Küçük, test edilebilir değişiklikler yapın
- ✅ Edge case'leri düşünün
- ✅ Tüm testleri çalıştırın

### Symbol Dosyaları
- Doğru symbol dosyalarını kullanın
- `!sym noisy` ile symbol yüklemesini debug edin
- PDB dosyalarını güncel tutun

### Performance
- `!vm` ve `!heap` komutları ile bellek analizi yapın
- Thread deadlock'larını `!locks` ile kontrol edin
- Resource leak'leri `!handle` ile tespit edin

## 🔍 Örnek Dump Dosyası

```
Örnek konum: C:\Codes\CoPilotApp\Demos\08-WindbgFilter\DumpAnalyser\w3wp-allproducts.DMP
```

## 📝 Çıktı Örneği

Başarılı bir debug seansı sonunda şunları alacaksınız:
- **Root Cause Analizi**: Hatanın temel sebebi
- **Fix Açıklaması**: Yapılan değişiklikler
- **Doğrulama Raporu**: Test sonuçları
- **Önlemler**: Benzer hataları önleme yolları

## 🛠️ .NET Uygulamaları Debugging

.NET uygulamalarını debug ederken:
- `!soshelp` komutu ile SOS debugging komutlarını listeleyin
- `.NET Framework` ve `.NET Core` arasındaki farkları göz önüne alın
- Managed heap sorunları için `!heap` komutunu kullanın

## 📞 Destek ve Kontrol Listesi

Debugging sırasında kontrol edin:
- [ ] Dump dosyası mevcut mu?
- [ ] Symbol dosyaları doğru mu?
- [ ] CDB.exe doğru konumda mı?
- [ ] Tüm relevant modüller stack trace'te mi?
- [ ] Değişken değerleri beklenilen şekilde mi?
- [ ] Thread kilit (deadlock) yok mu?
- [ ] Bellek sızıntısı semptomları var mı?

## 🎓 Kaynaklar

- Windows Kits Debuggers: https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/
- WinDbg Commands: https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugger-commands
- .NET Debugging: https://docs.microsoft.com/en-us/dotnet/core/diagnostics/

## 📦 Versiyon

**Sürüm**: 1.0  
**Son Güncelleme**: Şubat 2026

---

**Not**: Bu proje AI tabanlı hata ayıklama asistanı olarak tasarlanmıştır. Karmaşık debugging senaryoları için detaylı dump dosyası ve symbol bilgileri sağlayınız.

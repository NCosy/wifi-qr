# Wi-Fi QR Oluşturucu

Wi-Fi ağ bilgilerinden QR kod üreten tek dosyalık bir web aracı. QR'ı telefon kamerasına
okutan kişi şifreyi elle yazmadan ağa bağlanır — misafirler için pratik, buzdolabına
yazdırıp asmak için ideal.

**Her şey tarayıcıda çalışır.** Sunucu yok, istek yok, analytics yok. Girdiğiniz ağ adı
ve şifre bilgisayarınızdan hiçbir yere gitmez.

## Canlı demo

**https://ncosy.github.io/wifi-qr/**

Ya da `index.html` dosyasını indirip çift tıklayın — kurulum gerekmez.

## Özellikler

- **WPA/WPA2/WPA3, WEP ve şifresiz** ağ desteği
- **Gizli ağ** (SSID yayını kapalı) seçeneği
- Yazarken anında QR önizleme
- **PNG indir** — paylaşmak veya saklamak için
- **Yazdır** — ağ adıyla birlikte temiz bir çıktı
- Şifrede geçen `\ ; , : "` gibi özel karakterler doğru şekilde kaçışlanır
- Mobil uyumlu arayüz, bağımlılığı yok (QR üretimi için tek bir CDN script'i hariç)

## Kullanım

1. **Wi-Fi adı (SSID)** alanına ağ adını modemde yazdığı gibi yazın — büyük/küçük harf önemli.
2. **Şifre** alanını doldurun. Doğru yazdığınızdan emin olmak için "Şifreyi göster"i işaretleyebilirsiniz.
3. **Güvenlik türü**nü seçin. Çoğu modern modemde doğru seçenek WPA'dır.
4. Ağınız gizliyse **"Bu ağ gizli"** kutusunu işaretleyin.
5. QR sağ panelde görünür. **PNG indir** veya **Yazdır**.

### Telefonla okutma

| Platform | Nasıl |
|---|---|
| iPhone / iPad (iOS 11+) | Kamerayı açın, QR'a doğrultun, çıkan **"Ağa Katıl"** bildirimine dokunun. |
| Android (10+) | Kamerayı QR'a doğrultun ya da **Google Lens** kullanın, çıkan Wi-Fi bağlantısına dokunun. |

## Nasıl çalışıyor

QR kodun içine standart Wi-Fi bağlantı dizesi gömülür:

```
WIFI:T:WPA;S:AgAdi;P:sifre;H:true;;
```

`T` güvenlik türü, `S` ağ adı, `P` şifre, `H` ise ağın gizli olup olmadığı.
Telefon işletim sistemleri bu formatı tanıyıp bağlantıyı kendisi kurar.

QR üretimi için [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator)
kütüphanesi kullanılır (cdnjs üzerinden), hata düzeltme seviyesi **M**.

## Güvenlik notu

QR kodu, Wi-Fi şifrenizi **düz metin olarak** taşır. Kodu okutabilen herkes şifreyi de
okuyabilir. Bu yüzden:

- Üretilen PNG'leri herkese açık bir yere (repo, sosyal medya, web sitesi) koymayın.
- Yazdırdığınız çıktıyı misafirlerinizin görmesini istediğiniz yerde tutun, sokağa bakan
  bir vitrinde değil.
- Bu repodaki `.gitignore`, kazara commit'lenmesini önlemek için `wifi-*.png`
  dosyalarını dışarıda bırakır.

## Lisans

MIT — `LICENSE` dosyasına bakın.

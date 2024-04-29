# Like-atanlari-kopyalama-Virgül

### ADIM 1

<p>- Facebook dilini Türkçe yap</p>
<p>- Tampermonkey eklentisi tarayıcınıza ekleyin</p>
<p>- Yeni Betik oluştura tıklayın</p>

![image](https://github.com/DenizKod/ARK-ISTEGI-IPTAL-ETME/assets/168285638/7e1b2696-803e-447a-ae3f-f7844a44d28f)

### Aşağıdaki kodu kopyala yeni betik sayfasındaki tüm kodları baştan sona sil ve bunu ekle.
```
// ==UserScript==
// @name         Facebook Beğeni Listesi Kopyalayıcı - F4 ile Kopyala, Virgülle Ayır
// @namespace    http://tampermonkey.net/
// @version      0.3
// @description  Facebook postlarında F4 tuşu ile beğeni yapan kullanıcıların isimlerini virgülle ayırarak kopyala
// @author       You
// @match        www.facebook.com/groups/bgyagain3*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    // Klavye olayını dinle
    document.addEventListener('keydown', function(e) {
        // F4 tuşuna basıldığında işlemi gerçekleştir
        if (e.key === 'F4') {
            e.preventDefault();  // F4'ün varsayılan işlevini engelle

            // Beğeni yapanların listesini seç
            var likeList = document.querySelectorAll('div[data-visualcompletion="ignore-dynamic"] a[role="link"]');
            var names = [];
            likeList.forEach(function(user) {
                // İsimleri al ve boşluklardan temizle
                var name = user.getAttribute("aria-label");
                if (name && name !== "Herkesi görmek için bağlantı") {  // spesifik metni hariç tut
                    name = name.trim();  // trim işlemi burada yapılıyor
                    if (name) {
                        names.push(name);
                    }
                }
            });

            // İsimleri virgülle ayırarak panoya kopyala
            var formattedNames = names.join(', ');
            navigator.clipboard.writeText(formattedNames).then(function() {
                alert("Başarıyla kopyalandı: " + names.length + " kullanıcı.");
            }, function() {
                alert("Kopyalama başarısız!");
            });
        }
    });
})();
```
## NASIL ÇALIŞIR?

<p>- Grupta herhangi bir posta gir ve like atanlar kısmını aç</p>
<p>- En aşağı kadar kaydır</p>
<p>- En aşağı indiğinde like kutusuna kapanmayacak şekilde 1 kere tıkla</p>
<p>- F4 tuşuna 1 kere bas</p>

![image](https://github.com/DenizKod/Like-atanlari-kopyalama-1/assets/168285638/98702393-18e4-4093-8ae3-e339936bbde8)


(kodun içindeki bu kısım; kodun hangi sayfada çalışacağını belirler)</p>
![image](https://github.com/DenizKod/Like-atanlari-kopyalama-1/assets/168285638/e757b9c2-c263-40fb-9e74-3ac2c3d325f9)


<p>- www.facebook.com/groups/gamingbgy2* sadece gaming'de çalışır</p>
<p>- www.facebook.com/groups/bgystonks2* sadece Stonks grubunda çalşışır</p>
<p>- www.facebook.com/profile.php?id=100079957152392* Ömer Serdar Özkan Profilinde çalışır<p>
<p>- www.facebook.com Tüm facebook üzerinde çalışır.</p>

<p>başka grupta kullanmak istiyorsan TEK YAPMAN GEREKEN @MATCH kısmındaki linki değiştirmek.</p>

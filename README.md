# FACEBOOK LİKE ATANLARIN İSİMLERİNİ VİRGÜL VİRGÜL AYIRARAK KOPYALAMA

### ADIM 1

<p>- Facebook dilini Türkçe yap</p>
<p>- Tampermonkey eklentisi tarayıcınıza ekleyin</p>
<p>- Yeni Betik oluştura tıklayın</p>

![image](https://github.com/DenizKod/ARK-ISTEGI-IPTAL-ETME/assets/168285638/7e1b2696-803e-447a-ae3f-f7844a44d28f) ![image](https://github.com/DenizKod/Facebook-Gonderiye-Like-Atanlarin-Ismini-Kopyala/assets/168285638/75139f78-5bf0-4191-be69-c22be4a2602b)


### Aşağıdaki kodu kopyala yeni betik sayfasındaki tüm kodları baştan sona sil ve bunu ekle.
```
// ==UserScript==
// @name         Facebook Beğeni Listesi Kopyalayıcı - F4 ile Kopyala
// @namespace    http://tampermonkey.net/
// @description  Facebook postlarında F4 tuşu ile beğeni yapan kullanıcıların isimlerini düzgün bir şekilde kopyala
// @match        *.facebook.com/*
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


# LİKE ATANLARIN İSİMLERİNİ ALT ALTA OLACAK ŞEKİLDE KOPYALAMA

![image](https://github.com/DenizKod/Facebook-Gonderiye-Like-Atanlarin-Ismini-Kopyala/assets/168285638/821cf9d7-4798-42f5-b8e6-26d15a0cb419)


```
// ==UserScript==
// @name         Facebook Beğeni Listesi Kopyalayıcı - F4 ile Kopyala
// @namespace    http://tampermonkey.net/
// @description  Facebook postlarında F4 tuşu ile beğeni yapan kullanıcıların isimlerini düzgün bir şekilde kopyala
// @match        *.facebook.com/*
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
                    names.push(name);
                }
            });

            // İsimleri panoya kopyala
            navigator.clipboard.writeText(names.join('\n')).then(function() {
                alert("Başarıyla kopyalandı: " + names.length + " kullanıcı.");
            }, function() {
                alert("Kopyalama başarısız!");
            });
        }
    });
})();
```

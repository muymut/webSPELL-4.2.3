# Rümeysa Okuma Yazma Öğreniyor — Kısa Animasyon Film

Kitap kapağından esinlenen, tarayıcıda oynayan yaklaşık 50 saniyelik pastel boya
tarzında bir kısa animasyon film. Harici hiçbir kütüphane gerektirmez; tek bir
HTML dosyasından oluşur (SVG + CSS animasyonları + hafif JavaScript zamanlayıcı).

## Hazır video

Tarayıcı açmadan izlemek için `rumeysa-film.mp4` dosyası da mevcut
(720x1080, 30 fps, ~53 saniye).

## Nasıl izlenir?

`index.html` dosyasını herhangi bir modern tarayıcıda açın ve
**"Filmi Başlat"** düğmesine tıklayın. Film bitince **"Tekrar Oynat"** ile
yeniden izleyebilirsiniz.

```bash
# isterseniz basit bir sunucuyla da açabilirsiniz
cd rumeysa-animasyon
python3 -m http.server 8080
# tarayıcıda: http://localhost:8080
```

## Sahneler

1. **Gün doğumu** — Gülümseyen güneş yükselir, bulutlar süzülür, filmin adı belirir.
2. **Anne ve Rümeysa** — Anne minik Rümeysa'yı kucağına alır; A, B, C, Ç, Ğ harfleri etraflarında dans eder, kalpler uçuşur.
3. **Harfler kitaba konar** — Harfler uçarak açık kitabın sayfalarına konar, kitap ışıldar.
4. **Kalem yazıyor** — Sarı kurşun kalem deftere harf harf "Rümeysa" yazar.
5. **Kutlama ve SON** — Çiçekler açar, harf konfetileri yağar: "Aferin Rümeysa!"

Her sahneye Türkçe alt yazı eşlik eder.

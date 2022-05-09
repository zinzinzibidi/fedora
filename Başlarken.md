# Fedora'ya Başlarken

Bu md dosyası Fedora işletim sistemine yeni başlayanlara destek olmak amacıyla hazırlanmıştır. Fedora 35 ve sonrası için uygundur.

<br>

## 1. İşletim Sistemi Güncelleme
Terminal'e aşağıdaki kodları yazıyoruz ve sırasıyla çalıştırıyoruz. (Kodun üzerine gelip sağındaki simge ile tek tıkla kopyalayabilirsiniz.)

```
sudo dnf update --refresh -y
```
```
sudo dnf upgrade --refresh -y
```

Terminale kodları copy + paste yaparken CTRL + V'ye izin vermemekte. Bu sebeple CTRL + SHIFT + V yapabilirsiniz.

update güncelleme dosyalarını indiriyor. upgrade ise kuruyor.

<br>

## 2. RPMFusion ve Flatpack Kurulumu

Fedora'nın yazılım kütüphanesi yetersizdir. Bu iki dağıtım Microsoft Edge, Visual Studio Code, PyCharm gibi tonlarca programı Software'e ekler. Bu şekilde kod yazmadan birçok yazılımı kurabiliriz.

Terminale sırasıyla

```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

yazıyoruz ve kurulumları gerçekleştiriyoruz.[^1][^2]

[^1]:[FlatPak](https://flatpak.org/setup/Fedora)

[^2]:[RPMFusion](https://rpmfusion.org/Configuration)

<br>

## 3. Wi-Fi Adapter Kurulumu

Kurulum sonrası Wi-Fi çalışmazsa aşağıdaki adımları uyguluyoruz.

Terminale

```
sudo reboot
```
yazın ve işletim sistemini tekrar başlatın. Settings'ten Wi-Fi ayarlarını kontrol edin.

Wi-Fi Adapter (Wireless Driver), RPMFusion ve Flatpack'ten sonra kurulmazsa aşağıdakileri uygulayabilirsiniz.[^3]

Terminal'e
```
lspci | grep -i net
``` 
yazıyoruz ve Wi-Fi Adapter'ı kuruyoruz.[^4]

[^3]:Kurulum sırasında kablolu bağlantı gereklidir. 

[^4]:Çalışmazsa [şuradaki](https://ask.fedoraproject.org/t/fedora-33-does-not-recognise-wifi-of-laptop/11399/2) kodları deneyebilirsiniz.

<br>

## 4. Dock Sabitleme
<ol>
  <li>GNOME Shell Extentions eklentisi Edge'e ya da Firefox'a kuruyoruz.</li>
  <li>Dash to Dock eklentisini google'layıp kuruyoruz.</li>
  <li>Extensions'ı açıyoruz ve ayarlamaları yapıyoruz.</li>
</ol>

<br>

## 5. Gnome Tweaks Kurulumu ve 1.75 Ekran Ölçeklendirme

4K çözünürlük kullanıyorsanız ekran ölçeklendirme gerekebilir.

Software'den Gnome Tweaks'i kuruyoruz.

<img src="https://zinzinzibidi.com/img/fedora-scale.png" alt="fedora scale" style="width:480px"/>

Fonts > Scaling Factor'den ayarları 1.75 yapabilirsiniz.

Ya da

Oturum açılışında parola sorduğunda sağ alt köşedeki çark simgesine tıklayıp "GNOME on Wayland"i seçebilirsiniz. Display ayarlarına %150, %175 seçenekleri gelecektir. Fakat NVIDIA düzgün çalışmayabilir. Bazı uygulamaları iyi render'lamayabilir ve bulanık gösterebilir.

Gnome Tweak ile koyu tema da kullanabilirsiniz.[^5]

[^5]:Fedora 36 ile koyu tema özelliği gelecektir.

<br>

## 6. Codec'ler
Multimedya codec'leri için Terminal'e aşağıdaki kodları yazıyoruz.[^6]

```
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel

sudo dnf install lame\* --exclude=lame-devel

sudo dnf group upgrade --with-optional Multimedia
```
[^6]:[Kaynak](https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/)

<br>

## 7. Windows Fontları Yükleme
Windows'tan gelen bazı dosyalar, özellikle Word belgeleri, fontlar yüzünden düzgün gösterilmeyebilir. Bu sebeple Windows fontlarını kullanmalıyız.

Files'ın sol konsolunun en altında bulunan +Other Locations'a tıklıyoruz. Windows > Fonts klasörü içindeki fontları kopyalıyoruz. Fedora'da gizli dosyaları gösteriyoruz ve Home klasörünün içinde .Font adlı yeni bir klasör oluşturup kopyaladığımız fontları buraya yapıştırıyoruz.

<br>

## 8. Masaüstünde Nesne Kullanma

Masaüstünde klasör, belge kullanabilmek için [Desktop Icons NG (DING) ](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/) eklentisi kurulabilir. Bu eklentiyi kurabilmek için daha önce [GNOME Shell Extensions](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep?hl=tr)
kurulmalıdır. (Firefox için [tıklayınız](https://addons.mozilla.org/tr/firefox/addon/gnome-shell-integration/).)

<br>

## 9. Topluluk Desteği

Bu belgedeki birçok konu Reddit topluluğu sayesinde hazırlandı. Sorun yaşadığınız her konuda [Fedora Subredditi](https://www.reddit.com/r/Fedora/)'ni kullanabilirsiniz. Çok sağlam bir community'si var.

<br>

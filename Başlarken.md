Fedora 35 ve sonrası için hazırlanmıştır.


## 1. İşletim Sistemi Güncelleme
Terminal'e aşağıdaki kodları yazıyoruz ve sırasıyla çalıştırıyoruz.

```
sudo dnf update --refresh -y
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


flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

yazıyoruz ve kurulumları gerçekleştiriyoruz.[^1][^2]

[^1]:[FlatPak](https://flatpak.org/setup/Fedora)

[^2]:[RPMFusion](https://rpmfusion.org/Configuration)

<br>

## 3. Wi-Fi Adapter Kurulumu

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
  <li>GNOME Shell Extentions eklentisi Edge'e ya da Firefox'a kuruyoruz./li>
  <li>Dash to Dock eklentisini google'layıp kuruyoruz./li>
  <li>Extensions'ı açıyoruz ve ayarlamaları yapıyoruz.</li>
</ol>

<br>

## 5. Gnome Tweaks Kurulumu ve 1.75 Ekran Ölçeklendirme
Software'den Gnome Tweaks'i kuruyoruz.

![fedora](https://zinzinzibidi.com/img/fedora-scale.png)

Fonts > Scaling Factor'den 1.75 yapabilirsin.

Ya da

![[wayland.jpg]]
Oturum açılışında parola sorduğunda sağ alt köşedeki çark simgesine tıklayıp "GNOME on Wayland"i seçebilirsin. Display ayarlarına %150, %175 seçenekleri gelecektir. Fakat NVIDIA düzgün çalışmayabilir. Bazı uygulamaları iyi render'lamıyor. Bulanık gösteriyor.

##### Codec'ler
Terminal'e aşağıdaki kodları yaz.

```
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel

sudo dnf install lame\* --exclude=lame-devel

sudo dnf group upgrade --with-optional Multimedia
```
[Kaynak](https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/)

##### Windows Fontları Yükleme
Windows > Fonts klasörü içindeki fontları kopyala. Gizli dosyaları göster ve Home klasörünün içinde .Font adlı yeni bir klasör oluştur. Fontları buraya yükle.




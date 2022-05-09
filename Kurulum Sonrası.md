
##### İşletim Sistemi Güncelleme
Terminale aşağıdaki kodları yaz.

```
sudo dnf update --refresh -y
sudo dnf upgrade --refresh -y
```

Terminale copy + paste yaparken CTRL + SHIFT + V yap. Direkt kodları yapıştırıyor.

##### RPMFusion ve Flatpack Kurulumu
Terminale

```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm


flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

yaz. [Kaynak](https://flatpak.org/setup/Fedora)[Kaynak2](https://rpmfusion.org/Configuration)

Software (Yazılımdan) VS Code, PyCharm, Obsidian, Microsoft Edge gibi birçok yazılımı kurmaya yarıyor.

##### Wi-Fi Adapter Kulumu
Wi-Fi Adapter RPMFusion ve Flatpack'ten sonra kurulmazsa aşağıdakileri uygula.

Terminal'e **inxi -Nxx** yaz.
[Kaynak](https://ask.fedoraproject.org/t/fedora-33-does-not-recognise-wifi-of-laptop/11399/2)
(Kurulum için kablolu bağlantı gerekli.)

Çalışmazsa kaynak'taki kodları dene.

##### Dock Sabitleme
GNOME Shell Extentions eklentisi Edge'e ya da Firefox'a kur.
Dash to Dock eklentsini google'a ve kur.
Extensions'u aç ve ayarlamaları yap.
##### Gnome Tweaks Kurulumu ve 1.75 Ekran Ölçeklendirme
Software'den Gnome Tweaks'i kur.

![[Pasted image 20220508202917.png]]

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




# Fedora'ya Başlarken

Bu md dosyası Fedora işletim sistemine yeni başlayanlara destek olması amacıyla hazırlanmıştır. Fedora 35 ve sonrası için uygundur.

<br>

## 1. Arama Özelliği 
İşletim sisteminde kurulu herhangi bir yazılıma ve özelliğe ulaşmak için Super Key'e (Windows ya da Elma logolu klavye tuşuna) bir kez basıldıktan sonra bulunmak istenen uygulama adının yazılması yeterlidir. WinKey + Calc gibi... (Hesap makinesi bulunabilecektir.)

<br>

## 2. İşletim Sisteminin Güncellemesi ve Yükseltilmesi
Fedora her 6 ayda bir yeni versiyon için güncellenmektedir. İşletim sistemini güncel tutmak için Terminal'e aşağıdaki kodları yazıyoruz ve sırasıyla çalıştırıyoruz. (Aşağıdaki kodun üzerine gelince sağ tarafta beliren kopyalama simgesini kullanabilirsiniz.)

```
sudo dnf update --refresh -y
```
```
sudo dnf upgrade --refresh -y
```

Terminale kodları yapıştırırken CTRL + V'ye izin vermemektedir. Bu sebeple CTRL + SHIFT + V kullanılmalıdır. Ya da sağ tıkla yapıştır yapabilirsiniz.

update güncelleme dosyalarını kontrol etmek, upgrade ise kurmak için kullanılmaktadır.

<br>

## 3. RPMFusion ve Flatpack Kurulumu
Fedora'nın yazılım kütüphanesi yetersizdir. Bu iki dağıtım Microsoft Edge, Visual Studio Code, PyCharm gibi tonlarca programı Software'e ekler. Bu şekilde kod yazmadan birçok yazılımı kurabilirsiniz.

Software, yazılımların kurulabildiği kütüphanedir. Winkey + Software ile erişebilirsiniz.

Terminale sırasıyla

```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

yazabilir ve kurulumları gerçekleştirebilirsiniz.[^1][^2]

[^1]:[FlatPak](https://flatpak.org/setup/Fedora)

[^2]:[RPMFusion](https://rpmfusion.org/Configuration)

<br>

## 4. Wi-Fi Adapter Kurulumu
Kurulum sonrası Wi-Fi çalışmazsa aşağıdaki adımları uygulayabilirsiniz.

Terminale

```
sudo reboot
```
yazılır ve işletim sistemini tekrar başlatılır. Settings'ten Wi-Fi ayarları kontrol edilir.

Wi-Fi Adapter (Wireless Driver), RPMFusion ve Flatpack'ten sonra hala kurulu değilse aşağıdaki adımlar uygulanır.[^3]

Terminal'e
```
lspci | grep -i net
``` 
yazılır ve Wi-Fi Adapter kurulur.[^4]

[^3]:Kurulum sırasında kablolu bağlantı gereklidir. 

[^4]:Çalışmazsa [şuradaki](https://ask.fedoraproject.org/t/fedora-33-does-not-recognise-wifi-of-laptop/11399/2) kodlar denenmelidir.

<br>

## 5. Dock Sabitleme
<ol>
  <li>GNOME Shell Extentions (https://addons.mozilla.org/tr/firefox/addon/gnome-shell-integration/) Edge'e ya da Firefox'a kurulur.</li>
  <li>Dash to Dock (https://extensions.gnome.org/extension/307/dash-to-dock/) eklenti kurulur.</li>
  <li>Süper Key + Extensions ile Extensions açılır. Gerekli ayarlamalar yapılır.</li>
</ol>

<img src="https://zinzinzibidi.com/img/fedora-extensions.png" alt="fedora extensions" style="width:480px"/>

<br>

## 6. Gnome Tweaks Kurulumu ve 1.75 Ekran Ölçeklendirme

4K çözünürlük kullanıyorsanız ekran ölçeklendirme gerekebilir.

Software'den Gnome Tweaks'i kurulur.

<img src="https://zinzinzibidi.com/img/tweaks-fonts.png" alt="fedora scale" style="width:600px"/>

Fonts > Scaling Factor'den ayarları 1.75, 1,80 yapabilirsiniz.

Ya da

Oturum açılışında parola sorduğunda sağ alt köşedeki çark simgesine tıklayıp "GNOME on Wayland"i seçebilirsiniz. Display ayarlarına %150, %175 seçenekleri gelecektir. Fakat NVIDIA düzgün çalışmayabilir. Bazı uygulamaları iyi render'lamayabilir ve bulanık gösterebilir.

Gnome Tweak ile koyu tema da kullanabilirsiniz.[^5]

[^5]:Fedora 36 ile koyu tema özelliği gelecektir.

<br>

## 7. Codec'ler
Multimedya codec'leri için Terminal'e aşağıdaki kodları yazıyoruz.[^6]

```
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
```
```
sudo dnf install lame\* --exclude=lame-devel
```
```
sudo dnf group upgrade --with-optional Multimedia
```
[^6]:[Kaynak](https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/)

<br>

## 8. Windows Fontları Yükleme
Windows'tan gelen bazı dosyalar, özellikle Word belgeleri, fontlar yüzünden düzgün gösterilmeyebilir. Bu sebeple Windows fontlarını kullanmalıyız.

Files'ın sol konsolunda en altta yer alan +Other Locations'a tıklıyoruz. Windows > Fonts klasörü içindeki fontları kopyalıyoruz. Fedora'da gizli dosyaları gösteriyoruz ve Home klasörünün içinde .Font adlı yeni bir klasör oluşturup kopyaladığımız fontları buraya yapıştırıyoruz.

<img src="https://zinzinzibidi.com/img/fedora-hidden-files.png" alt="fedora hidden files" style="width:600px"/>

Gizli dosyaları görebilmek için Home klasöründe Show Hidden Files seçeneği seçilmelidir.

<br>

## 9. Masaüstünde Nesne Kullanma

Masaüstünde klasör, belge kullanabilmek için [Desktop Icons NG (DING)](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/) eklentisi kurulabilir. Bu eklentiyi kurabilmek için daha önce [GNOME Shell Extensions](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep?hl=tr)
kurulmalıdır. (Firefox için [tıklayınız](https://addons.mozilla.org/tr/firefox/addon/gnome-shell-integration/).)

<br>

## 10. Harici Yazılım Kurulumu ve Kaldırılması

Fedora'da harici yazılım kurmak için rpm uzantılı dosyalar kullanılmaktadır. rpm uzantılı tüm dosyalar paket olarak adlandırılmaktadır.

Paketlerin kurulumu için

```
dnf install paket_adi
```

Kaldırılması için

```
dnf remove paket_adi
```

komutlarını kullanıyoruz. Kaldırma işlemlerinde .rpm uzantısını yazılmamalıdır. Sadece paket adları yazılmalıdır.

![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) rpm paket kurulumları son çare olarak kullanılmalıdır. Bu paketleri kaldırmak kimi zaman sorunlara yol açabilmektedir.

Kaldırma işlemlerinde sorun çıkarsa aşağıdaki örnekteki yöntemi uygulayabilirsiniz:

Diyelim ki **softmaker-office-2021-1046.x86_64.rpm** paket yazılımını indirdik. Fakat Software'den kaldıramadık. Terminal'e başında sudo olmadan

```
dnf list --installed \*softmaker\*
```
ya da 

```
sudo dnf search \*softmaker\*
```

komutlarını yazıyoruz. Buradaki \* \* karakterleri softmaker kelimesinden önce ya da sonra karakter olsun ya da olmasın içinde "softmaker" geçen tüm paketleri listelemeye yarar. Komutu çalıştırdığımızda yanıt olarak

```
Installed Packages
softmaker-office-2021.x86_64
```
dönecektir.

```
dnf remove -y softmaker-office-2021.x86_64
```
paket adını öğrendikten sonra SoftMaker Office'i yukarıdaki komutlar yardımıyla kaldırabiliriz.

<br>

## 11. OnlyOffice Kurulumu

<img src="https://zinzinzibidi.com/img/onlyoffice.png" alt="fedora scale" style="width:480px"/>

Fedora ile varsayılan olarak LibreOffice yazılımı gelse de topluluğun en çok tercih ettiği ofis programı Microsoft 365'e benzemesi sebebiyle OnlyOffice'dir.

Kurulum öncesi 3. başlıkta anlatılan RPMFusion ve Flatpack paketlerinin kurulması gerekmektedir.

PSoftware'den OnlyOffice aratılarak kurulabilir. Tamamen ücretsizdir.

<br>

## 12. VLC media player

Bazı videolar mp4 formatında olsa dahi codec eksikliği yüzünden Fedora'nın varsayılan video oynatıcısı tarafından çalışmayabilir. Bunun için Software'den VLC media player kurulabilir.

<br>

## 13. Ekran Görüntüsü Alma

Tam ekran görüntüsü almak için PrintScreen, belirli bir alanın ekran görüntüsünü için SHIFT + PrintScreen tuş kombinasyonunu kullanabilirsiniz. Görüntüler Files > Pictures içerisine kaydedilmektedir. Dilerseniz Photoshop'un alternatifi olan GIMP ile görseller üzerinde çalışabilirsiniz.

<img src="https://zinzinzibidi.com/img/fedora-shutter.png" alt="fedora shutter" style="width:480px"/>

Belirli bir alanın ekran görüntüsünü alma, dikdörtgen ve ok şekileri vurgu yapma gibi özellikler için Shutter yazılımı kullanılabilir.

<br>

## 14. Açılış Listesinde Eski Versiyonların Listeden Kaldırılması

Bilgisayarı baştan başlattığımızda hangi işletim sistemini seçeceğimize dair bir liste görüntülenecektir.

<img src="https://zinzinzibidi.com/img/fedora-oldversions.png" alt="fedora old versions" style="width:480px"/>

Her yeni güncelleme ile bu liste uzamaya başlayacaktır. Bu sebeple GRUB açılış listesindeki eski versiyonları listeden kaldırmak için

```
sudo dnf remove --oldinstallonly
```
komutunu kullanmamız yeterlidir.

![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) Bu çözüm Fedora'nın eski versiyonlarını silecektir. Çökme durumlarında kurtarma sürümüne geçilememektedir. Bu yüzden dikkatli kullanılmalıdır.

<br>

## 15. Varsayılan Uygulamalar

Varsayılan uygulamaları değiştirmek için Super Key yapıldıktan sonra "Default App" yazılabilir.

<img src="https://zinzinzibidi.com/img/fedora-defaultapps.png" alt="fedora default apps" style="width:600px"/>

Ya da doğrudan Settings > Default Applications yolu izlenebilir.

<br>

## 16. Topluluk Desteği

Bu belgedeki birçok konu Reddit topluluğu sayesinde hazırlanmıştır. Sorun yaşadığınız her konuda [Fedora Subredditi](https://www.reddit.com/r/Fedora/)'ni kullanabilirsiniz. Çok sağlam bir community'si vardır.

<br>

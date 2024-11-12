# Linux Commands


- uname -u : Sistem bilgisi(çekirdek sürümü, tarihi ve mimarisi)
- uname -r : Çekirdek sürümü bilgisi
- uptime : Sistemin ne kadar zamandır açık olduğunu ve yükü gösterir
- hostname : Sistem adı
- last reboot : Son kapanma listesi çalışma düzey değişikliği dahil
- date : tarih hakkında bilgi verir
- cal : takvim
- w : hangi kullanıcı o anda hangi komutu çalıştırdığını görürüz.
- whoami : o anki kullanılan kullanıcı adını verir
- finger yakup : Kullanıcı hakkında bilgi verir
- echo “user:passwd” | chpasswd : Tek satırda parola yenilemek

## Harware Commands


- dmesq : Kernel mesajlarını verir
- cat /proc/cpuinfo : İşlemci hakkında bilgi verir
- cat /proc/meminfo : Bellek(RAM) hakkında bilgi verir
- cat /proc interrupts : CPU Çekirdek sistem kesme listesi
- lshw : Sistemin donanım konfigurasyon bilgileri
- lsblk : Disk Bölümleme tablosu
- free -m : Sistemde kullanılan ram bilgisi
- lspci -tv : PCI cihazlarını listeler
- lsusb -tv : USB cihazlarını listeler
- dmidecode : BIOS donanım bilgisi
- hdparm -i /dev/sda : Disk hakkında bilgi verir
- hdparm -tT /dev/sda : Kullanılan disk için okuma hız testi
- badblocks -s /dev/sda : Ulaşılamayan block tespiti


## Users Commands


- cat /etc/passwd : Tüm kullanıcıları listeler
- id : Kullanıcı id bilgisi
- last : Sisteme en son giriş yapmış kullanıcıların bugünden geriye doğru listesi
- who : Sisteme kayıtlı kullanıcılar
- groupadd : Sistemde yeni bir grup oluşturur
- useradd yakup : Sisteme yakup isimli bir kullanıcı ekler
- userdel yakup : Sistemden yakup isimli kulllanıcıyı siler
- usermod : Kullanıcı izinlerini değiştirme

## File Commands


- ls -la : Dosyaları listeler (a gizli olanlar, l detaylı)
- pwd : Mevcut dizin gösterir
- mkdir : Dizin oluşturur
- rm : Dosya silme
- rm -r : Dizin sil(alt dizinlerde dahil)
- rm -f : Sormadan siler
- rm -rf : Dizini ve alt dizinleri sormadan siler
- cp : Dosyayı kopyala
- cp -r home1 home2 : home1 isimli dizini home2 ye taşı yoksa kapyala
- mv : Dosyaları taşıma
  
- ln -s “/home/Mert/bgpdump” /usr/local/bin : bin klasörüne bgpdump uygulaması için kısayol oluşturur

- touch : Dosya oluştur
- cat : Dosya içeriğinin tümünü oku
- more : Dosyanın içeriğini sayfalayarak göster
- head : Dosya içeriğinin ilk 10 satırını göster
- tail : Dosya içeriğinin son 10 satırını göster
- tail -f : Dosyanın içeriğinin son 10 satırını anlık gösterir

## Process Commands

- ps : Çalışan süreçler
- ps aux | grep uygulama adı : Adı verilen uygulamanın çalışan süreçleri
- pmap -x PID : İşlemin bellek haritası
- top : Temel sistem durumu, çalışmakta olan süreçler ne kadar bellek/işlemci kullandıkları
- kill : İşlemi bitir
- killall : Bütün işlemleri bitir
- pkill -f telnet : İşlemi bitir
- bg : Durdurulmuş işleme arkaplanda devam et
- fg : Arkaplanda yapılan işlemi ön plana getir

## Permissions Commands

- chattr +i dosyaadı : Dosyalar silinemez dokunulmaz olur
- chattr -i dosyaadı : Dosya dokunulmazlığını kaldırma
- chattr +a dosyaadı : Varolan satırları korur, altına satır eklenmesine izin verir.
- lsattr dosyadı : Chattr komutu geçerli olmuşmu diye kontrol edilir
- chmod 777 : Her şey okunabilir, yazılabilir ve çalıştırılabilir
- chmod 644 : Sadece okunabilir
- chmod 755 : Sadece sahibi okur, yazar ve çalıştırılabilir
- chown owner-user : Dosyanın sahibini değiştirir
- chown owner-user:owner-group : Dosyanın sahibini ve grubunu değiştirir
- chown -R kullanıcıadı:kulllanıcıadı dizin/dosya : Kullanıcıya dizinleriyle birlikte erişim izni verir


## Network Commands

- ip addr show : Tüm network interfaceslerini listeler ve ip adreslerini gösterir
- ip address add 192.168.0.2 dev enp4so : Belirtilen interfaces ip adresi ekler
- ip link set <interface> up : Ağ arayüzünü aktifleştirir.
- ip link set <interface> down : Ağ arayüzünü pasifleştirir.
- ethool enp4s0 : Ethernetin durumu hakkında bilgi verir.
- ping 192.168.0.2 : Belirtilen ip adresine echo isteği yollar.
- dig example.com : Alan adı hakkında DNS bilgisini verir.
- dig -x : Geriye doğru arama işlemi.
- host example.com : Host adını alıp makine adına bakar.
- hostname -i : Yerel ip adresini gösterir.
- wget : Belirtilen adresten dosya indirir.
- netstat -tulpn : Aktid dinlenilen portları listeler.
- ip a : Bilgisayardaki bulunan interfaces elamanları listeler.
- echo “1” > /proc/sys/net/ipv4/ip_forward : IP Yönlendirmeyi aktif eder, sistemi routere çevirir
- echo “1.1.1.1” > /etc/resolv.conf : Sistem Cloudflare DNS kullanılır.

## Archiving Commands

tar -cf homebackup.tar home : homebackup.tar adlı bir arşiv dosyası oluşturur
tar -xf homebackup.tar : homebackup.tar adlı arşivi ayrıştırır
tar -czf homebackup.tar.gz home : gzip sıkıştırması kullanılarak arşiv oluşturur
gzip home : home.gz olarak arşiv dosyası oluşturur
unzip abc.zip : Zip dosyasını çıkartır.
zipgrep *.txt abcd.zip : Zipp içerisinde txt dosyalarını arar
tar xjf archive.tar.bz2 : tar.bz2 dosyasını çıkartır
tar ztvf home.tar.gz | grep abc : tar.gz içinde arama yapar
gzip -d home.gz : gzip dosyasını çıkartır
zgrep ‘abc’ /var/log/maillog*.gz : Log dosyası içinde çıkartmadan arama imkanı sağlar
Kurulum (Debian)


apt-get install paket_adi : Debian tabanlı sistemlerde paketi kurar
apt-get purge paket-adı : Debian tabanlı sistemleri paketi kaldırır

## Compiler Commands

./configure
make
make install
Temelde tüm derleme işlemleri bu komutlar aracılığı ile yapılmaktadır.

## Searching Commands

find -name “yakup*” : Adında yakup geçen tüm dosyaları bulur
find . -type f -size +100k : 100k dan büyük olan dosyaları aratır
find . -type f -size +100k -a -size -110k : 100k ve 110k arasında dosyaları aratır
sed : akış editörü ve text manipülasyonu
grep ifade dosya : Dosya içerisinde geçen ifadeyi aratır
grep -r ifade dosya : Özyineli olarak belirtilen ifadeyi aratır
locate dosya : Belirtilen dosyayı aratır.

## Secure Shell (SSH) Commands

ssh kullanıcı@host : Belirtilen makineye bağlanır
ssh kullanıcı@host -p port : Belirtilen makineye belirtilen port ile bağlanır
telnet host : Telnet portu ile makineye bağlanır

## File Transfer (FTP) commands


scp kullanıcı@host:aktarılıcakdosya.txt /home/mert : Belirtilen makineye dosya transferi yapar
rsync -a /home/mertcan /yedekler : Kaynak ile hedef arasında senkronizasyonu sağlar

## Disk Usage Commands

du -ah : Dizinlerin kullandıkları alanı okunaklı olarak gösterir
du -sh : Dizinin kullandığı toplan alanı gösterir
df -h : Diskler hakkındaki son durum görülür
df -i : Boş inode durumu görüntülenir
findmnt : Dosya sistemindeki bağlı tüm dizinleri detaylı bir şekilde gösterir
mount /dev/sda/ /mnt : Diski /mnt ye bağlar


## Directory Commands

cd : Birinci seviye dizine gider
cd -: Bir önceki dizine döner
cd ~ : Home dizinene geçer
cd .. : Bir üst dizine gider
cd dizin : Belirtilen dizine gider


Bonus


history -c : Komut satır geçmişini temizler

clamscan -r -z — remove — verbose /home : Virüs tarama ve silme işlemi

du -h — max-depth=1 | sort -hr : Dizinlerin toplam boyutlarını gösterir

find /home/mertcan/ -type -f -exec grep -H ‘yazı’ {} ; Dizin içerisinde yaziyı aratır

dd if=debain.iso of=/dev/sdb : Iso kalıbını USB veya DVD ye yazdırma

shred -verbose -random-source=/dev/zero -iterations=5 /dev/sda: Ultra güvenli disk silme

find -type f -exec chmod 644 {} ; Tüm dosya izinlerini 644 yapar.

openvpn — config client.ovpn: VPN sunucusuna bağlantı sağlar

sensors : Donanım parçalaırnın ısılarını verir.

gcc -o output input.c : C kodunu derler

rdesktop x.x.x.x : RDP bağlantısını sağlar

ssh root@x.x.x.x | cat /dev/null > ~/.bash_history : Bash geçmişini temizler.
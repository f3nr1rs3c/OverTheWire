bandit0 = 0 => readme cat yaparak alttaki şifreyi aldık bandit1'e bağlandık.

bandit1 = ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If şifresi. Bağlandıktan sonra ls yapıyoruz - çıkıyor
fakat bu dosyayı cat - yapınca okuyamıyoruz bu yüzden cat ./- yapacağız ki okuyalım. Sonra şifre çıkıyor.

bandit2 = 263JGJPfgU6LtdEvgfWU1XP5yac29mFx şifresi. ls yaptık space in this filename çıktı
bu sefer cat spaces in this filename yapıyoruz. Şifre çıkıyor

bandit3 = MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx şifresi. ls yapıyoruz. inhere klasörüne cd giriyorz
sonra ls yapıyoz bir şey çıkmıyor. ls -la yapıyorz. Gizli dosya çıkıyor. Onu okumak içinde cat ...Hiding-From-You yapıyoruz ve şifre çıkıyor.

bandit4 = 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ şifresi. ls yaıyoruz inhere klasörü çıkıyor giriyorz sonrasında file dosyaları ortaya çıkıyor
cat ./-file... tüm dosyaları böyle okuyoruz içerisinde net yazılı olanı buluyoruz. cat ./-file07 de şifreyi buluyoruz.

bandit5 = 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw şifresi. ls yapıyoruz inhere klasörü çıkıyor sonra cd inhere diyoruz bu sefer
find . -type f -size 1033c => burada 1033c 1033byte istenilen dosyanın boyutudur. Sonrasında
cat ./maybehere07/.file2 yazıyoruz. Şifreyi veriyor

bandit6 = HWasnPhtq9AVKe0dmk45nxy20cvUa6EG şifresi burada kaldık bağlantı kurucağız. 
ls -la yapıyoruz gizli ve normal bir dosya gözükmemektedir. find . -type f -user bandit7 -group bandit6 -size 33c yapıyoruz
fakat bir şey çıkmıyor. find / -type f -user bandit7 -group bandit6 -size 33c tüm dizinlerin köküne tarama yapıyoruz.
/var/lib/dpkg/info/bandit7.password adlı dosyayı sonunda buluyoruz.

bandit7 = morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj şifresi. ls yapıyoruz karşımıza data.txt çıkıyor. cat data.txt yapıyoruz bir sürü şifre ve kullanıcı adı çıkıyor.
sonra direk şifreyi bulmak istediğimizde. strings data.txt | grep "millionth" yapıyoruz. Millionth'da bize verilen görev içeriğinde yazıyordu.

bandit8 = dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc şifresi. ls yapıyoruz data.txt dosyayısını görüyoruz. cat data.txt yapıyoruz ona da ve çıktı alıyoruz.
sonrasında hepsi düzensiz burada ki çoğu şifre birden çok kez kullanılmış bizim amacımız ise sadece 1 kez kullanılan şifreyi bulmak.
bu yüzden sort data.txt yapıp hepsini düzene sokuyoruz. sort data.txt | uniq -c yapıyoruz ve burda da kaç adet kullanılmışsa yanlarına yazıyor.

bandit9 = 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM şifresi. ls yapıyoruz data.txt tekrar çıkıyor fakat cat data.txt yaptığımızda dosya bozuk şekilde gözüküyor.
strings data.txt | grep "=" yapıyoruz. Ve şifre karşımızda altta.

bandit10 = FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey şifresi. ls yapıyoruz sonra cat data.txt yapıyoruz karşımıza base64 ile şifrelenmiş bir şifre çıkıyor onu base64 decrypt bulunan siteye
yapıştırıp decrypt yapıyoruz ve şifre çıkıyor.

bandit11 = dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr şifresi. ls yapıyoruz sonra cat data.txt yapıyoruz. Çıkan ROT13 ile cryptolanmış şifreyi rot13 decrypt programı içerisine koyup gerçek şifreyi alıyoruz

bandit12 = 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4 şifresi. ls yapıyoruz sonra cat data.txt yapıyoruz. Karşımıza karışık şeyler çıkıyor. Sonra mkdir /tmp/fenrir adında dosya açıyoruz
cp data.txt /tmp/fenrir içerisine kopyalıyoruz. cd /tmp/fenrir yapıp dosyaya gidiyoruz ls komutu çalıştırıyoruz. Sonrasında ise xxd -r data.txt > fenpass ismiyle geri çevirme yapıyoruz data.txt çünkü
içerisinde hexdecimal olduğu için. Şimdide cat fenpass yapıyoruz yine sonuç alamadık. Bu sefer bu dosya hangi program ile sıkıştırılmış ona bakıyoruz. file fenpass yapıyoruz ve karşımıza gzip ile olduğu çıkıyor.
önce dosyaya uzantı verelim yoksa gzip komutu kullanamayız bu yüzden mv fenpass fenpass.gz yapıyoruz. Fakat bu sefer de bzip2 ile sıkıştırılmış bu yüzden mv fenpass fenpass.bz2 komutu kullanıyoruz.
bzip2 -d fenpass.bz2 bu sefer bu komutu kullanıyoruz. Sonra ls yaptığımızda yine şifreli gözüküyor. Tekrar file fenpass yapıyoruz tekrardan gzip ile sıkıştırılmış. gzip -d fenpass.gz tekrardan bu komutu kullanıyoruz. 
file fenpass diyoruz. Bu seferde tar ile sıkışlaştırılmış. tar xf fenpass.tar yapıyoruz. Sonra ls diyoruz ve data.txt çıkıyor. Sonrasında sırasıyla bu komutlar kullandım. file data6, mv data6 data6.tar, tar xf data6.tar
ls, file data8.bin, mv data8.bin data8.gz, gzip -d data8.gz, ls, file data8, cat data8 sonunda şifreyi buldum!

bandit13 = FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn şifresi. ls yapıyoruz sshkey.private diyor. ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220 yazıyoruz. sonra cat /etc/bandit_pass/bandit14 yaptım.
bandit14'ün şifresini de elde etmiş olduk.

bandit14 = MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS şifresi. nc 127.0.0.1 30000 yerelde bu portta dinleme başlatıp bandit14'ün şifresini yapıştırıyoruz ve bandit15 şifresini alıyoruz.

bandit15 = 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo şifresi. ncat --ssl 127.0.0.1 30001 yerelde bu portta dinleme başlatıp bandit15'in şifresini yapıştırıp bandit16'nın şifresini alıyoruz.

bandit16 = kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx şifresi. ls -la yapıyoruz. .bandit15.password adlı bir ASCII yazısı buluyoruz açmak için. file ./.bandit15.password yazıyoruz.
ve bakıyoruz ki bandit15 şifresi elimize gelmiş. :) Fakat bandit16'nın görevi nmap ile açık olan portu bulmak 31000 - 32000 arasında bulmaya çalışalım. nmap 127.0.0.1 -p 31000-32000 yazıyoruz ve karşımıza çıkıyor.
çıkan portları sırasıyla ncat --ssl 127.0.0.1 31790 denerken bu 31790 port private key buluyoruz bunu tamamen kopyalıyım kendi makinamıza bandit17key adında bir metin dosyasına yapıştırıyoruz.
sonrasında ssh -i bandit17key bandit17@bandit.labs.overthewire.org -p 2220 tekrar bağlantı kuruyoruz. bandit17 girmek için kullanıyorz private key yani.
güvenlik sebebiyle olmuyor bu yüzden sadece okuma yetkisi vermemiz gerekiyor çünkü yazma yetkiside var. chmod 400 bandit17key yetkiyi de böyle verdik ssh -i bandit17key bandit17@bandit.labs.overthewire.org -p 2220 tekrar bunu yazıp
giriyoruz. Ve görev başarılı bandit 17'e girdik.

bandit17 = diff passwords.old passwords.new yaptık sondaki şifre x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO bu 

bandit18 = x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO şifresi. bu şifreyi bandit18 giriş yapınca bize byebye diyor bu yüzden bandit19'a erişip öyle girmek lazım.
ssh -t bandit18@bandit.labs.overthewire.org -p 2220 '/bin/sh' şifresi: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
girdikten sonra ls diyoruz sonrasında readme çıkıyor cat readme diyoruz şifreyi alıyoruz.

bandit19 = cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8 şifresi. ls yapıyoruz sonrasında çıkan bandit20-do çalıştırabilir bir dosya. ./bandit20-do id diyoruz. Bize grup ve uid bilgileri veriyor.
bizim de bandit20'nin şifresini almamız için ./bandit20-do cat /etc/bandit_pass/bandit20

bandit20 = 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO şifresi. ls yapıyoruz ve bakıyoruz ki suconnect adlı dosya görüyoruz. Burada iki tane terminal açıyoruz. Sol taraftaki terminale netcat 8080 portuna dinleme yapıyoruz. nc -l 127.0.0.1 8008 yazıyoruz. 
Diğer terminalde ise ./suconnect 8080 yapıyoruz bağlantının açık portu 8080 olduğundan açılıyor farklı bir port girsek olmaz. Sonra dinlenen veya diğer ./suconnect 8080 port bandit20 şifresini yazarsak bandit21 
şifresini veriyor.

bandit21 = EeoULMCra2q0dSkYj561DX7s1CpBuOBt şifresi. ls yapıyoruz hiç bir şey çıkmıyor. OverTheWire sitesinde bize cd /etc/cron.d/ adlı klasöre geçmemizi istiyor. Sonra cat cronjob_bandit22 yapıyoruz içinde bir bash uzantılı dosya varmış onun içerisine de /dev/null yapıştırmamızı söylüyor. Biz önce bash uzantılı
dosyayı cat aracılığıyla okuyalım. Okuduğumuzda yetkilendirme ayarları var. İçerisinde cat ile okuduğumuzda önce yetkisi arttırıyor. Sonrasında cat /etc/bandit_pass/bandit22 şifresini okuyor. Sonra bu dosya içerisine yazıyor. /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv . Bizde bu dosyayı cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv diyerek okuyoruz.

bandit22 = tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q şifresi. ls yapıyoruz yine bir şey yok. OverTheWire diyor ki yine aynı cron.d dosyasına bak diyor.
cd /etc/cron.d/ diyoruz. cat cronjob_bandit22 yapıyoruz. Yine aynı bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null çıkıyor. cat /usr/bin/cronjob_bandit23.sh yapıyoruz. Sırasıyla, cd /etc/cron.d yapıyoruz, ls -la,  cat /etc/cron.d/cronjob_bandit23 yapıyoruz. cat /usr/bin/cronjob_bandit23.sh adlı dosyayı okuyoruz. Bash script ile yazılanı terminale bastırıyoruz. Çıkan kodu, cat /tmp/8ca319486bfbbc3663ea0fbe81326349 /tmp/ dosyasının içerisinde okuyoruz.


bandit23 = 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga şifresi. Sırasıyla

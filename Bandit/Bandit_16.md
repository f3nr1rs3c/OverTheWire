bandit16 = kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx şifresi. ls -la yapıyoruz. .bandit15.password adlı bir ASCII yazısı buluyoruz açmak için. file ./.bandit15.password yazıyoruz.
ve bakıyoruz ki bandit15 şifresi elimize gelmiş. :) Fakat bandit16'nın görevi nmap ile açık olan portu bulmak 31000 - 32000 arasında bulmaya çalışalım. nmap 127.0.0.1 -p 31000-32000 yazıyoruz ve karşımıza çıkıyor.
çıkan portları sırasıyla ncat --ssl 127.0.0.1 31790 denerken bu 31790 port private key buluyoruz bunu tamamen kopyalıyım kendi makinamıza bandit17key adında bir metin dosyasına yapıştırıyoruz.
sonrasında ssh -i bandit17key bandit17@bandit.labs.overthewire.org -p 2220 tekrar bağlantı kuruyoruz. bandit17 girmek için kullanıyorz private key yani.
güvenlik sebebiyle olmuyor bu yüzden sadece okuma yetkisi vermemiz gerekiyor çünkü yazma yetkiside var. chmod 400 bandit17key yetkiyi de böyle verdik ssh -i bandit17key bandit17@bandit.labs.overthewire.org -p 2220 tekrar bunu yazıp
giriyoruz. Ve görev başarılı bandit 17'e girdik.

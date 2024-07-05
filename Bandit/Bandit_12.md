bandit12 = 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4 şifresi. ls yapıyoruz sonra cat data.txt yapıyoruz. Karşımıza karışık şeyler çıkıyor. Sonra mkdir /tmp/fenrir adında dosya açıyoruz
cp data.txt /tmp/fenrir içerisine kopyalıyoruz. cd /tmp/fenrir yapıp dosyaya gidiyoruz ls komutu çalıştırıyoruz. Sonrasında ise xxd -r data.txt > fenpass ismiyle geri çevirme yapıyoruz data.txt çünkü
içerisinde hexdecimal olduğu için. Şimdide cat fenpass yapıyoruz yine sonuç alamadık. Bu sefer bu dosya hangi program ile sıkıştırılmış ona bakıyoruz. file fenpass yapıyoruz ve karşımıza gzip ile olduğu çıkıyor.
önce dosyaya uzantı verelim yoksa gzip komutu kullanamayız bu yüzden mv fenpass fenpass.gz yapıyoruz. Fakat bu sefer de bzip2 ile sıkıştırılmış bu yüzden mv fenpass fenpass.bz2 komutu kullanıyoruz.
bzip2 -d fenpass.bz2 bu sefer bu komutu kullanıyoruz. Sonra ls yaptığımızda yine şifreli gözüküyor. Tekrar file fenpass yapıyoruz tekrardan gzip ile sıkıştırılmış. gzip -d fenpass.gz tekrardan bu komutu kullanıyoruz. 
file fenpass diyoruz. Bu seferde tar ile sıkışlaştırılmış. tar xf fenpass.tar yapıyoruz. Sonra ls diyoruz ve data.txt çıkıyor. Sonrasında sırasıyla bu komutlar kullandım. file data6, mv data6 data6.tar, tar xf data6.tar
ls, file data8.bin, mv data8.bin data8.gz, gzip -d data8.gz, ls, file data8, cat data8 sonunda şifreyi buldum!

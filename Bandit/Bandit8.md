bandit8 = dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc şifresi. ls yapıyoruz data.txt dosyayısını görüyoruz. cat data.txt yapıyoruz ona da ve çıktı alıyoruz.
sonrasında hepsi düzensiz burada ki çoğu şifre birden çok kez kullanılmış bizim amacımız ise sadece 1 kez kullanılan şifreyi bulmak.
bu yüzden sort data.txt yapıp hepsini düzene sokuyoruz. sort data.txt | uniq -c yapıyoruz ve burda da kaç adet kullanılmışsa yanlarına yazıyor.

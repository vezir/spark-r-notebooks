# sparkR notebooks
Bu sıralar büyük veri işlemede Hadoop ile birlikte en çok sözü edilen uygulama Spark kuşkusuz. Spark kullanımı için sunulan arabirimlerden (API); Python, Scala ve Java dışında, istatistikçilerin gözdesi R ile Spark işleri çalıştırmak olanağı sunan SparkR ın yeteneklerini incelemek amaçlı yaptığım çalışmaları burada ilgilenenlerle paylaşıyorum. Bu çalışma büyük oranda [tutorial](https://github.com/jadianes/spark-r-notebooks) dan faydalanılmıştır ama çevirisi değildir.

Bu incelemeyi kolay bir ortamda yapabilmek için sparkR ın komut satırını değilde, IPython / Jupyter notebook u kullanmayı tercih ettim. Bu şekilde hem çalışmamız daha kolay olacak, hem de yaptığımız analizleri paylaşmak, tekrar etmek, diğer kişilerle paylaşmak çok rahat olacak. Bu dokümantasyon yapmak anlamına da geliyor olacak.

#Başlangıç
Öncelikle kullanacağımız ortamdan bahsedelim. Bu çalışma değişik işletim sistemleri kullanılarak yapılabilir ama benim tercihlerim Windows7 olan makinamda, Oracle VM VirtualBox a kurduğum Linux varyantı Ubuntu 14.04 LTS yi kullanacağım.
Gerekli yazılımlar Spark, R, Jupyter Notebook, tercihen Hadoop olacak. Hadoop yapacağımız alıştırmalar için mutlaka gerekmiyor ve yeri geldiğinde bunun ne anlama geldiğini anlatacağım.

Kullanacağımız ortam [Jypter notebook](http://jupyter.org/) default olarak Python ile çalışacak şekilde düzenlenmiştir. Farklı dillerde çalışma yapabilmek için bu dillerin motorlarına ilgili komutları aktarıp sonuçları notebook a geri getirecek bir yazılıma ihtiyaç duyuyoruz. Bu yazılımlara Kernel deniyor ve R için olanı [IRkernel](http://irkernel.github.io/installation/) dan kurulumu yapabilirsiniz. Ayrıca [Using R with Jupyter Notebooks](http://blog.revolutionanalytics.com/2015/09/using-r-with-jupyter-notebooks.html) da sizlere yardımcı olacaktır.

Tabii [Spark](https://spark.apache.org/docs/latest/index.html) ın kurulumunun yapıldığını kabul ediyorum. Bunun için gerekirse ayrı bir sayfa açabiliriz. [Hadoop](http://hadoop.apache.org/releases.html) kurulumu opsiyoneldir. Yeri gelince bunun nedenini açıklayacağım. Java ve [Scala](http://www.scala-lang.org/) kurulumu yapıldığını da kabul ediyoruz.

#Veri Seti
Veri seti olarak yeterince büyük olması ve veri biliminin önde gelen sitelerinden [Kaggle](https://www.kaggle.com/) da detayları verilmiş bir veri seti [2013 American Community Survey dataset](https://www.kaggle.com/census/2013-american-community-survey) i seçiyoruz.

1. Verinin yüklenmesi ve SparkR ın başlatılması
2. Spark SQL
3. Data Frame operasyonları
4. SparkR ve ggplot2 ile veri analizi
5. SparkR ile Lineer modelleme
 

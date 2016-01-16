# sparkR notebooks
Bu sıralar büyük veri işlemede Hadoop ile birlikte en çok sözü edilen uygulama Spark kuşkusuz. Spark kullanımı için sunulan arabirimlerden (API); Python, Scala ve Java dışında, istatistikçilerin gözdesi R ile Spark işleri çalıştırmak olanağı sunan [SparkR](http://spark.apache.org/docs/latest/sparkr.html) ın yeteneklerini incelemek amaçlı yaptığım çalışmaları burada ilgilenenlerle paylaşıyorum. Bu çalışma [Jose A Dianes](https://github.com/jadianes) in aynı isimli güzel [tutorial](https://github.com/jadianes/spark-r-notebooks) ından esinlenerek hazırlanmıştır. İlgilisi için o tutorial u da incelemesini öneririm.

Bu incelemeyi kolay bir ortamda yapabilmek için sparkR ın komut satırını değilde, [IPython / Jupyter notebook](http://jupyter.org/) u kullanmayı tercih ettim. Bu şekilde hem çalışmamız daha kolay olacak, hem de yaptığımız analizleri diğer kişilerle paylaşmak, tekrar etmek çok rahat olacak. Bu şekilde dokümantasyonda yapılmış oluyor.

#Başlangıç
Öncelikle kullanacağımız ortamdan bahsedelim. Bu çalışma değişik işletim sistemleri kullanılarak yapılabilir ama benim ortamım Windows7 olan makinamda, Oracle VM VirtualBox a kurduğum Linux varyantı Ubuntu 14.04 LTS şeklinde.
Gerekli yazılımlar Spark, R, Jupyter Notebook, tercihen Hadoop olacak. Hadoop yapacağımız alıştırmalar için mutlaka gerekmiyor.

Kullanacağımız ortam [Jupyter notebook](http://jupyter.org/) default olarak Python ile çalışacak şekilde düzenlenmiştir. Farklı dillerde çalışma yapabilmek için bu dillerin motorlarına ilgili komutları aktarıp sonuçları notebook a geri getirecek bir yazılıma ihtiyaç duyuyoruz. Bu yazılımlara Kernel deniyor ve R için olanı [IRkernel](http://irkernel.github.io/installation/) dan kurulumu yapabilirsiniz. Ayrıca [Using R with Jupyter Notebooks](http://blog.revolutionanalytics.com/2015/09/using-r-with-jupyter-notebooks.html) da sizlere yardımcı olacaktır.

Tabii [Spark](https://spark.apache.org/docs/latest/index.html) ın kurulumunun yapıldığını kabul ediyorum. Ben 1.6.0 versiyonunu kurdum. [Hadoop](http://hadoop.apache.org/releases.html) kurulumu opsiyoneldir. Yeri gelince bunun nedenini açıklayacağım. Java ve [Scala](http://www.scala-lang.org/) kurulumu yapıldığını da kabul ediyoruz. Son versiyon 2.11.7 yerine 2.10.x kurmanızda/kullanmanızı öneririm.

#Veri Seti
Büyük veri ile ilgili bir çalışmanın en önemli başlangıç unsuru tabii olarak büyük bir veridir. Günümüzde sıradan insanların büyük veriye erişmesi hiç olmadığı kadar kolaylaşmıştır. Hatta bu veriler bazı iş ihtiyaçları için bile kullanılabilir. Burada özellikle birkaç büyük veri kaynağı vereceğim. Bunun için [Big Data: 20 Free Big Data Sources Everyone Should Know](http://www.smartdatacollective.com/bernardmarr/235366/big-data-20-free-big-data-sources-everyone-should-know) daki kaynaklar iyi bir başlangıçtır.

[Jose A Dianes](https://github.com/jadianes) ın tutorial ında, veri seti olarak yeterince büyük olması ve veri biliminin önde gelen sitelerinden Kaggle da detayları verildiği için [2013 American Community Survey](https://www.kaggle.com/census/2013-american-community-survey) veri seti seçilmiştir. Ben tekrar olmaması açısında farklı bir veri seti, *ABD - California da yol kazalarında yaralanmaları 2002-2010* [Road Traffic Injuries 2002-2010](http://www.healthdata.gov/dataset/road-traffic-injuries-2002-2010) ile ilgili verileri aldım.

Bu veri setinde Kaliforniya'da yaşayan kişi ve mil başına olan trafik kazalarının yaya, otomobil, motorsiklet gibi kategorilerdeki istatistikleri, Kaliforniya'nın alt bölgeleri bazında verilmektedir. Veriyi doğrudan incelemek isterseniz [analiz için hazırlanmış sayfadan](https://cdph.data.ca.gov/Environment/Road-Traffic-Injuries-2002-2010/xmwz-xvsf) faydalanabilirsiniz. Var olan alanların neler olduğu ile ilgili bir [excel doküman](https://cdph.data.ca.gov/api/views/xmwz-xvsf/files/vFZ2-VvAdPb_6aOkATlLb19r3PpHHYGEgns1EH3kAQs?download=true&filename=RoadTrafficInjuries_DD.xlsx) da mevcuttur.

Düşündüğümüz analizleri SparkR ile yapabilmek için aşağıdaki adımları takip edeceğiz.

#Temel başlıklarımız
1. [Verinin yüklenmesi ve SparkR ın başlatılması](https://github.com/vezir/spark-r-notebooks/blob/master/notebooks/1-baslangic/baslangic.ipynb)
2. [Spark SQL](https://github.com/vezir/spark-r-notebooks/blob/master/notebooks/2-sparkSQL/sparkSQL.ipynb)
3. [Data Frame operasyonları](https://github.com/vezir/spark-r-notebooks/blob/master/notebooks/3-sparkSQL/dataFrameOperations.ipynb)
4. [SparkR ve ggplot2 ile veri analizi](https://github.com/vezir/spark-r-notebooks/blob/master/notebooks/4-sparkSQL/graphicAnalysis.ipynb)
5. [SparkR ile Lineer modelleme](https://github.com/vezir/spark-r-notebooks/blob/master/notebooks/5-sparkSQL/linearModelling.ipynb)
 

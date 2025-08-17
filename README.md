# Uart-Nedir-
UART (Universal Asynchronous Receiver/Transmitter), mikrodenetleyiciler ile bilgisayar veya başka cihazlar arasında seri veri iletişimi sağlayan bir donanım birimidir. Asenkron çalışır, yani veri iletiminde saat sinyali (clock) kullanılmaz. Bunun yerine gönderici ve alıcı taraflar aynı baud rate (iletişim hızı) ayarında kullanılır.

BVerici (Transmitter): Verici, verileri seri olarak ileten cihazdır. Veri iletimi için bir seri veri akışı kullanılır. Verici, veriyi başlatma biti (Start Bit), veriyi (Data Bits), durum bitleri (Parity Bit), ve durdurma biti (Stop Bit) gibi bileşenlerle birlikte gönderir.

Alıcı (Receiver): Alıcı, veriyi alır ve veriyi analiz eder. Verinin başlangıcını ve bitişini tanımak için başlangıç biti ve durma biti kullanılır. Alıcı, verinin doğruluğunu kontrol etmek için durum bitlerini kullanabilir.

UART haberleşme protokolü, iki cihaz arasında veri iletimi sağlar ve farklı hızlarla (baud hızı) çalışabilir. Her iki cihazın baud hızları uyumlu olmalıdır.

Baud Hızı (Baud Rate): Saniyede iletilen bit sayısını ifade eden veri iletişim hızıdır. İki cihazın da aynı baud hızında (örneğin, 9600, 115200) ayarlanması zorunludur.Eğer iki cihazın baud rate ayarı uyuşmazsa (fark %2–3’ten fazla olursa) veriler kayar ve bozulur.
STM32’de UART baud rate, sistem clock’una göre hesaplanarak ayarlanır.

Veri Uzunluğu (Data Length): Veri çerçevesindeki bit sayısıdır (örneğin, 8 bit).

Eşlik Biti (Parity Bit): Hata kontrolü için kullanılan eşlik bitinin (tek veya çift) açık olup olmadığıdır.

Durdurma Biti Sayısı (Stop Bits): Veri paketinin sonundaki durdurma bitlerinin sayısıdır (1 veya 2).



**UART Nerelerde Kullanılır?**

Mikrodenetleyici – Bilgisayar (ör. STM32 ↔ PC, USB-TTL dönüştürücü ile)

Mikrodenetleyici – Mikrodenetleyici iletişimi

Sensör modülleri (GPS, Bluetooth HC-05, ESP8266, GSM modülleri vb.)

Debug ve veri takibi (seri port terminali üzerinden)






TTL (Transistor-Transistor Logic):

Mikrodenetleyiciler ve gömülü sistemlerde en yaygın kullanılan mantık seviyesidir.

Lojik "1" genellikle +3.3V veya +5V seviyesidir.

Lojik "0" ise 0V (GND) seviyesidir.

TTL seviyeleri, kısa mesafeli ve aynı güç kaynağını kullanan cihazlar arasında doğrudan iletişim için idealdir.

RS-232:

Daha eski bilgisayar sistemlerinin seri portlarında kullanılan bir standarttır.

TTL'ye göre ters bir mantık kullanır ve daha yüksek voltaj seviyelerinde çalışır.

Lojik "1" genellikle -3V ile -15V arasındadır.

Lojik "0" ise +3V ile +15V arasındadır.

Bu yüksek voltaj seviyeleri sayesinde RS-232, daha uzun mesafelerde ve elektriksel gürültüye daha dayanıklı bir iletişim sağlar.

TTL seviyelerini RS-232'ye dönüştürmek için MAX232 gibi özel entegrelere ihtiyaç duyulur.

TX (Transmit): Mikrodenetleyici veriyi seri hale çevirir ve hatta gönderir.

RX (Receive): Karşı taraftan gelen seri veriyi alır ve paralel hale çevirir.

Gönderme ve alma aynı anda yapılabilir (full-duplex).

FIFO Bellek (First-In, First-Out Buffer)
Modern mikrodenetleyicilerdeki UART birimleri genellikle bir FIFO (First-In, First-Out) bellek ile donatılmıştır. Bu, bir veri tamponu (buffer) görevi görür ve veri akışını yönetir.

Gönderim Tarafında: Gönderilecek veriler, TX hattına gönderilmeden önce bu belleğe yazılır. UART modülü, verileri birer birer gönderirken, işlemci yeni verileri belleğe yazmaya devam edebilir. Bu, işlemci yükünü azaltır ve daha hızlı bir veri akışı sağlar.

Alıcı Tarafında: Gelen veriler, RX hattından okunduktan sonra bu belleğe yazılır. İşlemci, gelen verileri bu bellekten okur. Eğer işlemci başka bir görevle meşgulken yeni veriler gelirse, bu veriler bellekte birikir ve işlemci müsait olduğunda hepsini birden okuyabilir. Bu, yavaş işlemci veya yazılım gecikmelerinden kaynaklanan veri kaybı riskini azaltır.

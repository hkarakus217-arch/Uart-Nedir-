# Uart-Nedir-
UART (Universal Asynchronous Receiver/Transmitter), mikrodenetleyiciler ile bilgisayar veya başka cihazlar arasında seri veri iletişimi sağlayan bir donanım birimidir. Asenkron çalışır, yani veri iletiminde saat sinyali (clock) kullanılmaz. Bunun yerine gönderici ve alıcı taraflar aynı baud rate (iletişim hızı) ayarında kullanılır.

Başlangıç Biti (Start Bit): Alıcıya verinin geldiğini bildiren ve iletişimi başlatan tek bir bittir (genellikle 0).

Veri Bitleri (Data Frame): Asıl veriyi içeren bitlerdir. Genellikle 5 ila 9 bit arasında değişir. Çoğu uygulamada 8 bit kullanılır.

Eşlik Biti (Parity Bit): Veri iletiminde hata kontrolü için kullanılan isteğe bağlı bir bittir. Gönderilen 1'lerin sayısının tek mi çift mi olduğunu kontrol ederek tek bitlik hataları tespit etmeye yarar.

Durdurma Biti (Stop Bit): Veri paketinin bittiğini belirten bir veya iki bittir (genellikle 1). Alıcının bir sonraki veri paketine hazırlanmasını sağlar.

Baud Hızı (Baud Rate): Saniyede iletilen bit sayısını ifade eden veri iletişim hızıdır. İki cihazın da aynı baud hızında (örneğin, 9600, 115200) ayarlanması zorunludur.

Veri Uzunluğu (Data Length): Veri çerçevesindeki bit sayısıdır (örneğin, 8 bit).

Eşlik Biti (Parity Bit): Hata kontrolü için kullanılan eşlik bitinin (tek veya çift) açık olup olmadığıdır.

Durdurma Biti Sayısı (Stop Bits): Veri paketinin sonundaki durdurma bitlerinin sayısıdır (1 veya 2).

# UART Nerelerde Kullanılır?
Mikrodenetleyici – Bilgisayar (ör. STM32 ↔ PC, USB-TTL dönüştürücü ile)

Mikrodenetleyici – Mikrodenetleyici iletişimi

Sensör modülleri (GPS, Bluetooth HC-05, ESP8266, GSM modülleri vb.)

Debug ve veri takibi (seri port terminali üzerinden)

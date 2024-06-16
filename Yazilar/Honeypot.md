# Honeypot-Avlarken Avlanmak 

Siber dünyanın karmaşık labirentlerinde, savunma hatlarını güçlendirmenin yollarından biri de saldırganları aldatmak ve onları kontrol altında tutmaktır. İşte burada devreye honeypotlar giriyor. Honeypotlar, adeta siber dünyanın cazibe merkezleri olarak, gerçek sistemlerimizi koruyarak saldırganları kendilerine çekiyor ve onların gerçek zarar vermelerini önlüyorlar.


## Honeypot Nedir?

Honeypot, siber güvenlikte sıkça kullanılan bir tuzaktır. Temel amacı, saldırganları aldatmak ve onları yanıltarak gerçek sistemlerden uzak tutmaktır. Honeypot'lar, saldırganların aktivitelerini izlemek, analiz etmek ve bu aktivitelerden elde edilen verilerle güvenlik stratejilerini geliştirmek için kullanılır​​.

## Honeypot Türleri

Honeypot'lar  birçok başlık altında incelenebilir([EK-1](#ek-1)). Bu yazıda etkileşim seviyelerine ve amaçlarına göre incelenecektir:

## Amaçlarına Göre Honeypotları
### Araştırma Honeypotları

Araştırma honeypotları, özellikle saldırganların teknikleri, taktikleri ve motivasyonları hakkında bilgi toplamak amacıyla tasarlanmıştır. Bu bal noktaları, veri toplama ve analiz için stratejik olarak konumlandırılmıştır ve tehdit analistleri ile araştırmacılar için büyük bir değer taşır.

#### Özellikler

- **Bilgi Toplama**: Saldırganların hareketlerini izleyerek, saldırı teknikleri ve stratejileri hakkında derinlemesine bilgi sağlar.
  
- **Analiz Amaçlı**: Elde edilen veriler, güvenlik açıkları ve olası tehditler hakkında içgörü kazanmak için kullanılır.

- **Değer**: Tehdit analistleri ve güvenlik araştırmacıları için paha biçilmez bir araçtır, çünkü gerçek dünya saldırıları hakkında gerçek zamanlı bilgi sağlar ve savunma stratejilerini güçlendirir.

### Üretim Honeypotları

Üretim honeypotları, canlı ve operasyonel ağlara entegre edilen, saldırganları aktif olarak meşgul etmek ve operasyonel güvenliği artırmak amacıyla kullanılan honeypot'lardır. Bu tür bal noktaları, kritik sistemlerin korunmasına ve meşru hedeflerin savunulmasına yardımcı olur.

#### Özellikler

- **Operasyonel Entegrasyon**: Canlı ağlara entegre edilir ve gerçek sistemler gibi davranır.
  
- **Saldırganları Meşgul Etmek**: Saldırganları etkileşime sokarak, gerçek sistemlere yönelik saldırıları önler veya sınırlar.

- **Güvenlik Artırma**: Genel güvenlik seviyelerini artırmak için kullanılır ve kritik altyapıları korumak için etkili bir araç olarak kabul edilir.

Bu sınıflandırma, honeypotların farklı amaçlar doğrultusunda nasıl kullanılabileceğini ve her birinin sağladığı faydaları açıkça ortaya koymaktadır. Araştırma honeypotları tehdit istihbaratı toplamak ve analiz etmek için ideal iken, üretim honeypotları operasyonel güvenliği artırmak ve saldırganları etkisiz hale getirmek için kullanılır.

## Etkileşim Seviyelerine Göre Honeypotlar
### Düşük Etkileşimli Honeypot'lar

- **Tanım**: Saldırganın sınırlı bir şekilde etkileşim kurmasına izin veren sistemlerdir.
- **Özellikler**: Gerçek sistemlerin yalnızca bazı hizmetlerini taklit ederler ve genellikle saldırı vektörlerini analiz etmek için kullanılırlar.
- **Örnek**: Honeyd, düşük etkileşimli honeypot'lara bir örnektir. Ağdaki belirli hizmetleri taklit ederek saldırı girişimlerini kaydeder​​.

### Orta Etkileşimli Honeypot'lar

- **Tanım**: Saldırganların sistemle daha fazla etkileşime girmesine izin veren, ancak tam bir işletim sistemi sunmayan sistemlerdir.
- **Özellikler**: Saldırganların belirli eylemlerini gerçekleştirmelerine izin vererek daha ayrıntılı bilgi toplanmasına olanak tanır.
- **Örnek**: Kippo, bir SSH sunucusunu taklit eden orta etkileşimli bir honeypot'tur.

### Yüksek Etkileşimli Honeypot'lar

- **Tanım**: Saldırganlara tam bir işletim sistemi sunarak onların tam potansiyellerini gösterebileceği sistemlerdir.
- **Özellikler**: Gerçek işletim sistemlerini kullanarak saldırganların tüm aktivitelerini yakalar ve analiz eder. Bu sayede daha derinlemesine analiz ve bilgi toplama imkanı sağlar.
- **Örnek**: Genellikle sanal makineler veya izole edilmiş fiziksel makineler kullanılarak oluşturulan sistemlerdir.

Bu türler, honeypot'un kullanım amacına ve güvenlik gereksinimlerine göre seçilir ve uygulanır. Her türün kendine özgü avantajları ve dezavantajları bulunmaktadır. Örneğin, düşük etkileşimli honeypot'lar daha az kaynak gerektirirken, yüksek etkileşimli honeypot'lar daha ayrıntılı ve derinlemesine bilgi sunar​​.


## Uygulamalı Senaryo
### Gerekli Yazılımlar
- Docker
- Docker Compose (sadece Tanner için)

### Cowrie ve Tanner Hakkında
- **Cowrie**: SSH ve Telnet protokollerini taklit eden bir honeypot. Saldırganların oturum açma girişimlerini kaydeder ve interaktif bir oturum sunar.
- **Tanner**: Web tabanlı saldırıları tespit etmek için kullanılan bir honeypot. Farklı web saldırılarını taklit eder ve kaydeder.

## Kurulum Adımları

#### 1. Cowrie Kurulumu

1. Docker komut satırını açın.
2. Aşağıdaki komutu çalıştırarak Cowrie konteynerini indirin ve başlatın:
    ```bash
    docker run -p 2222:2222 cowrie/cowrie:latest
    ```
   Bu komut, Cowrie'yi Docker konteynerinde çalıştırarak, yerel makinenizde 2222 numaralı portu Cowrie'nin 2222 numaralı portuna yönlendirir.

#### 2. Tanner Kurulumu

1. Proje dizinine gidin ve `docker-compose.yml` dosyasını oluşturun (Tanner belgelerinde dosyanın içeriğini bulabilirsiniz).
2. Aşağıdaki komutları sırasıyla çalıştırın:
    ```bash
    sudo docker-compose build
    sudo docker-compose up
    ```
   Bu komutlar, Docker Compose kullanarak Tanner'ı inşa eder ve başlatır.

### Test Adımları
--------------

### Nmap ile Port Tarama

Kurulumların ardından, Nmap kullanarak portları taradık(kali linux):

```python
┌──(kali㉿kali)-[~]
└─$ nmap 192.168.89.129 -p-
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-06-16 11:24 EDT
Nmap scan report for 192.168.89.129
Host is up (0.0014s latency).
Not shown: 65532 closed tcp ports (conn-refused)
PORT     STATE SERVICE
2222/tcp open  EtherNetIP-1
8090/tcp open  opsmessaging
8091/tcp open  jamlink

Nmap done: 1 IP address (1 host up) scanned in 4.53 seconds
```
----------------------
### Cowrie

Cowrie Ekran Çıktısı
Nmap taraması sonrasında Cowrie ekranında aşağıdaki bilgiler gözlemlendi:

```plaintext
2024-06-16T15:24:57+0000 [cowrie.ssh.factory.CowrieSSHFactory] New connection: 192.168.89.128:48956 (172.17.0.2:2222) [session: a6d97d506ea4]
2024-06-16T15:24:57+0000 [cowrie.ssh.transport.HoneyPotSSHTransport#info] connection lost
2024-06-16T15:24:57+0000 [HoneyPotSSHTransport,3,192.168.89.128] Connection lost after 0 second
```
### 2222 Port üzerinden inceleme

2222 portunu ssh ile giriş sağlıyoruz. İçeri girdiğimiz anda kod denemeleri gerçekleştiriyoruz.:

```python
┌──(kali㉿kali)-[~]
└─$ ssh -p 2222 root@192.168.89.129
root@192.168.89.129's password: 

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
root@svr04:~# ls 
root@svr04:~# pwd 
/root
root@svr04:~# cd home 
bash: cd: home: No such file or directory
root@svr04:~# cd /home/ 
root@svr04:/home# ls 
phil 
root@svr04:/home# cd phil/ 
root@svr04:/home/phil# ls 
root@svr04:/home/phil# pwd 
/home/phil
root@svr04:/home/phil# whoami 
root
```

 Cowrie ekranında aşağıdaki bilgiler gözlemlendi:

```plaintext
2024-06-16T15:45:25+0000 [cowrie.ssh.transport.HoneyPotSSHTransport#debug] starting service b'ssh-connection'
...
2024-06-16T15:45:25+0000 [twisted.conch.ssh.session#info] Getting shell
2024-06-16T15:46:17+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: ls
2024-06-16T15:46:17+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: ls
2024-06-16T15:46:19+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: pwd
2024-06-16T15:46:19+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: pwd
2024-06-16T15:46:25+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: cd home
2024-06-16T15:46:25+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: cd home
2024-06-16T15:46:29+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: cd /home/
2024-06-16T15:46:29+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: cd /home/
2024-06-16T15:46:32+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: ls
2024-06-16T15:46:32+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: ls
2024-06-16T15:46:35+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: cd phil/
2024-06-16T15:46:35+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: cd phil/
2024-06-16T15:46:36+0000 [HoneyPotSSHTransport,1,192.168.89.128] CMD: ls
2024-06-16T15:46:36+0000 [HoneyPotSSHTransport,1,192.168.89.128] Command found: ls
```
### Tanner
```python
┌──(kali㉿kali)-[~]
└─$ nikto --host 192.168.89.129 --port 8091
- Nikto v2.5.0
---------------------------------------------------------------------------
+ Target IP:          192.168.89.129
+ Target Hostname:    192.168.89.129
+ Target Port:        8091
+ Start Time:         2024-06-16 12:01:57 (GMT-4)
---------------------------------------------------------------------------
+ Server: Python/3.9 aiohttp/3.9.5
+ /: The anti-clickjacking X-Frame-Options header is not present. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options
+ /: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type. See: https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ /: Apache is vulnerable to XSS via the Expect header. See: http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-3918
+ Python/3.9 appears to be outdated (current is at least 3.9.6).
+ OPTIONS: Allowed HTTP Methods: GET, HEAD .
+ /#wp-config.php#: #wp-config.php# file found. This file contains the credentials.
+ 8106 requests: 0 error(s) and 6 item(s) reported on remote host
+ End Time:           2024-06-16 12:02:22 (GMT-4) (25 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

```

 Tanner ekranında gözlemlenen bazı çıktılar:

```plaintext
tanner_web    | 
tanner_web    |     b'GET ../../../../../../../../../../etc/* HTTP/1.1'
tanner_web    |           ^
tanner_web    | Error handling request
tanner_web    | Traceback (most recent call last):
tanner_web    |   File "/opt/tanner/tanner-env/lib/python3.9/site-packages/aiohttp/web_protocol.py", line 350, in data_received
```
```plaintext
tanner_web    |     b'<script>alert(1)</script> / HTTP/1.1'
tanner_web    |       ^
tanner_web    | Error handling request
tanner_web    | Traceback (most recent call last):
tanner_web    |   File "/opt/tanner/tanner-env/lib/python3.9/site-packages/aiohttp/web_protocol.py", line 350, in data_received
```
--------------------------------------------
### EK-1
## Honeypot Types and Classifications

| Sınıflandırma Kategorisi       | Honeypot Türü                        | Tanım                                                                                                                                  |
| ------------------------------ | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| Amaca Göre                     | Araştırma Honeypotları (ReH)         | Bu honeypotlar, saldırganların teknikleri, taktikleri ve motivasyonları hakkında bilgi toplamak için tasarlanmıştır. Organizasyonlar için doğrudan üretken bir değeri yoktur, ancak gelecekteki güvenlik için dolaylı bir değer sağlar. |
|                                | Üretim Honeypotları (PrH)            | Bu honeypotlar, ağları korumak ve tehditleri azaltmak için tasarlanmıştır. Ana sunucuları korumak için favori güvenlik açıklarını ve hizmetleri simüle ederler. |
| Etkileşim Seviyesine Göre      | Yüksek Etkileşimli Honeypotlar (HiH) | Bu honeypotlar, bir sistemin tüm parçalarını ve hizmetlerini taklit eder. Saldırganların gerçek bir sistemden ayırt etmesi zordur. Ancak, başarılı bir şekilde ele geçirilirse, ağda güçlü saldırılar başlatabilirler. |
|                                | Düşük Etkileşimli Honeypotlar (LoH)  | Bu honeypotlar, bir işletim sisteminin belirli bir parçasını ve belirli sayıda hizmeti taklit eder. Tasarımı ve uygulanması daha basittir ve ele geçirildiğinde daha az zarar verir. |
|                                | Orta Etkileşimli Honeypotlar (MeH)   | Bu honeypotların etkileşim seviyesi, düşük ve yüksek etkileşimli honeypotlar arasında yer alır. Tüm uygulama katmanı hizmetlerini taklit ederler. |
| Uygulama Yöntemine Göre        | Fiziksel Honeypotlar (PhH)           | Ayrı bir makinede uygulanır ve benzersiz bir IP adresine sahiptir. Güvenliği özel dikkat gerektirir.                                  |
|                                | Sanal Honeypotlar (ViH)              | Sanal honeypotlar, ayrı fiziksel makineler gerektirmez. Tek bir fiziksel sunucuda birden fazla sanal honeypot barındırılabilir.       |
| Aktivite Seviyesine Göre       | Pasif Honeypotlar (PaH)              | Bu honeypotların amacı, diğer sistemleri koruma garantisi vermeden saldırganlardan bilgi toplamaktır.                                 |
|                                | Aktif Honeypotlar (AcH)              | Potansiyel saldırganları kritik sistemlerden uzaklaştırmak ve meşgul etmek için tasarlanmıştır.                                       |
| Çalışma Tarafına Göre          | Sunucu Taraflı Honeypotlar (SeH)     | Bu honeypotlar, sunucu tarafı güvenlik açıklarını ve güvenlik sızıntılarını tespit etmeye çalışır.                                   |
|                                | İstemci Taraflı Honeypotlar (ClH)    | Bu honeypotlar, kötü amaçlı sunucuları bulmak ve istemci tarafı güvenlik açıklarını tespit etmek için tasarlanmıştır.                |
| Davranış Türüne Göre               | Statik Honeypotlar (StH)             | Sabit bir yapılandırmaya sahiptir ve farklı saldırganlar ve zamanlarda aynı şekilde davranır.                                         |
|                                | Dinamik Honeypotlar (DyH)            | Ağ durumundaki değişikliklere dinamik olarak uyum sağlar ve davranışlarını polimorfik saldırılara yanıt olarak değiştirir.            |
| Çeşitlilik Durumuna Göre      | Homojen Honeypotlar (HoH)            | Ağda benzer tuzaklar kullanır ve sadece belirli türde saldırıları tespit edebilir ve geciktirebilir.                                  |
|                                | Heterojen Honeypotlar (HeH)          | Heterojen tuzaklar ve çeşitli güvenlik araçları kullanır, bu yüzden saldırıları tespit etmede daha güçlüdür.                         |

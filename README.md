# Kapsamlı Docker Rehberi: Modern Uygulama Geliştirme ve Dağıtımın Anahtarı

**Yazar:** Cihan Atas <atascihan115@gmail.com>
*(Sercan Bayram'ın temel komut listesinden yararlanılmıştır)*

<!-- Bu README.md dosyası, sağlanan LaTeX kaynağından otomatik olarak dönüştürülmüştür. -->

## İçindekiler

- [Önsöz](#önsöz)
- [Docker'a Giriş: Konteyner Devrimini Anlamak](#dockera-giriş-konteyner-devrimini-anlamak)
  - [Docker Nedir? Ne Değildir?](#docker-nedir-ne-değildir)
  - [Konteyner Teknolojisi ve VM'lerden Farkı](#konteyner-teknolojisi-ve-vmlerden-farkı)
  - [Docker'in Avantajları](#dockerin-avantajları)
  - [Docker Mimarisi: Bileşenlerin Çalışması](#docker-mimarisi-bileşenlerin-çalışması)
- [Docker Kurulumu ve İlk Adımlar](#docker-kurulumu-ve-i̇lk-adımlar)
  - [Platforma Özel Kurulum](#platforma-özel-kurulum)
  - [Kurulum Sonrası Test ve Bilgi Alma](#kurulum-sonrası-test-ve-bilgi-alma)
  - [Yardımcı Araçlar](#yardımcı-araçlar)
- [Temel Docker Kavramları ve Komutları](#temel-docker-kavramları-ve-komutları)
  - [Imaj Yönetimi](#imaj-yönetimi)
    - [İmaj Çekme (Pulling Images)](#i̇maj-çekme-pulling-images)
    - [Lokal İmajları Listeleme](#lokal-i̇majları-listeleme)
    - [İmaj Oluşturma (Building Images)](#i̇maj-oluşturma-building-images)
    - [İmaj Etiketleme (Tagging Images)](#i̇maj-etiketleme-tagging-images)
    - [İmajı Registry'ye Yükleme (Pushing Images)](#i̇majı-registryye-yükleme-pushing-images)
    - [İmaj Silme (Removing Images)](#i̇maj-silme-removing-images)
    - [İmaj Detaylarını İnceleme](#i̇maj-detaylarını-i̇nceleme)
    - [İmaj Geçmişini Görme](#i̇maj-geçmişini-görme)
    - [İmaj Kaydetme ve Yükleme (Save/Load)](#i̇maj-kaydetme-ve-yükleme-saveload)
  - [Konteyner Yönetimi](#konteyner-yönetimi)
    - [Konteyner Çalıştırma (Running Containers)](#konteyner-çalıştırma-running-containers)
    - [Çalışan/Tüm Konteynerleri Listeleme](#çalışantüm-konteynerleri-listeleme)
    - [Konteynerleri Başlatma, Durdurma, Yeniden Başlatma](#konteynerleri-başlatma-durdurma-yeniden-başlatma)
    - [Konteyner Silme (Removing Containers)](#konteyner-silme-removing-containers)
    - [Konteyner Loglarını Görme](#konteyner-loglarını-görme)
    - [Çalışan Konteyner İçinde Komut Çalıştırma](#çalışan-konteyner-i̇çinde-komut-çalıştırma)
    - [Konteyner Kaynak Kullanımını İzleme](#konteyner-kaynak-kullanımını-i̇zleme)
    - [Konteyner Detaylarını İnceleme](#konteyner-detaylarını-i̇nceleme)
    - [Dosya Kopyalama (Host <-> Konteyner)](#dosya-kopyalama-host---konteyner)
    - [Diğer Konteyner Komutları](#diğer-konteyner-komutları)
  - [Docker Volume ve Veri Yönetimi: Verilerinizi Kalıcı Hale Getirmek](#docker-volume-ve-veri-yönetimi-verilerinizi-kalıcı-hale-getirmek)
    - [Neden Gerekli?](#neden-gerekli)
    - [Veri Kalıcılığı Yöntemleri](#veri-kalıcılığı-yöntemleri)
    - [Volume Komutları](#volume-komutları)
  - [Docker Networking: Konteynerleri Birbirine Bağlamak](#docker-networking-konteynerleri-birbirine-bağlamak)
    - [Temel Kavramlar](#temel-kavramlar)
    - [Network Tipleri (Drivers)](#network-tipleri-drivers)
    - [Network Komutları](#network-komutları)
    - [Konteynerler Arası İletişim](#konteynerler-arası-i̇letişim)
    - [Port Yönlendirme (Port Mapping)](#port-yönlendirme-port-mapping)
- [Dockerfile: İmajları İnşa Etmek](#dockerfile-i̇majları-i̇nşa-etmek)
  - [Dockerfile Nedir?](#dockerfile-nedir)
  - [Temel Dockerfile Direktifleri](#temel-dockerfile-direktifleri)
  - [Örnek Dockerfile Yapıları](#örnek-dockerfile-yapıları)
    - [Basit Node.js Uygulaması](#basit-nodejs-uygulaması)
    - [Basit Python/Flask Uygulaması](#basit-pythonflask-uygulaması)
    - [Multi-stage Build Örneği (Basit Go Uygulaması)](#multi-stage-build-örneği-basit-go-uygulaması)
  - [.dockerignore Dosyası](#dockerignore-dosyası)
- [Docker Compose: Çoklu Konteyner Uygulamalarını Yönetmek](#docker-compose-çoklu-konteyner-uygulamalarını-yönetmek)
  - [Neden Docker Compose?](#neden-docker-compose)
  - [Temel Komutlar](#temel-komutlar)
  - [`docker-compose.yml` Dosyası Yapısı](#docker-composeyml-dosyası-yapısı)
    - [Örnek `docker-compose.yml`](#örnek-docker-composeyml)
    - [Environment Variable Yönetimi](#environment-variable-yönetimi)
    - [Scaling with Compose](#scaling-with-compose)
- [Docker Swarm (Temel Seviye): Dahili Konteyner Orkestrasyonu](#docker-swarm-temel-seviye-dahili-konteyner-orkestrasyonu)
  - [Neden Orkestrasyon?](#neden-orkestrasyon)
  - [Docker Swarm Nedir?](#docker-swarm-nedir)
  - [Swarm Mimarisi](#swarm-mimarisi)
  - [Temel Swarm Komutları](#temel-swarm-komutları)
  - [Replication vs Global Services](#replication-vs-global-services)
  - [Rolling Updates and Rollbacks](#rolling-updates-and-rollbacks)
- [Güvenlik En İyi Uygulamaları](#güvenlik-en-i̇yi-uygulamaları)
  - [İmaj Güvenliği](#i̇maj-güvenliği)
  - [Konteyner Çalışma Zamanı Güvenliği](#konteyner-çalışma-zamanı-güvenliği)
  - [Secret Yönetimi](#secret-yönetimi)
  - [Network Güvenliği](#network-güvenliği)
  - [Host ve Daemon Güvenliği](#host-ve-daemon-güvenliği)
- [Monitoring ve Logging](#monitoring-ve-logging)
  - [Neden Önemli?](#neden-önemli-1)
  - [Docker Dahili Araçlar](#docker-dahili-araçlar)
  - [Logging Mimarileri ve Stratejileri](#logging-mimarileri-ve-stratejileri)
  - [Monitoring Araçları ve Yaklaşımları](#monitoring-araçları-ve-yaklaşımları)
- [CI/CD Pipeline'larında Docker Kullanımı](#cicd-pipelinelarında-docker-kullanımı)
  - [Neden Docker CI/CD İçin İdealdir?](#neden-docker-cicd-i̇çin-i̇dealdir)
  - [Tipik CI/CD Akışı (Docker ile)](#tipik-cicd-akışı-docker-ile)
  - [Docker ve Popüler CI/CD Araçları](#docker-ve-popüler-cicd-araçları)
  - [Dağıtım Stratejileri (Deployment Strategies)](#dağıtım-stratejileri-deployment-strategies)
- [Sorun Giderme ve Debugging](#sorun-giderme-ve-debugging)
  - [Temel Sorun Giderme Komutları (Tekrar)](#temel-sorun-giderme-komutları-tekrar)
  - [Yaygın Hatalar ve Çözümleri](#yaygın-hatalar-ve-çözümleri)
- [İleri Seviye Konular ve Ekosistem](#i̇leri-seviye-konular-ve-ekosistem)
  - [Kubernetes ile Docker Entegrasyonu](#kubernetes-ile-docker-entegrasyonu)
  - [Docker API ve SDK'lar](#docker-api-ve-sdklar)
  - [Özel (Custom) Network ve Volume Sürücüleri (Plugins)](#özel-custom-network-ve-volume-sürücüleri-plugins)
  - [BuildKit ve Gelişmiş Build Seçenekleri](#buildkit-ve-gelişmiş-build-seçenekleri)
  - [Windows Konteynerları](#windows-konteynerları)
  - [ARM Mimarisi ve Multi-Arch İmajlar](#arm-mimarisi-ve-multi-arch-i̇majlar)
  - [Rootless Docker](#rootless-docker)
- [Sonuç ve Öğrenme Kaynakları](#sonuç-ve-öğrenme-kaynakları)
  - [Faydalı Kaynaklar](#faydalı-kaynaklar)
- [Komut Referansı](#komut-referansı)
  - [Docker Kurulum, Bilgi ve Oturum Komutları](#docker-kurulum-bilgi-ve-oturum-komutları)
  - [Imaj Yönetimi Komutları](#imaj-yönetimi-komutları)
  - [Konteyner Yaşam Döngüsü Komutları](#konteyner-yaşam-döngüsü-komutları)
  - [Konteyner Etkileşim ve İnceleme Komutları](#konteyner-etkileşim-ve-i̇nceleme-komutları)
  - [Ağ Yönetimi Komutları](#ağ-yönetimi-komutları)
  - [Volume (Birim) Yönetimi Komutları](#volume-birim-yönetimi-komutları)
  - [Docker Compose Komutları (CLI Plugin: `docker compose`)](#docker-compose-komutları-cli-plugin-docker-compose)
  - [Sistem Yönetimi ve Temizlik Komutları](#sistem-yönetimi-ve-temizlik-komutları)
  - [Gelişmiş, Swarm ve Çeşitli Komutlar](#gelişmiş-swarm-ve-çeşitli-komutlar)

---

# Önsöz

Bu rehber, Docker'ı sıfırdan başlayarak kavramak ve günlük iş akışlarınıza entegre etmek isteyen geliştiriciler, sistem yöneticileri ve teknoloji meraklıları için hazırlanmıştır. Amacımız, Docker'ın temel kavramlarını, en sık kullanılan komutlarını, en iyi uygulamalarını ve ekosistemdeki yerini kapsamlı bir şekilde sunmaktır. Bu birleştirilmiş rehberde, hem teorik altyapıyı sağlam bir şekilde kurmayı hem de pratik komut kullanımında yetkinlik kazanmanızı hedefliyoruz. Adım adım ilerleyerek Docker dünyasında kendinizi rahat hissetmenizi sağlayacağız.

# Docker'a Giriş: Konteyner Devrimini Anlamak

## Docker Nedir? Ne Değildir?

Docker, uygulamaları ve bağımlılıklarını **konteyner** adı verilen hafif, taşınabilir ve yalıtılmış ortamlarda paketlemeye, dağıtmaya ve çalıştırmaya yarayan açık kaynaklı bir platform ve araç setidir.

**Ne Değildir?**

*   **Sadece bir Sanallaştırma Aracı Değildir:** Geleneksel sanal makinelerin (VM) aksine, Docker işletim sistemi seviyesinde sanallaştırma kullanarak daha verimli bir izolasyon sunar. Kendi çekirdeğini (kernel) çalıştırmaz, ana makinenin çekirdeğini paylaşır.
*   **Bir Yapılandırma Yönetim Aracı Değildir:** Ansible, Chef, Puppet gibi araçların yerini almaz, ancak onlarla birlikte veya onların içinde kullanılabilir. Docker, ortamın kendisini paketlerken, bu araçlar genellikle ortamın içindeki yapılandırmayı yönetir.
*   **Bir Bulut Platformu Değildir:** AWS, Azure, GCP gibi platformlar değildir, ancak bu platformlarda konteynerleri çalıştırmak için temel bir teknoloji olarak yaygın şekilde kullanılır.

## Konteyner Teknolojisi ve VM'lerden Farkı

Temel fark, izolasyon seviyesi ve kaynak kullanımıdır:

**Sanal Makineler (VM'ler):**

*   Her VM kendi tam işletim sistemini (kernel dahil) çalıştırır.
*   Donanım üzerinde bir **hipervizör** katmanı gerektirir (örn: VMware, VirtualBox, KVM).
*   Kaynak tüketimi yüksektir (disk, RAM, CPU).
*   Başlatılmaları dakikalar sürebilir.
*   Tam donanım ve işletim sistemi izolasyonu sağlarlar.

**Konteynerler (Docker):**

*   Ana makinenin (host) işletim sistemi çekirdeğini (kernel) paylaşırlar.
*   İzolasyon, process ve dosya sistemi seviyesinde sağlanır (Linux'ta `namespaces` ve `cgroups` gibi kernel özellikleri kullanılır).
*   Çok daha hafiftirler, saniyeler içinde başlarlar.
*   Daha az kaynak tüketirler (disk, RAM, CPU).
*   Kernel paylaşıldığı için VM'ler kadar güçlü bir güvenlik izolasyonu sunmazlar (ancak çoğu durum için yeterlidir).

**Analoji:** VM'ler, her biri tamamen ayrı bir ev gibidir (kendi temeli, çatısı, tesisatı vardır). Konteynerler ise, aynı apartmandaki daireler gibidir (temel ve ana yapıyı paylaşır, fakat içerileri ayrıdır ve birbirini doğrudan etkilemez).

## Docker'in Avantajları

*   **Tutarlılık:** "Benim makinemde çalışıyordu" sorununu ortadan kaldırır. Geliştirme, test ve üretim ortamlarının (neredeyse) aynı olmasını sağlar.
*   **Hız:** Konteynerler saniyeler içinde başlatılıp durdurulabilir, bu da geliştirme ve dağıtım (CI/CD) süreçlerini inanılmaz hızlandırır.
*   **Taşınabilirlik:** Docker konteynerleri, Docker'ın çalıştığı her yerde (lokal makine, test sunucusu, bulut, Raspberry Pi) aynı şekilde çalışır.
*   **Verimlilik:** VM'lere göre çok daha az kaynak tüketir, aynı donanım üzerinde daha fazla uygulamanın paralel çalışmasını sağlar.
*   **İzolasyon:** Uygulamalar ve bağımlılıkları birbirini etkilemeden, kendi yalıtılmış ortamlarında çalışır. Bağımlılık çakışmalarını önler.
*   **Mikroservis Mimarileri:** Mikroservisleri paketlemek, dağıtmak, ölçeklemek ve yönetmek için ideal bir platformdur.
*   **Hızlı Ölçeklenme:** İhtiyaç anında servis kopyalarını (konteynerlerini) yatay olarak hızla artırıp azaltmak mümkündür.
*   **Sürüm Kontrolü ve Dağıtım:** Dockerfile'lar ve imajlar sayesinde altyapıyı kod olarak (Infrastructure as Code) yönetmek ve dağıtımları tekrarlanabilir hale getirmek kolaylaşır.

## Docker Mimarisi: Bileşenlerin Çalışması

Docker platformu temel olarak birkaç ana bileşenden oluşur:

*   **Docker Daemon (`dockerd`):** Arka planda çalışan ve asıl işi yapan ana servistir. İmajları, konteynerleri, ağları (network) ve birimleri (volume) oluşturmaktan, çalıştırmaktan ve yönetmekten sorumludur. API isteklerini dinler ve Docker nesnelerini yönetir. Genellikle sunucu veya lokal makinede bir sistem servisi olarak çalışır.
*   **Docker Client (`docker`):** Kullanıcıların Docker Daemon ile etkileşim kurmasını sağlayan komut satırı arayüzüdür (CLI). Kullandığımız `docker run`, `docker pull`, `docker ps` gibi komutlar aslında Client tarafından alınır ve Daemon'a API üzerinden iletilir. Client ve Daemon aynı makinede veya farklı makinelerde olabilir.
*   **Docker Registry:** Docker imajlarının saklandığı ve dağıtıldığı depodur.
    *   **Docker Hub:** Docker Inc. tarafından yönetilen, varsayılan halka açık registry'dir. Binlerce hazır imaj bulunur.
    *   **Özel Registry'ler:** Şirket içinde veya bulut sağlayıcılarda (örn: AWS ECR, Google GCR, Azure ACR, GitLab Registry, Harbor) kendi özel imajlarınızı saklamak için kullanılabilir.
*   **Docker Nesneleri (Objects):**
    *   **Images (İmajlar):** Konteyner oluşturmak için kullanılan, salt okunur (read-only) şablonlardır. Bir imaj; uygulamayı, gerekli kütüphaneleri, çalışma zamanı ortamını, sistem araçlarını, kodları ve yapılandırma dosyalarını içerir. İmajlar, katmanlı (layered) bir yapıya sahiptir ve genellikle bir `Dockerfile` ile oluşturulur.
    *   **Containers (Konteynerler):** Docker imajlarının çalıştırılabilir örnekleridir (instance). Bir imajdan birden fazla, birbirinden bağımsız konteyner oluşturulabilir. Her konteyner kendi yalıtılmış dosya sistemine, ağ arayüzüne ve process alanına sahiptir, ancak ana makinenin kernel'ini paylaşır.
    *   **Volumes (Birimler):** Konteynerler silindiğinde verilerin kaybolmaması için kalıcı depolama sağlamanın tercih edilen yoludur. Docker tarafından yönetilirler ve konteyner yaşam döngüsünden bağımsızdırlar. Veritabanı dosyaları, kullanıcı yüklemeleri gibi kalıcı olması gereken veriler için kullanılır.
    *   **Networks (Ağlar):** Konteynerlerin birbirleriyle ve dış dünya ile iletişim kurmasını sağlayan sanal ağlardır. Docker, farklı ağ sürücüleri (bridge, host, overlay vb.) sunar.

# Docker Kurulumu ve İlk Adımlar

## Platforma Özel Kurulum

Docker'ı farklı işletim sistemlerine kurmak için genellikle aşağıdaki yöntemler kullanılır:

**Windows:**

*   **Docker Desktop for Windows:** En yaygın ve önerilen yöntemdir. Windows 10/11 (Pro, Enterprise veya Education 64-bit) gerektirir. Arka planda WSL 2 (Windows Subsystem for Linux 2) veya Hyper-V teknolojisini kullanır. WSL 2 genellikle daha iyi performans sunar ve Windows Home sürümünde de çalışır.
*   Kurulumu <https://docs.docker.com/desktop/install/windows-install/> adresinden indirebilirsiniz.

**macOS:**

*   **Docker Desktop for Mac:** macOS için önerilen yöntemdir. Apple Silicon (M1/M2/M3) veya Intel işlemcili Mac'lerde çalışır. Arka planda macOS'un sanallaştırma teknolojilerini kullanır.
*   Kurulumu <https://docs.docker.com/desktop/install/mac-install/> adresinden indirebilirsiniz.

**Linux:**

*   **Docker Engine:** Çeşitli Linux dağıtımları (Ubuntu, Debian, CentOS, Fedora vb.) için doğrudan kurulabilir. Docker Desktop Linux için de mevcuttur ancak genellikle sunucularda veya sadece CLI ihtiyacı olanlar için Docker Engine yeterlidir.
*   **Önerilen Yöntem:** Resmi Docker deposunu kullanarak paket yöneticisi (`apt` for Ubuntu/Debian, `yum/dnf` for CentOS/Fedora) ile kurmaktır. Detaylı talimatlar için: <https://docs.docker.com/engine/install/>
*   **Kurulum Sonrası Adım (Önemli):** Genellikle kurulumdan sonra mevcut kullanıcınızı `docker` grubuna eklemeniz gerekir ki `sudo` kullanmadan Docker komutlarını çalıştırabilesiniz.
    ```bash
    # Grup yoksa (genellikle vardır): sudo groupadd docker
    sudo usermod -aG docker $USER
    # Değişikliğin etkili olması için oturumu kapatıp açın veya 'newgrp docker' komutunu deneyin
    ```

**Docker Toolbox (Eski Sistemler İçin):**
Docker Desktop'ın sistem gereksinimlerini karşılamayan eski Windows veya macOS sürümleri için VirtualBox tabanlı bir alternatifti. **Artık önerilmez** ve aktif olarak geliştirilmemektedir. Mümkünse Docker Desktop'a geçin veya Linux kullanın.

## Kurulum Sonrası Test ve Bilgi Alma

Kurulumun başarılı olup olmadığını ve sisteminiz hakkındaki bilgileri kontrol etmek için temel komutlar:

1.  `docker --version`
    **Docker Client sürümünü gösterir:**
    ```bash
    docker --version
    # Çıktı örneği: Docker version 24.0.5, build ced0996
    ```
    **Açıklama:** Yüklü Docker istemci (client) sürümünü kısaca gösterir.

2.  `docker version`
    **Client ve Daemon sürüm detaylarını gösterir:**
    ```bash
    docker version
    # Çıktı örneği (kısaltılmış):
    # Client:
    #  Version:           24.0.5
    #  ...
    # Server: Docker Engine - Community
    #  Engine:
    #   Version:          24.0.5
    #   ...
    ```
    **Açıklama:** Hem Docker İstemcisi hem de Docker Motoru (Sunucu/Daemon) için ayrıntılı sürüm bilgilerini gösterir.

3.  `docker info`
    **Docker sistemi hakkında detaylı bilgi:**
    ```bash
    docker info
    # Çıktı örneği (kısaltılmış):
    # Client: ...
    # Server:
    #  Containers: 10
    #  Running: 3
    #  Paused: 0
    #  Stopped: 7
    #  Images: 55
    #  Server Version: 24.0.5
    #  Storage Driver: overlay2
    #  ...
    #  Operating System: Ubuntu 22.04.3 LTS
    #  Kernel Version: 5.15.0-88-generic
    #  ...
    ```
    **Açıklama:** Konteyner ve imaj sayısı, depolama sürücüsü, çekirdek sürümü, işletim sistemi, ağ ve volume bilgileri dahil olmak üzere Docker kurulumu hakkında sistem genelinde bilgi gösterir. Sorun gidermede çok faydalıdır.

4.  `docker run hello-world`
    **İlk test konteynerini çalıştırma:**
    ```bash
    docker run hello-world
    # Çıktı örneği (kısaltılmış):
    # Unable to find image 'hello-world:latest' locally
    # latest: Pulling from library/hello-world
    # ...
    # Status: Downloaded newer image for hello-world:latest
    #
    # Hello from Docker!
    # This message shows that your installation appears to be working correctly.
    # ...
    ```
    **Açıklama:** Bu komut, Docker kurulumunuzun temel işlevselliğini test etmek için tasarlanmıştır. Aşağıdaki adımları gerçekleştirir:
    a)  Client, Daemon’a `hello-world` imajından bir konteyner çalıştırma isteği gönderir.
    b)  Daemon, `hello-world` imajını lokalde (makinenizde) arar.
    c)  Bulamazsa, varsayılan registry olan Docker Hub'dan imajı indirir (`pull` işlemi).
    d)  İmaj indirildikten sonra, bu imajdan yeni bir konteyner oluşturur (`create` işlemi).
    e)  Konteyneri başlatır (`start` işlemi).
    f)  Konteyner içindeki program (`hello`) çalışır, ekrana bir karşılama mesajı basar ve görevi bittiği için hemen çıkış yapar.
    g)  Konteyner otomatik olarak durur.

    Ekranda "Hello from Docker!" mesajını görüyorsanız, kurulumunuz büyük olasılıkla başarılıdır.

## Yardımcı Araçlar

**Docker Compose:**

*   Çoklu konteynerli uygulamaları (örneğin bir web sunucusu, bir veritabanı ve bir cache servisi) tek bir YAML dosyası (`docker-compose.yml`) ile tanımlamak, yapılandırmak ve yönetmek için kullanılan bir araçtır.
*   `docker-compose up` gibi basit komutlarla tüm uygulama yığınını (stack) başlatmayı ve `docker-compose down` ile durdurup kaldırmayı sağlar.
*   Geliştirme ortamları ve basit dağıtımlar için çok popülerdir.
*   Genellikle Docker Desktop ile birlikte gelir. Linux'ta Docker Engine kullanıyorsanız, ayrıca kurmanız gerekebilir (<https://docs.docker.com/compose/install/>).
*   Modern Docker sürümlerinde `docker compose` (tire olmadan) komutu, Docker CLI'a entegre edilmiştir ve kullanımı teşvik edilmektedir.

**Docker Machine:**

*   Uzak makinelerde (sanal veya fiziksel) Docker host'ları (Docker Engine kurulu makineler) oluşturmak ve yönetmek için kullanılan bir araçtı.
*   Bulut sağlayıcılarında (AWS, Azure, DigitalOcean vb.) veya yerel sanallaştırma yazılımlarıyla (VirtualBox, VMware) Docker host'ları hazırlamayı kolaylaştırıyordu.
*   Günümüzde Docker Desktop'ın yaygınlaşması ve bulut sağlayıcılarının kendi yönetilen Docker/Kubernetes servislerini sunmasıyla kullanımı azalmıştır ve **artık aktif olarak geliştirilmemektedir**.

# Temel Docker Kavramları ve Komutları

Bu bölümde Docker'ın temel nesneleri olan İmajlar, Konteynerler, Volume'lar ve Network'ler ile nasıl çalışılacağını ve ilgili temel komutları öğreneceğiz.

## Imaj Yönetimi

İmajlar, konteynerlerimizi oluşturmak için kullandığımız şablonlardır.

### İmaj Çekme (Pulling Images)

Uzak bir registry'den (genellikle Docker Hub) imaj indirme işlemidir.

**Bir imajı registry'den çekme:**
```bash
docker pull [SEÇENEKLER] İMAJ_ADI[:ETİKET]

# Örnekler:
docker pull ubuntu          # Ubuntu'nun 'latest' etiketli imajını çeker
docker pull ubuntu:20.04    # Ubuntu'nun '20.04' etiketli imajını çeker
docker pull nginx:1.21-alpine # Nginx'in belirli bir Alpine versiyonunu çeker
docker pull registry.example.com/my-app:v2 # Özel registry'den çeker
docker pull --platform linux/amd64 node:18 # Belirli bir platform için çeker
```
**Açıklama:** `docker pull` komutu, belirtilen imajı ve etiketi (tag) varsayılan olarak Docker Hub'dan veya belirtilmişse başka bir registry'den yerel makinenize indirir. Etiket belirtilmezse, `latest` etiketi varsayılır (ancak `latest` her zaman en son stabil sürüm anlamına gelmeyebilir, dikkatli olun).

### Lokal İmajları Listeleme

Mevcut sisteminizdeki indirilmiş veya oluşturulmuş imajları görme.

**Lokal imajları listeleme:**
```bash
docker images [SEÇENEKLER] [DEPO[:ETİKET]]
docker image ls # Alternatif ve daha modern komut

# Örnekler:
docker images
docker image ls
docker images ubuntu # Sadece 'ubuntu' deposuna ait imajları listeler
docker images -a     # Ara katmanlar dahil tüm imajları gösterir (genellikle kullanılmaz)
docker images -q     # Sadece imaj ID'lerini listeler (scripting için kullanışlı)
```
**Açıklama:** `docker images` veya `docker image ls`, lokalinizdeki imajları; depo adı (REPOSITORY), etiket (TAG), imaj ID'si (IMAGE ID), oluşturulma zamanı (CREATED) ve boyutu (SIZE) gibi bilgilerle listeler.

### İmaj Oluşturma (Building Images)

Bir `Dockerfile` kullanarak kendi özel imajlarınızı oluşturma.

**Dockerfile'dan imaj oluşturma:**
```bash
docker build [SEÇENEKLER] PATH | URL | -

# Temel Örnek:
# Mevcut dizindeki Dockerfile'ı kullanarak 'my-app:1.0' adında bir imaj oluşturur.
docker build -t my-app:1.0 .

# Diğer Örnekler:
# Farklı bir dizindeki Dockerfile'ı kullanma:
docker build -t my-app:1.0 /path/to/app/context

# Farklı bir Dockerfile adı belirtme:
docker build -f Dockerfile.prod -t my-app:prod .

# Build argümanı geçirme:
docker build --build-arg USER=cihan -t my-app .

# Cache kullanmadan build etme:
docker build --no-cache -t my-app .
```
**Açıklama:** `docker build` komutu, belirtilen yoldaki (genellikle `.` yani mevcut dizin) `Dockerfile` dosyasını okur ve içindeki talimatları adım adım uygulayarak yeni bir Docker imajı oluşturur. `-t` seçeneği ile oluşturulan imaja bir isim (repository) ve etiket (tag) verilir (`isim:etiket` formatında). Build işlemi sırasında Dockerfile'daki her komut genellikle bir imaj katmanı oluşturur. Build bağlamı (context), build işlemi sırasında Docker daemon'a gönderilen dosya ve dizinlerdir.

### İmaj Etiketleme (Tagging Images)

Mevcut bir imaja ek bir isim ve/veya etiket atama. Genellikle bir imajı registry'ye push etmeden önce kullanılır.

**Bir imajı etiketleme:**
```bash
docker tag KAYNAK_İMAJ[:ETİKET] HEDEF_İMAJ[:ETİKET]
docker image tag # Alternatif komut

# Örnekler:
# 'my-app:1.0' imajını Docker Hub'a push etmek için yeniden etiketleme
docker tag my-app:1.0 cihanatas/my-app:1.0

# Bir imaj ID'sini kullanarak etiketleme
docker tag 4e50cbc1b7c3 my-local-app:latest
```
**Açıklama:** `docker tag` komutu, mevcut bir imaja (kaynak) yeni bir referans (hedef) oluşturur. Aslında yeni bir imaj kopyası oluşturmaz, sadece aynı imaj ID'sine işaret eden farklı bir isim/etiket atar. Bu, imajları farklı isimlerle veya sürümlerle yönetmek ve özellikle registry'lere (örneğin Docker Hub kullanıcı adınızla başlayan bir depo adı) push etmek için gereklidir.

### İmajı Registry'ye Yükleme (Pushing Images)

Oluşturduğunuz veya etiketlediğiniz bir imajı bir registry'ye (Docker Hub veya özel registry) gönderme.

**Bir imajı registry'ye yükleme:**
```bash
docker push [SEÇENEKLER] İSİM[:ETİKET]
docker image push # Alternatif komut

# Örnek (Önce login olmanız gerekir: docker login):
docker push cihanatas/my-app:1.0
docker push registry.example.com/internal-app:v3
```
**Açıklama:** `docker push` komutu, belirtilen imajı (ve katmanlarını) hedef registry'ye yükler. Push edeceğiniz imajın adının genellikle registry'nin adresini ve/veya kullanıcı/proje adını içermesi gerekir (örn: `dockerhubkullaniciadi/repoadi:etiket` veya `ozelregistry.com/proje/repoadi:etiket`). İmajı push etmeden önce genellikle `docker tag` ile doğru şekilde etiketlemeniz ve `docker login` ile registry'ye giriş yapmanız gerekir.

### İmaj Silme (Removing Images)

Lokal sisteminizden bir veya daha fazla imajı kaldırma.

**Lokal imajları silme:**
```bash
docker rmi [SEÇENEKLER] İMAJ [İMAJ...]
docker image rm # Alternatif komut

# Örnekler:
docker rmi ubuntu:20.04       # Belirli bir imajı etiketiyle siler
docker rmi 4e50cbc1b7c3       # Belirli bir imajı ID'si ile siler
docker rmi my-app:1.0 my-app:latest # Birden fazla imajı siler

# Bir konteyner tarafından kullanılan imajı zorla silme (dikkatli olun!)
docker rmi -f my-app:1.0

# Tüm kullanılmayan (dangling - <none>:<none>) imajları silme
docker image prune

# Sadece dangling değil, hiçbir konteyner tarafından kullanılmayan tüm imajları silme
docker image prune -a

# Tüm imajları silme (çok dikkatli olun!)
# docker rmi $(docker images -q) # Bu komutu dikkatli çalıştırın!
```
**Açıklama:** `docker rmi` veya `docker image rm` komutu, belirtilen imajları (ID veya isim:etiket ile) lokal diskinizden kaldırır. Bir imaj, durdurulmuş veya çalışan bir konteyner tarafından kullanılıyorsa, doğrudan silinemez (önce konteyneri silmeniz gerekir veya `-f` force seçeneğini kullanmanız gerekir, ancak bu genellikle önerilmez). `docker image prune` komutu, özellikle etiketlenmemiş (dangling) veya artık hiçbir konteyner tarafından referans alınmayan imajları temizlemek için kullanışlıdır.

### İmaj Detaylarını İnceleme

Bir imaj hakkında katmanlar, ortam değişkenleri, entrypoint gibi detaylı bilgileri görme.

**İmaj detaylarını inceleme:**
```bash
docker inspect [SEÇENEKLER] İMAJ [İMAJ...]
docker image inspect # Alternatif komut

# Örnek:
docker inspect nginx:latest
docker image inspect ubuntu:20.04

# Sadece belirli bir bilgiyi çekme (örneğin mimari)
docker inspect -f '{{.Architecture}}' nginx:latest
```
**Açıklama:** `docker inspect`, Docker nesneleri (imajlar, konteynerler, ağlar, volume'ler) hakkında JSON formatında çok detaylı bilgi verir. İmajın yapılandırmasını, katmanlarını, ortam değişkenlerini, maruz bırakılan portları, varsayılan komutunu ve daha fazlasını görmek için kullanılır. `-f` veya `--format` seçeneği ile çıktıyı formatlayarak sadece istediğiniz bilgiyi alabilirsiniz.

### İmaj Geçmişini Görme

Bir imajı oluşturan katmanları ve bu katmanların nasıl oluşturulduğunu (Dockerfile komutları) görme.

**İmaj geçmişini görme:**
```bash
docker history [SEÇENEKLER] İMAJ
docker image history # Alternatif komut

# Örnek:
docker history python:3.9-slim
```
**Açıklama:** `docker history` komutu, bir imajın katmanlarını, her katmanın ID'sini, oluşturulma zamanını, boyutunu ve o katmanı oluşturan Dockerfile komutunu (varsa) listeler. Bu, imaj boyutunu anlamak veya belirli bir katmanın nereden geldiğini bulmak için faydalı olabilir.

### İmaj Kaydetme ve Yükleme (Save/Load)

Docker imajlarını bir registry kullanmadan dosya olarak dışa aktarma ve içe aktarma. İnternet bağlantısı olmayan ortamlarda veya yedekleme için kullanılabilir.

**İmajı tar dosyasına kaydetme:**
```bash
docker save [SEÇENEKLER] İMAJ [İMAJ...] -o hedef_dosya.tar
# veya
docker save [SEÇENEKLER] İMAJ [İMAJ...] > hedef_dosya.tar
docker image save # Alternatif komut

# Örnek:
docker save -o my-ubuntu-image.tar ubuntu:latest ubuntu:20.04
docker save my-app:1.0 > my-app.tar
```
**Açıklama (`save`):** `docker save` komutu, bir veya daha fazla imajı (tüm katmanları ve meta verileriyle birlikte) bir `.tar` arşiv dosyasına kaydeder. `-o` seçeneği ile çıktı dosyası belirtilir veya standart çıktıya yönlendirilir.

**Tar dosyasından imaj yükleme:**
```bash
docker load [SEÇENEKLER] -i kaynak_dosya.tar
# veya
docker load [SEÇENEKLER] < kaynak_dosya.tar
docker image load # Alternatif komut

# Örnek:
docker load -i my-ubuntu-image.tar
docker load < my-app.tar
```
**Açıklama (`load`):** `docker load` komutu, `docker save` ile oluşturulmuş bir `.tar` arşivinden imaj(lar)ı yükler. `-i` seçeneği ile girdi dosyası belirtilir veya standart girdiden okunur.

## Konteyner Yönetimi

İmajların çalışan örnekleri olan konteynerleri yönetme.

### Konteyner Çalıştırma (Running Containers)

Bir imajdan yeni bir konteyner oluşturma ve başlatma. En temel ve çok yönlü Docker komutlarından biridir.

**Bir imajdan konteyner çalıştırma:**
```bash
docker run [SEÇENEKLER] İMAJ [KOMUT] [ARG...]
docker container run # Alternatif komut

# --- Sık Kullanılan Seçenekler ---
# -d, --detach: Konteyneri arka planda (detached mode) çalıştırır ve konteyner ID'sini yazdırır.
# -it:        Etkileşimli bir TTY oturumu açar (genellikle kabuk erişimi için kullanılır).
# --name <isim>: Konteynere okunabilir bir isim verir. Verilmezse rastgele bir isim atanır.
# -p <host_port>:<container_port>: Host makinesindeki bir portu konteynerdeki bir porta yönlendirir.
# -v <host_path_veya_volume>:<container_path>[:<options>]: Host dosya sistemini veya bir volume'ü konteynere bağlar.
# --rm:       Konteyner durduğunda otomatik olarak silinir (genellikle kısa süreli görevler için).
# -e <DEĞİŞKEN>=<değer>, --env <DEĞİŞKEN>=<değer>: Ortam değişkeni tanımlar.
# --network <ağ_adı>: Konteyneri belirtilen ağa bağlar.
# --restart <policy>: Konteyner durduğunda yeniden başlatma politikasını belirler (no, on-failure[:max-retries], always, unless-stopped).

# --- Örnekler ---
# Arka planda bir Nginx web sunucusu başlatma ve 8080 portunu yönlendirme:
docker run -d --name my-nginx-server -p 8080:80 nginx

# Etkileşimli bir Ubuntu kabuğu başlatma ve çıkınca silme:
docker run -it --rm ubuntu bash

# Mevcut dizini konteynerdeki /app dizinine bağlayarak bir Python scripti çalıştırma:
# Linux/macOS: docker run -v $(pwd):/app -w /app python:3.9 python my_script.py
# Windows (CMD): docker run -v %cd%:/app -w /app python:3.9 python my_script.py
# Windows (PowerShell): docker run -v ${PWD}:/app -w /app python:3.9 python my_script.py

# Ortam değişkeni ile bir PostgreSQL veritabanı başlatma ve volume bağlama:
docker volume create pgdata # Önce volume oluşturalım
docker run -d --name my-postgres -e POSTGRES_PASSWORD=mysecretpassword -v pgdata:/var/lib/postgresql/data postgres:14

# Belirli bir ağa bağlı bir konteyner çalıştırma:
docker network create my-net
docker run -d --name service1 --network my-net my-app-image

# Her zaman yeniden başlatılacak bir konteyner:
docker run -d --restart always --name important-service my-service-image
```
**Açıklama:** `docker run` komutu aslında iki adımı birleştirir: `docker create` (konteyneri oluşturur) ve `docker start` (oluşturulan konteyneri başlatır). Çok sayıda seçeneği vardır ve Docker ile çalışmanın temelini oluşturur. İmaj adından sonra bir komut ve argümanlar belirtilirse, Dockerfile'daki varsayılan `CMD` veya `ENTRYPOINT` yerine bu komut çalıştırılır.

### Çalışan/Tüm Konteynerleri Listeleme

Mevcut konteynerlerin durumunu görme.

**Konteynerleri listeleme:**
```bash
docker ps [SEÇENEKLER]
docker container ls # Alternatif komut

# Örnekler:
docker ps          # Sadece o an çalışan konteynerleri listeler
docker ps -a       # Çalışan ve durdurulmuş tüm konteynerleri listeler
docker ps -q       # Sadece konteyner ID'lerini listeler (çalışanlar)
docker ps -aq      # Tüm konteyner ID'lerini listeler
docker ps -s       # Boyut bilgilerini de gösterir
docker ps --filter "status=exited" # Sadece çıkış yapmış konteynerleri filtreler
docker ps --filter "name=my-nginx"  # İsme göre filtreler
```
**Açıklama:** `docker ps` komutu, konteyner ID'si, kullanılan imaj, çalışan komut, oluşturulma zamanı, durumu (Up, Exited), port yönlendirmeleri ve konteyner adı gibi bilgileri gösterir. `-a` seçeneği en sık kullanılanlardan biridir, çünkü durmuş olan konteynerleri de görmenizi sağlar. Filtreleme seçenekleri belirli konteynerleri bulmak için çok kullanışlıdır.

### Konteynerleri Başlatma, Durdurma, Yeniden Başlatma

Mevcut konteynerlerin yaşam döngüsünü yönetme.

**Konteyner yaşam döngüsü komutları:**
```bash
# Durdurulmuş bir konteyneri başlatma
docker start [SEÇENEKLER] KONTEYNER [KONTEYNER...]
docker container start # Alternatif

# Çalışan bir konteyneri düzgünce durdurma (SIGTERM, sonra SIGKILL)
docker stop [SEÇENEKLER] KONTEYNER [KONTEYNER...]
docker container stop # Alternatif

# Çalışan bir konteyneri zorla durdurma (SIGKILL)
docker kill [SEÇENEKLER] KONTEYNER [KONTEYNER...]
docker container kill # Alternatif

# Bir konteyneri yeniden başlatma (durdurur ve tekrar başlatır)
docker restart [SEÇENEKLER] KONTEYNER [KONTEYNER...]
docker container restart # Alternatif

# Örnekler:
docker start my-nginx-server my-postgres
docker stop my-nginx-server
docker kill unresponsive-container
docker restart my-app-container

# Çalışan tüm konteynerleri durdurma:
# docker stop $(docker ps -q) # Bu komutu dikkatli çalıştırın!
```
**Açıklama:**

*   `start`: Daha önce `docker create` ile oluşturulmuş veya `docker stop` ile durdurulmuş bir konteyneri başlatır.
*   `stop`: Konteyner içindeki ana sürece önce SIGTERM sinyali göndererek düzgünce kapanması için zaman tanır (varsayılan 10 saniye). Süreç kapanmazsa SIGKILL göndererek zorla sonlandırır.
*   `kill`: Doğrudan SIGKILL sinyali göndererek konteyneri anında sonlandırır. `stop` komutu işe yaramadığında kullanılır.
*   `restart`: Konteyneri önce durdurur (`stop` gibi), sonra tekrar başlatır (`start` gibi).

Bu komutlar konteyner ID'si veya adı ile kullanılabilir. Birden fazla konteyner ID/adı boşluklarla ayrılarak verilebilir.

### Konteyner Silme (Removing Containers)

Artık ihtiyaç duyulmayan (genellikle durdurulmuş) konteynerleri sistemden kaldırma.

**Konteynerleri silme:**
```bash
docker rm [SEÇENEKLER] KONTEYNER [KONTEYNER...]
docker container rm # Alternatif

# Örnekler:
docker rm exited-container-id old-container-name
# Durumu 'exited' olan tüm konteynerleri sil (Linux/macOS):
# docker rm $(docker ps -aq --filter "status=exited")
# Durumu 'exited' olan tüm konteynerleri sil (Windows PowerShell):
# docker ps -aq --filter "status=exited" | ForEach-Object { docker rm $_ }

# Çalışan bir konteyneri zorla silme (önce kill eder) - Dikkat!
docker rm -f running-container

# Tüm durdurulmuş konteynerleri silme
docker container prune
```
**Açıklama:** `docker rm` komutu, belirtilen konteynerleri kaldırır. Varsayılan olarak sadece durdurulmuş konteynerleri silebilirsiniz. Çalışan bir konteyneri silmek için `-f` (force) seçeneğini kullanmanız gerekir, bu komut önce konteynere SIGKILL gönderir. `docker container prune` komutu, durumu "exited" veya "created" olan tüm konteynerleri tek seferde silmek için pratik bir yoldur. `docker run --rm` seçeneği ile başlatılan konteynerler durduklarında otomatik olarak silinir.

### Konteyner Loglarını Görme

Bir konteynerin standart çıktı (stdout) ve standart hata (stderr) akışlarını görme. Sorun gidermede en önemli komutlardan biridir.

**Konteyner loglarını görme:**
```bash
docker logs [SEÇENEKLER] KONTEYNER
docker container logs # Alternatif

# Örnekler:
docker logs my-nginx-server

# Logları gerçek zamanlı takip etme (tail -f gibi)
docker logs -f my-app-container
# Takibi durdurmak için Ctrl+C

# Son 100 satırı gösterme
docker logs --tail 100 my-postgres

# Zaman damgalarını gösterme
docker logs -t my-service
```
**Açıklama:** `docker logs` komutu, bir konteynerin çalışması sırasında ürettiği logları getirir. Bu, uygulamanızın ne yaptığını, hata verip vermediğini anlamak için kritiktir. `-f` (follow) seçeneği ile log akışını canlı olarak izleyebilirsiniz.

### Çalışan Konteyner İçinde Komut Çalıştırma

Halihazırda çalışan bir konteynerin içine girip komutlar çalıştırma veya sadece tek bir komut çalıştırma. Debugging ve inceleme için çok kullanışlıdır.

**Çalışan konteynerde komut çalıştırma:**
```bash
docker exec [SEÇENEKLER] KONTEYNER KOMUT [ARG...]
docker container exec # Alternatif

# --- Sık Kullanılan Seçenekler ---
# -i, --interactive: Komutun STDIN'ini açık tutar (etkileşim için).
# -t, --tty: Sahte bir TTY ayırır (genellikle -i ile birlikte kabuk için kullanılır).
# -d, --detach: Komutu arka planda çalıştırır.
# -w, --workdir <dizin>: Komutun çalıştırılacağı dizini belirtir.
# -u, --user <kullanıcı>: Komutu çalıştıracak kullanıcıyı belirtir.

# --- Örnekler ---
# Çalışan bir konteynerde etkileşimli bir bash kabuğu açma:
docker exec -it my-app-container bash
docker exec -it my-alpine-container sh # Alpine'da genellikle sh olur

# Çalışan bir konteynerde tek bir komut çalıştırma (etkileşimsiz):
docker exec my-nginx-server ls -l /etc/nginx/conf.d
docker exec my-postgres psql -U postgres -c "SELECT version();"

# Arka planda uzun süren bir işlem başlatma:
docker exec -d my-worker-container long_running_task.sh

# Belirli bir dizinde ve kullanıcı ile komut çalıştırma:
docker exec -w /app -u nobody my-web-server python manage.py check
```
**Açıklama:** `docker exec`, çalışan bir konteynerin namespace'i içinde yeni bir süreç başlatmanızı sağlar. `docker run` gibi yeni bir konteyner oluşturmaz, var olanın içine girer. En yaygın kullanımı `-it` seçenekleriyle bir kabuk (`bash`, `sh`) açarak konteynerin içini incelemek, dosyalara bakmak veya diagnostic komutları çalıştırmaktır.

### Konteyner Kaynak Kullanımını İzleme

Çalışan konteynerlerin CPU, RAM, Ağ G/Ç ve Disk G/Ç kullanımlarını canlı olarak görme.

**Konteyner kaynak kullanımını izleme:**
```bash
docker stats [SEÇENEKLER] [KONTEYNER...]
docker container stats # Alternatif

# Örnekler:
docker stats # Tüm çalışan konteynerlerin istatistiklerini gösterir
docker stats my-nginx-server my-postgres # Belirli konteynerleri izler
docker stats --no-stream # Anlık bir görüntü alır, canlı akış yapmaz
```
**Açıklama:** `docker stats` komutu, çalışan konteynerlerin kaynak tüketimini gerçek zamanlı olarak gösteren bir terminal arayüzü sunar. Performans sorunlarını teşhis etmek veya hangi konteynerin ne kadar kaynak kullandığını anlamak için faydalıdır. Çıkmak için Ctrl+C kullanılır.

### Konteyner Detaylarını İnceleme

Bir konteyner hakkında IP adresi, bağlı volume'ler, ağ ayarları gibi çok detaylı bilgileri görme.

**Konteyner detaylarını inceleme:**
```bash
docker inspect [SEÇENEKLER] KONTEYNER [KONTEYNER...]
docker container inspect # Alternatif

# Örnek:
docker inspect my-app-container

# Sadece IP adresini alma (Linux/macOS):
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-app-container
# Sadece IP adresini alma (Windows - daha karmaşık olabilir, jq gibi araçlar önerilir):
# docker inspect my-app-container | ConvertFrom-Json | Select-Object -ExpandProperty NetworkSettings | Select-Object -ExpandProperty Networks | Select-Object -ExpandProperty IPAddress

# Sadece bağlı volume'leri görme (jq ile daha okunaklı):
docker inspect -f '{{json .Mounts}}' my-app-container | jq .
```
**Açıklama:** `docker inspect` (imajlarda olduğu gibi), bir konteynerin tüm yapılandırma detaylarını, çalışma zamanı durumunu, ağ ayarlarını, bağlı volume'leri ve daha fazlasını JSON formatında sunar. Özellikle otomasyon veya belirli yapılandırma detaylarını kontrol etmek için kullanılır. `-f` ile formatlama güçlü bir özelliktir. `jq` gibi bir araç JSON çıktısını işlemek için çok faydalıdır.

### Dosya Kopyalama (Host <-> Konteyner)

Host makinesi ile çalışan veya durdurulmuş bir konteyner arasında dosya veya dizin kopyalama.

**Host ve konteyner arasında dosya kopyalama:**
```bash
# Konteynerden Host'a Kopyalama:
docker cp [SEÇENEKLER] KONTEYNER:KAYNAK_YOL HEDEF_YOL
docker container cp # Alternatif

# Host'tan Konteynere Kopyalama:
docker cp [SEÇENEKLER] KAYNAK_YOL KONTEYNER:HEDEF_YOL

# Örnekler:
# Konteynerdeki log dosyasını host'a alma:
docker cp my-app-container:/app/logs/error.log /tmp/error.log

# Host'taki konfigürasyon dosyasını konteynere gönderme:
docker cp config.prod.json my-web-server:/etc/app/config.json

# Host'taki bir dizini konteynere kopyalama:
docker cp ./my-app-code my-app-container:/usr/src/app
```
**Açıklama:** `docker cp` komutu, `scp` komutuna benzer şekilde çalışır ve host ile konteyner arasında dosya transferi sağlar. Konteyner çalışan veya durdurulmuş olabilir. Yol belirtirken `KONTEYNER_ADI_VEYA_ID:/konteyner/icindeki/yol` formatı kullanılır.

### Diğer Konteyner Komutları

*   `docker attach KONTEYNER`: Çalışan bir konteynerin standart girdi/çıktı/hata akışlarına bağlanır. Genellikle `docker run -it` ile başlatılan ve ana süreci etkileşimli olan konteynerler için kullanılır. Konteyneri durdurmadan ayrılmak için `Ctrl+P Ctrl+Q` kullanılır. `docker exec -it ... bash` genellikle daha esnektir.
*   `docker commit [SEÇENEKLER] KONTEYNER [DEPO[:ETİKET]]`: Bir konteynerin mevcut durumundan (dosya sistemindeki değişiklikler) yeni bir imaj oluşturur. **Genellikle önerilmez**, çünkü tekrarlanabilir değildir. Bunun yerine Dockerfile kullanmak en iyi pratiktir. Debugging veya geçici durumları kaydetmek için nadiren kullanılabilir.
*   `docker diff KONTEYNER`: Konteyner oluşturulduktan sonra dosya sisteminde yapılan değişiklikleri (eklenen, silinen, değiştirilen dosyalar) gösterir.
*   `docker top KONTEYNER`: Konteyner içinde çalışan süreçleri listeler (Linux'taki `top` gibi değil, `ps` gibi anlık liste verir).
*   `docker port KONTEYNER`: Konteynerin port yönlendirmelerini (host portu -> konteyner portu eşleşmeleri) gösterir.
*   `docker pause KONTEYNER`: Çalışan bir konteyner içindeki tüm süreçleri geçici olarak duraklatır (cgroups freezer kullanarak).
*   `docker unpause KONTEYNER`: Duraklatılmış bir konteynerdeki süreçleri devam ettirir.
*   `docker wait KONTEYNER`: Belirtilen konteyner durana kadar bekler ve çıkış kodunu yazdırır. Scripting için kullanışlıdır.
*   `docker export -o dosya.tar KONTEYNER`: Bir konteynerin dosya sistemini bir tar arşivi olarak dışa aktarır (imaj katmanları veya meta veri olmadan).
*   `docker import dosya.tar [DEPO[:ETİKET]]`: `docker export` ile oluşturulan veya başka bir tar dosyasını tek katmanlı bir imaj olarak içe aktarır.

## Docker Volume ve Veri Yönetimi: Verilerinizi Kalıcı Hale Getirmek

### Neden Gerekli?

Konteynerler doğası gereği geçicidir (ephemeral). Bir konteyner silindiğinde, içindeki dosya sisteminde yapılan tüm değişiklikler (yeni dosyalar, değiştirilmiş dosyalar) kaybolur. Veritabanı dosyaları, kullanıcı tarafından yüklenen içerikler, loglar gibi kalıcı olması gereken verileri saklamak için konteyner yaşam döngüsünden bağımsız bir depolama mekanizmasına ihtiyaç vardır. İşte burada Volume'ler ve Bind Mount'lar devreye girer.

### Veri Kalıcılığı Yöntemleri

**1. Volumes (Docker Tarafından Yönetilen - Önerilen Yöntem):**

*   Docker tarafından yönetilen, host dosya sisteminde özel bir alanda (`/var/lib/docker/volumes/` altında Linux'ta) saklanan birimlerdir.
*   Konteynerlerden bağımsız olarak oluşturulabilir, listelenebilir, silinebilirler.
*   Birden fazla konteyner tarafından aynı anda kullanılabilirler (dikkatli olmak gerekir).
*   Yedeklemesi, taşınması ve yönetimi daha kolaydır.
*   Platform bağımsızdır (Windows, macOS, Linux üzerinde benzer şekilde çalışır).
*   Performans genellikle iyidir.
*   Kullanım:
    ```bash
    # İsimli volume kullanımı (volume yoksa otomatik oluşturulur)
    docker run -d --name some-app -v mydata:/app/data my-image

    # Anonim volume kullanımı (volume'e rastgele bir ID atanır, yönetimi zordur)
    docker run -d --name another-app -v /app/config my-image
    ```
*   `--mount` sözdizimi daha açıklayıcıdır ve daha fazla seçenek sunar:
    ```bash
    docker run -d --name some-app --mount source=mydata,target=/app/data my-image
    ```

**2. Bind Mounts (Host Dizini Bağlama):**

*   Host makinesindeki herhangi bir dosya veya dizini doğrudan konteyner içindeki bir yola bağlar.
*   Host'taki değişiklikler anında konteynere, konteynerdeki değişiklikler anında host'a yansır.
*   Geliştirme ortamları için çok kullanışlıdır (kodunuzu host'ta değiştirirsiniz, konteyner anında görür).
*   Host dosya sistemine bağımlıdır, platformlar arası taşınabilirlik sorunları olabilir.
*   Performans, özellikle çok sayıda küçük dosya işlemi varsa, Volume'lere göre daha düşük olabilir (macOS ve Windows'ta).
*   Host'taki dosya izinleri (permissions) ile konteyner içindeki kullanıcı UID/GID uyumsuzlukları sorun yaratabilir (özellikle Linux host'ta).
*   Kullanım:
    ```bash
    # Host'taki mevcut dizini konteynerdeki /app'e bağlama
    # Linux/macOS:
    docker run -d --name dev-app -v "$(pwd):/app" my-dev-image
    # Windows (CMD):
    docker run -d --name dev-app -v "%cd%:/app" my-dev-image
    # Windows (PowerShell):
    docker run -d --name dev-app -v "${PWD}:/app" my-dev-image

    # Belirli bir dosyayı bağlama
    docker run -d --name nginx-with-custom-conf -v /path/to/my/nginx.conf:/etc/nginx/nginx.conf:ro nginx
    # (:ro eki 'read-only' yani salt okunur bağlar)
    ```
*   `--mount` sözdizimi:
    ```bash
    # Linux/macOS:
    docker run -d --name dev-app --mount type=bind,source="$(pwd)",target=/app my-dev-image
    # Windows (CMD):
    docker run -d --name dev-app --mount type=bind,source="%cd%",target=/app my-dev-image
    # Windows (PowerShell):
    docker run -d --name dev-app --mount type=bind,source="${PWD}",target=/app my-dev-image
    ```

**3. tmpfs Mounts (Bellekte Geçici Depolama):**

*   Verileri host'un diskine değil, doğrudan belleğine (RAM) yazar.
*   Çok hızlıdır ancak kalıcı değildir; konteyner durduğunda içindeki tüm veriler kaybolur.
*   Hassas olmayan geçici dosyalar, cache'ler veya state dosyaları için kullanılabilir.
*   Sadece Linux host'larda çalışır.
*   Kullanım:
    ```bash
    docker run -d --name temp-app --mount type=tmpfs,destination=/app/cache my-image
    # veya eski sözdizimi:
    docker run -d --name temp-app --tmpfs /app/cache my-image
    ```

### Volume Komutları

Docker tarafından yönetilen volume'leri yönetmek için kullanılan komutlar:

**Volume yönetimi komutları:**
```bash
# Mevcut volume'leri listeleme
docker volume ls [SEÇENEKLER]

# Yeni bir volume oluşturma (genellikle 'docker run -v' otomatik yapar)
docker volume create [SEÇENEKLER] [VOLUME_ADI]

# Bir volume hakkında detaylı bilgi alma (bağlantı noktası vb.)
docker volume inspect [SEÇENEKLER] VOLUME [VOLUME...]

# Bir veya daha fazla volume'ü silme (konteyner tarafından kullanılmıyorsa)
docker volume rm [SEÇENEKLER] VOLUME [VOLUME...]

# Kullanılmayan tüm lokal volume'leri silme (dikkatli olun! Veri kaybı olabilir!)
docker volume prune [SEÇENEKLER]

# Örnekler:
docker volume ls
docker volume create my-shared-data
docker volume inspect my-shared-data
docker volume rm old-data-volume
docker volume prune -f # Onay sormadan siler (DİKKAT!)
```
**Açıklama:** Bu komutlar, özellikle isimlendirilmiş volume'leri yönetmek için kullanılır. `docker volume prune`, yanlışlıkla önemli verileri silebileceği için çok dikkatli kullanılmalıdır.

## Docker Networking: Konteynerleri Birbirine Bağlamak

### Temel Kavramlar

Varsayılan olarak Docker, konteynerleri kendi izole edilmiş sanal ağlarında çalıştırır. Konteynerlerin birbirleriyle veya host makinesiyle/dış dünya ile iletişim kurabilmesi için Docker'ın ağ yeteneklerini anlamak önemlidir.

### Network Tipleri (Drivers)

Docker farklı ağ oluşturma yöntemleri (sürücüler) sunar:

*   **bridge (Köprü - Varsayılan):**
    *   Docker kurulduğunda otomatik olarak `bridge` adında bir varsayılan köprü ağı oluşturulur. `docker run` ile ağ belirtilmezse konteynerler bu ağa bağlanır.
    *   Varsayılan `bridge` ağındaki konteynerler birbirlerine sadece IP adresleri ile erişebilirler (isimle erişemezler - eski sürümlerde). Modern sürümlerde bazen isimle erişim çalışabilir ancak garanti değildir.
    *   **Kullanıcı Tanımlı Köprü Ağları (User-Defined Bridge Networks):** En çok tavsiye edilen yöntemdir. `docker network create --driver bridge my-net` gibi oluşturulur.
    *   Bu ağlardaki konteynerler, birbirlerine hem IP adresleri hem de **konteyner isimleri** ile (Docker'ın gömülü DNS sunucusu sayesinde) güvenilir bir şekilde erişebilirler.
    *   Daha iyi izolasyon sağlarlar (farklı kullanıcı tanımlı ağlardaki konteynerler birbirini göremez).
*   **host (Ana Makine):**
    *   Konteyner, host makinesinin ağ yığınını (network stack) doğrudan kullanır. Ayrı bir ağ namespace'i oluşturulmaz.
    *   Konteyner içindeki servisler, host'un IP adresindeki portlarda çalışır (örn: konteyner 80 portunu dinliyorsa, host'un 80 portu kullanılır). Port yönlendirmeye (`-p`) gerek kalmaz.
    *   Performans çok iyidir ancak izolasyon azalır (port çakışmaları olabilir). Konteyner, host üzerindeki tüm ağ servislerine (localhost dahil) erişebilir.
    *   Kullanım: `docker run --network host ...` (Linux'ta yaygın, Docker Desktop'ta kısıtlamaları olabilir).
*   **none (Yok):**
    *   Konteynerin ağ arayüzü olmaz (`lo` - loopback hariç). Tamamen izole edilir.
    *   Ağ erişimi gerektirmeyen batch işleri veya özel ağ yapılandırmaları için kullanılabilir.
    *   Kullanım: `docker run --network none ...`
*   **overlay (Katman):**
    *   Birden fazla Docker host'unu (Docker Swarm kümesi gibi) birbirine bağlayan dağıtık ağlar oluşturmak için kullanılır.
    *   Farklı makinelerdeki konteynerlerin sanki aynı ağdaymış gibi iletişim kurmasını sağlar.
    *   Genellikle Docker Swarm ile birlikte kullanılır.
*   **macvlan:**
    *   Konteynerlere host'un fiziksel ağı üzerinde kendi MAC adreslerini atar. Sanki ağa bağlı fiziksel bir cihaz gibi görünürler ve fiziksel ağdan IP alabilirler (örn: DHCP ile).
    *   Özellikle host ağına doğrudan bağlanması gereken legacy uygulamalar veya belirli ağ cihazları (DHCP isteyen vb.) için kullanışlıdır. Host ile konteyner arası iletişim ek yapılandırma gerektirebilir.
*   **ipvlan:** Macvlan'a benzer ancak Layer 3 (IP seviyesi) odaklıdır ve MAC adresi yerine IP adresi bazlı çalışır. Daha fazla esneklik sunabilir.

### Network Komutları

Docker ağlarını yönetmek için kullanılan komutlar:

**Network yönetimi komutları:**
```bash
# Mevcut Docker ağlarını listeleme
docker network ls [SEÇENEKLER]

# Yeni bir ağ oluşturma (varsayılan sürücü 'bridge')
docker network create [SEÇENEKLER] AĞ_ADI
# Örnek: Kullanıcı tanımlı köprü ağı oluşturma
docker network create my-app-network
# Örnek: Farklı sürücü ile overlay ağı oluşturma (Swarm için)
# docker network create --driver overlay my-overlay-net

# Bir ağ hakkında detaylı bilgi alma (bağlı konteynerler vb.)
docker network inspect [SEÇENEKLER] AĞ [AĞ...]

# Çalışan bir konteyneri bir ağa bağlama
docker network connect [SEÇENEKLER] AĞ KONTEYNER

# Çalışan bir konteynerin bir ağ ile bağlantısını kesme
docker network disconnect [SEÇENEKLER] AĞ KONTEYNER

# Bir veya daha fazla ağı silme (konteyner bağlı değilse)
docker network rm [SEÇENEKLER] AĞ [AĞ...]

# Kullanılmayan tüm ağları (genellikle kullanıcı tanımlı olanlar) silme
docker network prune [SEÇENEKLER]

# Örnekler:
docker network ls
docker network create backend-net
docker network inspect backend-net
docker run -d --name api-server --network backend-net my-api-image
docker run -d --name db-server --network backend-net postgres:14
# 'web-server' konteynerini 'frontend-net'e de bağla (varsa):
# docker network connect frontend-net web-server
# 'old-service' konteynerini 'backend-net'ten çıkar:
# docker network disconnect backend-net old-service
docker network rm unused-test-net
docker network prune -f
```
**Açıklama:** Bu komutlar Docker ağlarınızı oluşturmanıza, incelemenize ve yönetmenize olanak tanır. Özellikle çoklu konteyner uygulamalarında konteynerlerin birbirleriyle güvenli ve kolay bir şekilde iletişim kurabilmesi için kullanıcı tanımlı köprü ağları (`docker network create ...`) oluşturmak ve konteynerleri `docker run --network ...` veya `docker network connect ...` ile bu ağlara bağlamak önemlidir.

### Konteynerler Arası İletişim

En iyi pratik, ilişkili konteynerleri aynı **kullanıcı tanımlı köprü ağına** bağlamaktır.

Örnek: Bir web uygulaması (konteyner adı: `webapp`) ve bir veritabanı (konteyner adı: `db`)
```bash
# 1. Ağı oluştur
docker network create app-net

# 2. Veritabanı konteynerini ağa bağla
# (Gerçek kullanımda şifreler ve kullanıcı adı için -e veya secrets kullanılır)
docker run -d --name db --network app-net postgres:14

# 3. Web uygulaması konteynerini ağa bağla ve DB'ye ismiyle eriş
# Uygulama kodunuzda veritabanı host'u olarak 'db' kullanabilirsiniz.
docker run -d --name webapp --network app-net -p 8000:80 -e DATABASE_HOST=db my-webapp-image
```
Bu senaryoda, `webapp` konteyneri, `db` konteynerine ağ içinde doğrudan `db` ismiyle (örneğin `ping db` veya veritabanı bağlantı string'inde `host=db`) erişebilir. Docker'ın gömülü DNS'i bu isim çözümlemesini yapar.

### Port Yönlendirme (Port Mapping)

Konteyner içinde çalışan bir servise host makinesi veya dış ağ üzerinden erişilmesini sağlamak için kullanılır.

```bash
docker run -p [HOST_IP:][HOST_PORT:]CONTAINER_PORT[/PROTOKOL] ... İMAJ

# --- Örnekler ---
# Host'un 8080 portunu konteynerin 80 portuna yönlendir (TCP varsayılan)
docker run -d -p 8080:80 nginx

# Host'un SADECE localhost (127.0.0.1) arayüzündeki 8080 portunu konteynerin 80'ine yönlendir
docker run -d -p 127.0.0.1:8080:80 nginx

# Host'ta rastgele boş bir portu konteynerin 80'ine yönlendir (hangi port olduğunu 'docker port' ile öğren)
docker run -d -p 80 nginx
# Hangi porta atandığını gör: docker port <container_id_or_name> 80

# UDP portu yönlendirme (örneğin DNS için 53)
docker run -d -p 53:53/udp my-dns-server

# Hem TCP hem UDP için aynı portu yönlendirme
docker run -d -p 5000:5000/tcp -p 5000:5000/udp my-service

# Port aralığı yönlendirme (Docker Engine v20.10+ gerekir)
# docker run -d -p 6000-6010:7000-7010 my-service
```
**Açıklama:** `-p` seçeneği, `HOST:KONTEYNER` formatında çalışır. Host portu belirtilmezse rastgele boş bir port atanır. Host IP adresi belirtilmezse, host'un tüm ağ arayüzlerindeki o port kullanılır (0.0.0.0). Protokol belirtilmezse TCP varsayılır.

# Dockerfile: İmajları İnşa Etmek

## Dockerfile Nedir?

Dockerfile, bir Docker imajının nasıl oluşturulacağını adım adım tanımlayan, metin tabanlı bir talimat (instruction) dosyasıdır. İmaj oluşturma sürecini otomatikleştirir, tekrarlanabilir hale getirir ve versiyon kontrol sistemlerinde (Git gibi) takip edilmesini sağlar. Genellikle projenin kök dizininde `Dockerfile` (büyük/küçük harf duyarlı olabilir, genellikle büyük 'D' ile başlar) adıyla bulunur.

## Temel Dockerfile Direktifleri

En sık kullanılan Dockerfile komutları:

*   **`FROM <image>[:<tag>] [AS <name>]`**:
    Temel alınacak imajı belirtir. Her Dockerfile `FROM` ile başlamalıdır (multi-stage hariç ilk aşama). `AS <name>` ile çok aşamalı build'lerde (multi-stage builds) bu aşamaya bir isim verilebilir.
    *Örnek:* `FROM ubuntu:22.04`, `FROM python:3.9-slim AS builder`

*   **`RUN <command>`**:
    İmaj oluşturulurken kabuk içinde çalıştırılacak komutları tanımlar. Genellikle paket yükleme, bağımlılık kurma, derleme gibi işlemler için kullanılır. Her `RUN` komutu yeni bir imaj katmanı oluşturur. Katman sayısını azaltmak için komutları `&&` ile birleştirmek yaygındır.
    *Örnek (shell form):* `RUN apt-get update && apt-get install -y --no-install-recommends curl && rm -rf /var/lib/apt/lists/*`
    *Örnek (exec form):* `RUN ["apt-get", "update"]` (Bu formda shell özellikleri çalışmaz, örn: değişkenler, pipe)

*   **`COPY [--chown=<user>:<group>] <src>... <dest>`**:
    Dosya veya dizinleri build bağlamından (context) imajın dosya sistemine kopyalar. Kaynak (`src`) host üzerindeki build bağlamına göreceli yoldur, hedef (`dest`) imaj içindeki mutlak veya `WORKDIR`'e göreceli yoldur. `--chown` ile kopyalanan dosyaların sahibini/grubunu ayarlayabilirsiniz (sayısal UID/GID veya isim).
    *Örnek:* `COPY . /app`, `COPY --chown=appuser:appgroup requirements.txt /tmp/`

*   **`ADD [--chown=<user>:<group>] <src>... <dest>`**:
    `COPY`'ye benzer, ancak ek olarak URL'lerden dosya indirebilir ve yerel `.tar` (`.tar.gz`, `.tar.bz2`, `.tar.xz`) arşivlerini otomatik olarak hedef dizine açabilir. Bu otomatik açma ve URL indirme özellikleri beklenmedik davranışlara yol açabileceğinden, genellikle **`COPY` tercih edilir**. `ADD` sadece URL'den indirme veya otomatik tar açma gerektiğinde kullanılmalıdır.
    *Örnek:* `ADD https://example.com/file.zip /tmp/`, `ADD rootfs.tar.gz /`

*   **`WORKDIR /path/to/workdir`**:
    Sonraki `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, `ADD` komutlarının çalışacağı varsayılan dizini ayarlar. Dizin yoksa oluşturulur. Mutlak veya göreceli yol alabilir. Belirtilmezse kök dizin (`/`) varsayılır.
    *Örnek:* `WORKDIR /app`

*   **`EXPOSE <port> [<port>/<protocol>...]`**:
    Konteynerin çalışma zamanında hangi ağ portlarını dinleyeceğini belirtir (dokümantasyon amaçlıdır ve bazı araçlar tarafından kullanılır). Bu komut portları otomatik olarak host'a **yönlendirmez**; bunun için `docker run -p` veya Docker Compose'daki `ports` kullanılır. Protokol belirtilmezse TCP varsayılır.
    *Örnek:* `EXPOSE 80`, `EXPOSE 8080/tcp 53/udp`

*   **`CMD ["executable","param1","param2"]`** (exec form - tercih edilen) \\
    **`CMD command param1 param2`** (shell form) \\
    **`CMD ["param1","param2"]`** (`ENTRYPOINT` için varsayılan parametreler olarak)
    Konteyner başlatıldığında varsayılan olarak çalıştırılacak komutu veya `ENTRYPOINT` için varsayılan argümanları belirler. Bir Dockerfile'da sadece bir tane `CMD` etkili olur (en sonuncusu). `docker run` komutunda imaj adından sonra bir komut belirtilirse, `CMD` tamamen ezilir. Exec formu shell işlemesi yapmaz, shell formu `/bin/sh -c` (veya `SHELL` ile belirtilen) içinde çalışır.
    *Örnek (exec):* `CMD ["python", "app.py"]`
    *Örnek (shell):* `CMD echo "Hello World"`
    *Örnek (ENTRYPOINT parametresi):* (ENTRYPOINT ["/usr/bin/git"] ile birlikte) `CMD ["--help"]`

*   **`ENTRYPOINT ["executable", "param1", "param2"]`** (exec form - tercih edilen) \\
    **`ENTRYPOINT command param1 param2`** (shell form)
    Konteyneri çalıştırılabilir bir uygulama gibi yapılandırır. `docker run` ile imaj adından sonra verilen argümanlar `ENTRYPOINT`'e parametre olarak **eklenir** (varsayılan `CMD`'yi parametre olarak alır veya run argümanlarını alır). `CMD` genellikle `ENTRYPOINT` için varsayılan parametreleri sağlamak amacıyla kullanılır. Bir Dockerfile'da sadece bir `ENTRYPOINT` etkili olur (en sonuncusu). `docker run --entrypoint` ile ezilebilir.
    *Örnek:* `ENTRYPOINT ["java", "-jar", "app.jar"]` (`docker run my-image arg1` çalıştırıldığında `java -jar app.jar arg1` çalışır)
    *Örnek (shell):* `ENTRYPOINT /entrypoint.sh` (run argümanları script'e `$@` olarak geçer)

*   **`ENV <key>=<value> ...`**:
    Ortam değişkenlerini ayarlar. Bu değişkenler hem imaj build işlemi sırasında (`RUN` komutlarında `$key` veya `${key}` olarak) hem de konteyner çalışma zamanında kullanılabilir. `docker run -e` ile ezilebilir.
    *Örnek:* `ENV APP_VERSION=1.0 DEBUG=false`, `ENV PATH="/usr/local/bin:${PATH}"`

*   **`ARG <name>[=<default_value>]`**:
    Sadece imaj **build** işlemi sırasında kullanılabilecek değişkenleri tanımlar (`docker build --build-arg <name>=<value>`). `FROM` direktifinden önce tanımlanan `ARG`'lar `FROM` içinde kullanılabilir (ancak build aşaması bittikten sonra geçerli olmaz). `RUN` komutları içinde kullanılabilirler ancak `ENV` gibi çalışma zamanında **geçerli olmazlar** (eğer aynı isimde bir `ENV` de tanımlanmazsa).
    *Örnek:* `ARG USER=guest`, `ARG VERSION=latest`
    *Örnek Kullanım:* `ARG NODE_VERSION=18` `FROM node:${NODE_VERSION}-alpine`

*   **`VOLUME ["/path/to/volume"]`**:
    Belirtilen yolda bir mount point (bağlantı noktası) oluşturur ve bu yolu harici bir volume veya host dizini ile bağlamak üzere işaretler. Eğer konteyner çalıştırılırken bu yola bir volume veya bind mount bağlanmazsa, Docker otomatik olarak bir *anonim volume* oluşturur ve buraya bağlar. Bu dizindeki veriler, volume silinmediği sürece kalıcı olur. Genellikle veritabanı dosyaları, loglar, konfigürasyon gibi kalıcı olması gereken verilerin konulduğu dizinler için kullanılır.
    *Örnek:* `VOLUME /var/lib/mysql`, `VOLUME ["/data", "/config"]`

*   **`USER <user>[:<group>]`** veya **`USER <UID>[:<GID>]`**:
    Sonraki `RUN`, `CMD`, `ENTRYPOINT` komutlarının hangi kullanıcı (ve isteğe bağlı grup) ile çalıştırılacağını belirtir. Güvenlik için genellikle `root` yerine özel bir kullanıcı oluşturup (`RUN groupadd ... && useradd ...`) bu komutla ona geçmek **şiddetle önerilir**. Kullanıcı adı veya UID/GID olarak belirtilebilir.
    *Örnek:* `USER nobody`, `USER appuser:appgroup`, `USER 1001:1001`

*   **`LABEL <key>=<value> <key>=<value> ...`**:
    İmaj hakkında meta veriler (etiketler) ekler. Örneğin, sürüm, açıklama, sahip, VCS referansı gibi bilgiler. Otomasyon ve yönetim için kullanışlıdır.
    *Örnek:* `LABEL version="1.0" description="My web application" maintainer="Cihan Atas <atascihan115@gmail.com>"`

*   **`STOPSIGNAL signal`**:
    Konteynerin durdurulması için gönderilecek varsayılan sistem sinyalini ayarlar (`docker stop` için). Varsayılan `SIGTERM`'dir. Uygulamanız farklı bir sinyalle daha düzgün kapanıyorsa bunu değiştirebilirsiniz.
    *Örnek:* `STOPSIGNAL SIGQUIT`

*   **`HEALTHCHECK [OPTIONS] CMD <command>`** veya **`HEALTHCHECK NONE`**:
    Konteynerin sağlıklı çalışıp çalışmadığını kontrol etmek için periyodik olarak çalıştırılacak bir komut tanımlar. Komutun çıkış kodu sağlığı belirler (0: healthy, 1: unhealthy). Seçeneklerle (`--interval=...`, `--timeout=...`, `--start-period=...`, `--retries=...`) kontrolün sıklığı, zaman aşımı, başlangıç periyodu ve deneme sayısı ayarlanabilir. Docker Swarm veya Kubernetes gibi orkestrasyon araçları bu durumu kullanarak sağlıksız konteynerleri yeniden başlatabilir. `NONE` ile devredışı bırakılır (varsayılan).
    *Örnek:* `HEALTHCHECK --interval=5m --timeout=3s CMD curl -f http://localhost:80 || exit 1`

*   **`SHELL ["executable", "parameters"]`**:
    `RUN`, `CMD`, `ENTRYPOINT`'in shell formlarının çalıştırılacağı varsayılan kabuğu değiştirir. Linux'ta varsayılan `["/bin/sh", "-c"]`, Windows'ta `["cmd", "/S", "/C"]`. Örneğin bash özelliklerini kullanmak için değiştirilebilir.
    *Örnek:* `SHELL ["/bin/bash", "-c"]`

## Örnek Dockerfile Yapıları

### Basit Node.js Uygulaması

**Node.js Uygulaması için Örnek Dockerfile:**
```dockerfile
# 1. Temel Node.js imajını seç (Alpine sürümü daha küçüktür)
FROM node:18-alpine

# 2. Uygulama için çalışma dizini oluştur ve ayarla
WORKDIR /usr/src/app

# 3. Bağımlılıkları kurma adımı (önce sadece package*.json kopyala - cache optimizasyonu)
# Bu dosyalar değişmediği sürece RUN npm install katmanı cache'den kullanılır.
COPY package*.json ./
# Geliştirme için: RUN npm install
# Üretim ortamı için npm ci daha hızlı ve güvenilirdir:
RUN npm ci --only=production

# 4. Uygulama kodunu çalışma dizinine kopyala
# .dockerignore dosyasında belirtilenler hariç her şeyi kopyala
COPY . .

# 5. Uygulamanın dinleyeceği portu belirt (dokümantasyon)
EXPOSE 3000

# 6. Güvenlik için root olmayan bir kullanıcıya geç (ÖNERİLİR)
# Alpine'da addgroup/adduser kullanımı:
# RUN addgroup -S appgroup && adduser -S appuser -G appgroup
# İmajda hazır 'node' kullanıcısı olabilir, onu kullanalım:
USER node

# 7. Konteyner başlatıldığında uygulamayı çalıştıracak komut
CMD ["node", "server.js"]
```

### Basit Python/Flask Uygulaması

**Python/Flask Uygulaması için Örnek Dockerfile:**
```dockerfile
# 1. Temel Python imajını seç (slim sürümü daha küçüktür)
FROM python:3.9-slim

# 2. Sistem bağımlılıklarını kur (gerekirse, örn: veritabanı istemcisi)
# Örnek: PostgreSQL client
# RUN apt-get update && apt-get install -y --no-install-recommends postgresql-client && rm -rf /var/lib/apt/lists/*

# 3. Çalışma dizinini ayarla
WORKDIR /app

# 4. Bağımlılıkları kur (önce requirements.txt kopyala - cache optimizasyonu)
COPY requirements.txt ./
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt
# --no-cache-dir imaj boyutunu küçültmeye yardımcı olur

# 5. Uygulama kodunu kopyala
COPY . .

# 6. Ortam değişkenlerini ayarla (Flask için örnek)
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0 # Konteyner dışından erişim için
# Üretim için DEBUG=0 olmalı
ENV FLASK_DEBUG=0

# 7. Uygulamanın dinleyeceği portu belirt
EXPOSE 5000

# 8. Güvenlik için root olmayan kullanıcı (ÖNERİLİR)
# Örnek kullanıcı oluşturma (Debian/Ubuntu tabanlı imajlar için):
# RUN useradd --create-home appuser
# USER appuser
# Veya daha basit:
USER nobody

# 9. Uygulamayı başlatacak komut (Üretim için Gunicorn/uWSGI önerilir)
# Geliştirme: CMD ["flask", "run"]
# Üretim (Gunicorn örneği):
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```

### Multi-stage Build Örneği (Basit Go Uygulaması)

Multi-stage build'ler, derleme bağımlılıklarını ve araçlarını son imaja dahil etmeden, sadece derlenmiş artefaktı (çalıştırılabilir dosya vb.) içeren küçük ve güvenli bir final imajı oluşturmayı sağlar.

**Go Uygulaması için Multi-stage Build Örneği:**
```dockerfile
# --- Aşama 1: Build Aşaması ---
# Go derleyicisini içeren tam Go imajını kullanıyoruz
FROM golang:1.20-alpine AS builder
LABEL stage=builder

# Çalışma dizinini ayarla
WORKDIR /app

# Önce modül dosyalarını kopyala ve bağımlılıkları indir (cache optimizasyonu)
COPY go.mod ./
COPY go.sum ./
RUN go mod download

# Tüm kaynak kodu kopyala
COPY . .

# Uygulamayı derle (statik olarak linkle, linux için cross-compile)
# CGO_ENABLED=0 statik linkleme için, GOOS=linux hedef işletim sistemi
# -ldflags="-w -s" debug bilgilerini ve sembol tablosunu kaldırarak boyutu küçültür
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-w -s" -o /goapp .

# --- Aşama 2: Final Aşaması ---
# Çok küçük bir temel imaj kullanıyoruz (Alpine veya Distroless)
# FROM alpine:latest
# Veya daha da küçük ve güvenli (sadece uygulamanız ve bağımlılıkları, shell yok):
FROM gcr.io/distroless/static-debian11 AS final
# FROM scratch AS final # Eğer uygulama tamamen statikse (libc dahil)

WORKDIR /

# Sadece derlenmiş uygulamayı 'builder' aşamasından kopyala
COPY --from=builder /goapp /goapp

# (Opsiyonel) Gerekli diğer dosyaları kopyala (config, templates, statik dosyalar vb.)
# COPY --from=builder /app/configs /configs
# COPY --from=builder /app/web/static /static

# Uygulamanın dinleyeceği port
EXPOSE 8080

# Güvenlik için root olmayan kullanıcı (Distroless'te genellikle 'nonroot' (65532) vardır)
# Alpine için: RUN addgroup -S appgroup && adduser -S appuser -G appgroup
# USER appuser
# Distroless için:
USER nonroot:nonroot

# Konteyner başladığında uygulamayı çalıştır
ENTRYPOINT ["/goapp"]
# CMD ["--config", "/configs/config.yaml"] # ENTRYPOINT için varsayılan argümanlar
```
Bu yapı sayesinde, son imaj sadece Alpine (veya Distroless/scratch) temel sistemini ve derlenmiş Go uygulamasını içerir, Go derleyicisini veya kaynak kodunu içermez. Bu da imaj boyutunu ve potansiyel güvenlik açıklarını önemli ölçüde azaltır.

## .dockerignore Dosyası

`Dockerfile` ile aynı dizinde bulunan `.dockerignore` dosyası, `COPY` veya `ADD` komutları çalıştırıldığında Docker build bağlamına (context) hangi dosya ve dizinlerin **dahil edilmeyeceğini** belirtir. Bu, gereksiz dosyaların (örneğin `.git` dizini, log dosyaları, lokal bağımlılıklar (`node_modules` gibi imajda kurulacaklar), IDE ayar dosyaları) build bağlamına gönderilmesini engelleyerek build hızını artırır, imaj boyutunu küçültebilir ve hassas bilgilerin sızmasını önleyebilir. Sözdizimi `.gitignore` dosyasına çok benzer.

Örnek `.dockerignore` içeriği:
```
# Git dosyaları
.git
.gitignore

# Node.js bağımlılıkları (imaj içinde kurulacak)
node_modules
npm-debug.log*
yarn-error.log

# Python cache ve sanal ortam
__pycache__
*.pyc
*.pyo
*.pyd
.venv
venv
env

# IDE ve Editör dosyaları
.vscode
.idea
*.suo
*.user
*.sln.docstates
*.sublime-project
*.sublime-workspace

# İşletim sistemi dosyaları
.DS_Store
Thumbs.db

# Build çıktıları (imaj içinde oluşacaksa)
dist
build
target
out

# Diğerleri
Dockerfile
.dockerignore
README.md
*.md # Projeye göre karar verilir, bazen imaja eklenmek istenebilir
*.log
logs/
.env* # Hassas ortam değişkenleri ASLA imaja girmemeli
secrets/
tmp/

# Test dosyaları (eğer testler imajda çalıştırılmayacaksa)
tests/
*.test.js
*.spec.js
```
Bu dosya, build bağlamını temiz tutmak ve hassas bilgilerin yanlışlıkla imaja kopyalanmasını önlemek için çok önemlidir.

# Docker Compose: Çoklu Konteyner Uygulamalarını Yönetmek

## Neden Docker Compose?

Modern uygulamalar genellikle tek bir servisten oluşmaz. Örneğin, bir web uygulaması bir web sunucusu (Nginx), bir uygulama sunucusu (Python/Node.js/Java), bir veritabanı (PostgreSQL/MySQL), bir önbellek (Redis) ve belki bir mesaj kuyruğu (RabbitMQ) gibi birden fazla bileşene ihtiyaç duyabilir. Bu bileşenlerin her birini ayrı ayrı `docker run` komutlarıyla yönetmek (ağları, volume'leri, portları, bağımlılıkları, ortam değişkenlerini, yeniden başlatma politikalarını ayarlamak) karmaşık, zaman alıcı ve hataya açık olabilir.

**Docker Compose**, bu tür çoklu konteynerli uygulamaları tek bir YAML dosyası (`docker-compose.yml` varsayılan isimdir) ile tanımlamanızı, yapılandırmanızı ve yönetmenizi sağlayan bir araçtır. Bu dosya ile:

*   Uygulamanızı oluşturan servisleri (konteynerleri) tanımlayabilirsiniz.
*   Her servis için kullanılacak imajı, build bağlamını, port yönlendirmelerini, volume'leri, ağları, ortam değişkenlerini, bağımlılıkları, sağlık kontrollerini, yeniden başlatma politikalarını ve diğer birçok ayarı belirtebilirsiniz.
*   Tek bir komutla (`docker compose up` veya eski `docker-compose up`) tüm uygulama yığınını (stack) oluşturup başlatabilirsiniz.
*   Tek bir komutla (`docker compose down` veya eski `docker-compose down`) tüm yığını durdurup ilişkili kaynakları (konteynerler, ağlar, isteğe bağlı olarak volume'ler) kaldırabilirsiniz.
*   Servisleri kolayca ölçekleyebilirsiniz (`docker compose up --scale ...`).
*   Geliştirme ve test ortamlarını hızla kurup yıkabilirsiniz.

Docker Compose, özellikle geliştirme, test ve basit üretim veya staging ortamları için konteyner yönetimini büyük ölçüde basitleştirir.

## Temel Komutlar

Docker Compose ile çalışmak için kullanılan temel komutlar (Modern Docker sürümlerinde `docker-compose` yerine `docker compose` (CLI Plugin) kullanılır ve bu tavsiye edilir):

*   **`docker compose up [OPTIONS] [SERVICE...]`**:
    YAML dosyasındaki servisleri oluşturur (gerekirse imajları build eder), gerekli ağları ve volume'leri oluşturur ve konteynerleri başlatır. Varsayılan olarak logları terminale basar (foreground).
    *   `-d` veya `--detach`: Servisleri arka planda (detached mode) başlatır.
    *   `--build`: Başlatmadan önce imajları (yeniden) build etmeye zorlar.
    *   `--force-recreate`: Konteynerleri durdurup yeniden oluşturur (yapılandırma değişmişse veya temiz bir başlangıç isteniyorsa faydalı).
    *   `--no-deps`: Bağımlı servisleri başlatmaz.
    *   `--scale <SERVICE>=<NUM>`: Belirli bir servisten belirtilen sayıda kopya (konteyner) başlatır (eski `docker-compose scale` komutunun yerini alır).
    *Örnek:* `docker compose up -d`, `docker compose up --build web`, `docker compose up -d --scale worker=3`

*   **`docker compose down [OPTIONS]`**:
    `docker compose up` ile oluşturulan konteynerleri durdurur ve kaldırır. Varsayılan olarak servislerle ilişkilendirilmiş ağları da kaldırır.
    *   `--volumes`, `-v`: Konteynerlerle birlikte YAML dosyasında tanımlanan *isimlendirilmiş* (ve bazı durumlarda anonim) volume'leri de kaldırır (**Dikkat: Veri kaybına neden olabilir!**).
    *   `--rmi <'all'|'local'>`: İmajları kaldırır ('all': tüm servis imajları, 'local': sadece özel etiket olmayan (`image:` yerine `build:` kullanılan) imajlar).
    *   `--remove-orphans`: Compose dosyasında artık tanımlı olmayan ancak bu projeye ait olan konteynerleri kaldırır.
    *Örnek:* `docker compose down`, `docker compose down -v --rmi local`

*   **`docker compose ps [OPTIONS] [SERVICE...]`**:
    Compose projesi tarafından yönetilen konteynerlerin durumunu listeler (`docker ps`'e benzer ama sadece bu projeye ait olanları gösterir).
    *Örnek:* `docker compose ps`

*   **`docker compose logs [OPTIONS] [SERVICE...]`**:
    Servislerin loglarını gösterir.
    *   `-f` veya `--follow`: Logları canlı olarak takip eder.
    *   `--tail="N"`: Son N satırı gösterir. `--tail=0 -f` ile sadece yeni logları takip eder.
    *   `-t`, `--timestamps`: Zaman damgalarını gösterir.
    *Örnek:* `docker compose logs -f web api`, `docker compose logs --tail=50 db`

*   **`docker compose build [OPTIONS] [SERVICE...]`**:
    YAML dosyasında `build` direktifi ile tanımlanmış servisler için imajları (yeniden) oluşturur.
    *   `--no-cache`: Build sırasında cache kullanmaz.
    *   `--pull`: Build öncesi temel imajları güncellemeyi dener.
    *Örnek:* `docker compose build --no-cache worker`

*   **`docker compose pull [OPTIONS] [SERVICE...]`**:
    YAML dosyasında `image` direktifi ile tanımlanmış servisler için gerekli imajları registry'den çeker veya günceller.
    *Örnek:* `docker compose pull db cache`

*   **`docker compose start [SERVICE...]`**:
    Daha önce `up` ile oluşturulmuş ve `stop` ile durdurulmuş servis konteynerlerini başlatır.
    *Örnek:* `docker compose start web db`

*   **`docker compose stop [OPTIONS] [SERVICE...]`**:
    Çalışan servis konteynerlerini kaldırmadan durdurur.
    *   `-t`, `--timeout <seconds>`: Durdurma için beklenecek süre (varsayılan 10).
    *Örnek:* `docker compose stop -t 30 worker`

*   **`docker compose restart [OPTIONS] [SERVICE...]`**:
    Servis konteynerlerini yeniden başlatır (durdurur ve başlatır).
    *Örnek:* `docker compose restart api`

*   **`docker compose rm [OPTIONS] [SERVICE...]`**:
    Durdurulmuş servis konteynerlerini kaldırır.
    *   `-f`, `--force`: Onay sormaz.
    *   `-s`, `--stop`: Kaldırmadan önce çalışan konteynerleri durdurur.
    *   `-v`: Konteynerlere bağlı anonim volume'leri de kaldırır.
    *Örnek:* `docker compose rm -fsv`

*   **`docker compose exec [OPTIONS] SERVICE COMMAND [ARGS...]`**:
    Çalışan bir servis konteynerinin içinde bir komut çalıştırır (`docker exec`'e benzer).
    *   `-d`, `--detach`: Komutu arka planda çalıştırır.
    *   `-e KEY=VALUE`: Ortam değişkeni tanımlar.
    *   `-u USER`: Kullanıcıyı belirtir.
    *   `-T`: TTY ayırmaz (scripting için).
    *   `--index=N`: Aynı servisin N'inci kopyasında çalıştırır (scale > 1 ise).
    *Örnek:* `docker compose exec web bash`, `docker compose exec -T db psql -U user -d dbname -c "SELECT COUNT(*) FROM users;"`

*   **`docker compose config [OPTIONS]`**:
    Compose dosyasını (varsa `.env` dosyası ile birleştirilmiş, doğrulanmış ve enterpolasyon yapılmış) terminale yazdırır. Hataları veya son yapılandırmayı kontrol etmek için kullanışlıdır.
    *   `--services`: Sadece servis isimlerini listeler.
    *   `--volumes`: Sadece volume isimlerini listeler.
    *   `--networks`: Sadece ağ isimlerini listeler.
    *Örnek:* `docker compose config`

*   **`docker compose version`**:
    Docker Compose CLI Plugin sürümünü gösterir.
    *Örnek:* `docker compose version`

*   **`docker compose run [OPTIONS] SERVICE [COMMAND] [ARGS...]`**:
    Belirli bir servis için tek seferlik bir komut çalıştırır (yeni bir konteyner başlatır). Servis tanımındaki port yönlendirmeleri varsayılan olarak **yapılmaz**. Bağlantılar (`depends_on`) oluşturulur. Genellikle veritabanı migration'ları, testler, yönetimsel görevler gibi tek seferlik işler için kullanılır.
    *   `--rm`: Komut bittikten sonra konteyneri otomatik olarak kaldırır (çok yaygın kullanılır).
    *   `-p HOST:CONTAINER`: Port yönlendirmesi yapar.
    *   `--service-ports`: Servis tanımındaki portları da açar.
    *   `-e KEY=VALUE`: Ortam değişkeni tanımlar.
    *   `-v HOST:CONTAINER`: Volume bağlar.
    *Örnek:* `docker compose run --rm web python manage.py migrate`

## `docker-compose.yml` Dosyası Yapısı

Compose dosyası YAML formatında yazılır ve temel olarak şu ana bölümleri içerir (Sürüm 3+ için):

*   **`version`**: (Artık Opsiyonel ama tavsiye edilir) Kullanılan Compose dosya formatı sürümünü belirtir. Genellikle `'3.8'` veya benzeri modern bir sürüm kullanılır. Farklı sürümler farklı özellikler destekler. Belirtilmezse en son desteklenen sürüm varsayılır.
*   **`services`**: Uygulamanızı oluşturan servislerin (konteynerlerin) tanımlandığı ana bölümdür. Her servis bir anahtar (key) ile temsil edilir (örn: `web`, `db`, `api`).
    *   **`image: <image_name>[:<tag>]`**: Servis için kullanılacak Docker imajını belirtir.
    *   **`build: <context_path>`** veya **`build: { context: <path>, dockerfile: <filename>, args: {...}, target: <stage_name> }`**: İmajı registry'den çekmek yerine lokaldeki Dockerfile'dan build etmek için kullanılır. `context` build bağlamının yolunu belirtir. `dockerfile` alternatif bir Dockerfile adı belirtir. `args` build argümanlarını iletir. `target` multi-stage build'de hedeflenen aşamayı belirtir.
    *   **`ports: ["<HOST_PORT>:<CONTAINER_PORT>", ...]`**: Port yönlendirmelerini tanımlar. Sadece `"<CONTAINER_PORT>"` belirtilirse host'ta rastgele bir port atanır.
    *   **`volumes: ["<HOST_PATH | VOLUME_NAME>:<CONTAINER_PATH>[:ro]", ...]`** veya daha detaylı syntax:
        ```yaml
        volumes:
          - type: volume # veya bind, tmpfs
            source: mydata # Volume adı veya host yolu
            target: /data
            read_only: true # Opsiyonel
            volume: # Volume'a özel seçenekler
              nocopy: true
            bind: # Bind mount'a özel seçenekler
              propagation: shared
            tmpfs: # tmpfs'e özel seçenekler
              size: 100m
        ```
    *   **`networks: [<network_name1>, <network_name2>, ...]`** veya daha detaylı:
        ```yaml
        networks:
          app_net: # Bu ağa bağlanır
            ipv4_address: 172.16.238.10 # Bu ağda statik IP (dikkatli kullanılmalı)
          other_net:
            aliases: # Bu ağda ek isimler
              - service-alias
        ```
    *   **`environment: { <KEY>: <VALUE>, ... }`** veya **`environment: ["<KEY>=<VALUE>", ...]`**: Ortam değişkenlerini tanımlar. Değer atanmazsa (`environment: [VAR1, VAR2=]`) host ortamından alınır.
    *   **`env_file: <filename>`** veya **`env_file: [<filename1>, <filename2>, ...]`**: Ortam değişkenlerini bir veya daha fazla dosyadan okur (dosya formatı `KEY=VALUE`).
    *   **`depends_on: [<service_name1>, <service_name2>, ...]`** veya daha detaylı (sağlık kontrolü bekleme):
        ```yaml
        depends_on:
          db:
            condition: service_healthy # Sadece db servisi healthy olunca başlar
          redis:
            condition: service_started # Sadece redis servisi başlayınca başlar (varsayılan)
        ```
    *   **`command: <command>`** veya **`command: ["executable", "arg1", ...]`**: Dockerfile'daki `CMD`'yi ezer.
    *   **`entrypoint: <command>`** veya **`entrypoint: ["executable", "arg1", ...]`**: Dockerfile'daki `ENTRYPOINT`'i ezer.
    *   **`restart: <policy>`**: Yeniden başlatma politikasını belirler (`no`, `always`, `on-failure[:max_attempts]`, `unless-stopped`).
    *   **`healthcheck: { test: ["CMD", "curl", "-f", "http://localhost:80"], interval: 1m30s, timeout: 10s, retries: 3, start_period: 40s }`**: Servis sağlık kontrolünü tanımlar. `disable: true` ile kapatılabilir.
    *   **`user: <user>[:<group>]`** veya **`user: <UID>[:<GID>]`**: Konteyneri çalıştıracak kullanıcı.
    *   **`working_dir: /path/to/dir`**: Konteyner içindeki çalışma dizini.
    *   **`labels: { key: "value", ... }`** veya **`labels: ["key=value", ...]`**: Konteynere etiket ekler.
    *   **`deploy:`** (Swarm mode için) Replikasyon, güncelleme politikaları, kaynak limitleri, yerleştirme kısıtlamaları gibi orkestrasyon ayarlarını içerir.
    *   **`secrets:`** (Swarm mode için) Docker secret'larını servise bağlar.
    *   **`configs:`** (Swarm mode için) Docker config'lerini servise bağlar.
    *   ...ve diğerleri (`stop_grace_period`, `sysctls`, `ulimits`, `dns`, `tmpfs` vb.)
*   **`networks`**: Uygulama için özel ağları tanımlar. Burada tanımlanan ağlar, servisler bölümünde referans alınabilir. Docker Compose varsayılan olarak proje adıyla bir köprü ağı oluşturur, bu bölüm genellikle özel sürücüler veya seçenekler gerektiğinde kullanılır.
    *   **`<network_name>:`**
        *   **`driver: <driver_name>`**: Ağ sürücüsünü belirtir (`bridge`, `overlay`, `host`, `none` veya özel sürücü).
        *   **`driver_opts: { key: value, ... }`**: Sürücüye özel seçenekler.
        *   **`attachable: true`**: Diğer bağımsız konteynerlerin bu ağa bağlanmasına izin verir (overlay ağları için Swarm'da).
        *   **`ipam: { driver: default, config: [{ subnet: "172.28.0.0/16", ip_range: "172.28.5.0/24", gateway: "172.28.5.254" }] }`**: IP adresi yönetimi ayarları.
        *   **`external: true`**: Docker dışında (önceden) oluşturulmuş bir ağı kullanmak için. Compose bu ağı oluşturmaz/kaldırmaz. `name: <external_network_name>` ile dış ağın adı belirtilebilir.
        *   **`internal: true`**: Ağı sadece iç iletişim için yapar, dış dünyaya bağlantısı olmaz.
*   **`volumes`**: İsimlendirilmiş volume'leri tanımlar. Burada tanımlanan volume'ler, servisler bölümünde referans alınabilir. Servislerde sadece volume adı kullanıldığında (`- mydata:/data`) ve burada tanımlanmadığında, varsayılan sürücü ile otomatik olarak oluşturulur.
    *   **`<volume_name>:`**
        *   **`driver: <driver_name>`**: Volume sürücüsünü belirtir (varsayılan `local` veya özel sürücü).
        *   **`driver_opts: { key: value, ... }`**: Sürücüye özel seçenekler (NFS, CIFS bağlama seçenekleri vb. için).
        *   **`external: true`**: Docker dışında (önceden) oluşturulmuş bir volume'ü kullanmak için. Compose bu volume'ü oluşturmaz/kaldırmaz. `name: <external_volume_name>` ile dış volume'ün adı belirtilebilir.
        *   **`labels: { key: "value", ... }`** : Volume'e etiket ekler.
*   **`secrets`**: (Swarm mode için) Uygulama yığını tarafından kullanılacak secret'ları tanımlar. Kaynak olarak dosya veya `external: true` kullanılabilir.
*   **`configs`**: (Swarm mode için) Uygulama yığını tarafından kullanılacak yapılandırma dosyalarını tanımlar. Kaynak olarak dosya veya `external: true` kullanılabilir.

### Örnek `docker-compose.yml`

Basit bir Web Uygulaması (Python/Django) ve PostgreSQL veritabanı için örnek:

**Örnek docker-compose.yml dosyası:**
```yaml
version: '3.8' # Compose dosya formatı sürümü (opsiyonel ama önerilir)

services:
  # Web Uygulaması Servisi
  web:
    build: . # Mevcut dizindeki Dockerfile'ı kullanarak build et
    command: python manage.py runserver 0.0.0.0:8000 # Konteyner başlatma komutu
    volumes:
      - .:/code # Host'taki kodu konteynerdeki /code dizinine bağla (geliştirme için)
      - static_volume:/code/static # Statik dosyalar için isimlendirilmiş volume
    ports:
      - "8000:8000" # Host port 8000'i konteyner port 8000'e yönlendir
    networks: # Bağlanacağı ağlar (varsayılan ağ kullanılacaksa bu bölüm gereksiz)
      - default # Varsayılan ağı belirtmek için
    environment: # Ortam değişkenleri
      - SECRET_KEY=${SECRET_KEY} # .env dosyasından veya host ortamından alınır
      - DEBUG=${DEBUG:-0} # Varsayılan değer 0 (false)
      - DATABASE_URL=postgres://${POSTGRES_USER}:${POSTGRES_PASSWORD}@db:5432/${POSTGRES_DB}
    depends_on: # Başlatma bağımlılığı
      db:
        condition: service_healthy # db servisi sağlıklı olana kadar bekle
    restart: unless-stopped # Konteyner manuel durdurulmadıkça yeniden başlat
    healthcheck: # Web uygulamasının sağlığını kontrol et (örnek)
      test: ["CMD", "curl", "-f", "http://localhost:8000/_healthcheck/"]
      interval: 1m
      timeout: 10s
      retries: 3
      start_period: 30s

  # Veritabanı Servisi
  db:
    image: postgres:14-alpine # PostgreSQL imajını kullan
    volumes:
      - db_data:/var/lib/postgresql/data # Veritabanı dosyaları için isimlendirilmiş volume
    # networks: # Varsayılan ağda olacağı için belirtmeye gerek yok
    #   - default
    environment: # Veritabanı yapılandırması (.env'den okunur)
      - POSTGRES_DB=${POSTGRES_DB}
      - POSTGRES_USER=${POSTGRES_USER}
      - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
    restart: always # Her zaman yeniden başlat
    healthcheck: # PostgreSQL sağlığını kontrol et
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}"]
      interval: 10s
      timeout: 5s
      retries: 5

# networks: # Varsayılan 'default' ağı Docker Compose tarafından oluşturulur.
#   default:
#     driver: bridge

volumes:
  # İsimlendirilmiş volume'ler (boş bırakılırsa varsayılan ayarlarla oluşturulur)
  db_data:
  static_volume:
    # driver: local # Varsayılan
    # driver_opts: {}
```

### Environment Variable Yönetimi

Hassas bilgileri (API anahtarları, şifreler) doğrudan `docker-compose.yml` içine yazmak **güvensizdir** ve kötü bir pratiktir. Bunun yerine:

*   **`.env` Dosyası:** `docker-compose.yml` ile aynı dizinde veya üst dizinlerde bir `.env` dosyası oluşturun. Bu dosyadaki `KEY=VALUE` formatındaki değişkenler, Compose dosyası içinde `${KEY}` veya `$KEY` şeklinde kullanılabilir (enterpolasyon). `.env` dosyasını `.gitignore`'a eklemeyi **unutmayın!**
    ```
    # .env dosyası içeriği (örnek)
    # Yorum satırları # ile başlar
    POSTGRES_USER=django_user
    POSTGRES_PASSWORD=gizlisifre123!
    POSTGRES_DB=mydjangodb
    SECRET_KEY=cok-daha-uzun-ve-rastgele-bir-secret-key-burada
    DEBUG=1
    ```
    Compose dosyasında kullanım yukarıdaki örnekte gösterilmiştir. Değişkenin yanında varsayılan değer de verilebilir: `${VARIABLE:-default}`. Değer boş ise hata vermesi için: `${VARIABLE:?error message}`.
*   **`env_file` Direktifi:** Ortam değişkenlerini ayrı bir dosyadan yüklemek için kullanılır. Bu dosya da hassas bilgiler içerebilir ve versiyon kontrolüne eklenmemelidir. `environment` ile birlikte kullanılabilir (`environment` önceliklidir).
    ```yaml
    services:
      web:
        env_file:
          - ./config/web.env
          - ./config/common.env # Birden fazla dosya belirtilebilir
        environment:
          - OVERRIDE_VAR=new_value # env_file'dakini ezer
    ```
*   **Sistem Ortam Değişkenleri:** Docker Compose çalıştırıldığı kabukta tanımlı olan ortam değişkenleri de `.env` dosyasındakiler gibi enterpolasyon için kullanılabilir. `.env` dosyasındaki değişkenler genellikle kabuktaki aynı isimli değişkenleri ezer.
*   **Docker Secrets:** Daha güvenli bir yöntem, özellikle Swarm veya Kubernetes gibi orkestrasyon ortamlarında Docker Secrets veya eşdeğer mekanizmaları kullanmaktır. Compose dosyası tek başına çalışırken bu doğrudan desteklenmez (Swarm modu hariç).

### Scaling with Compose

Belirli bir servisin birden fazla kopyasını (konteynerini) çalıştırmak için `up` komutuyla `--scale` seçeneği kullanılır:
```bash
# 'worker' servisinden 3 kopya, 'api' servisinden 2 kopya başlat
docker compose up -d --scale worker=3 --scale api=2

# Not: Ölçeklenen servislerin gelen istekleri nasıl dağıtacağı (load balancing)
# ayrıca düşünülmelidir. Docker Compose tek başına gelişmiş yük dengeleme sağlamaz.
# Genellikle önüne bir Nginx, HAProxy veya Traefik gibi
# bir reverse proxy/load balancer konulur ve bu proxy, ölçeklenen
# servis konteynerlerine istekleri dağıtır.
```

# Docker Swarm (Temel Seviye): Dahili Konteyner Orkestrasyonu

*Not: Bu bölüm, Docker'ın kendi orkestrasyon çözümüne temel bir giriş sağlar. Daha karmaşık ve yaygın kullanılan çözüm Kubernetes'tir, ancak Swarm daha basit senaryolar için veya öğrenme amacıyla iyi bir başlangıç noktası olabilir.*

## Neden Orkestrasyon?

Tek bir host üzerinde Docker ve Docker Compose kullanmak geliştirme ve basit uygulamalar için yeterli olabilir. Ancak uygulamalar büyüdükçe, daha fazla kullanıcıya hizmet vermesi gerektiğinde ve yüksek erişilebilirlik kritik hale geldiğinde, uygulamayı birden fazla sunucuya (host) dağıtmak ve yönetmek gerekir. Bu noktada şu ihtiyaçlar ortaya çıkar:

*   **Yüksek Kullanılabilirlik (High Availability):** Bir sunucu (node) çökerse, uygulamanın diğer sunucularda çalışmaya devam etmesi ve servis kesintisinin minimize edilmesi.
*   **Yük Dengeleme (Load Balancing):** Gelen trafiği uygulamanın birden fazla çalışan kopyasına (konteyner/replica) otomatik olarak dağıtmak.
*   **Ölçeklenebilirlik (Scalability):** Artan veya azalan yüke göre çalışan konteyner sayısını kolayca ve otomatik olarak artırıp azaltabilmek (yatay ölçeklenme).
*   **Kolay Dağıtım ve Güncelleme (Deployment & Rolling Updates):** Yeni uygulama sürümlerini kesinti olmadan veya minimum kesintiyle (rolling update) devreye almak ve gerektiğinde kolayca geri alabilmek (rollback).
*   **Servis Keşfi (Service Discovery):** Konteynerlerin (özellikle farklı servislerdekilerin) birbirini ağ üzerinde dinamik olarak bulabilmesi (IP adreslerini manuel bilmeye gerek kalmadan).
*   **Sağlık Kontrolü ve Self-Healing (Health Checking):** Çalışmayan veya sağlıksız hale gelen konteynerleri otomatik olarak tespit edip yeniden başlatmak veya değiştirmek.
*   **Merkezi Yönetim:** Tüm bu işlemleri birden fazla makine üzerinde merkezi bir noktadan yönetebilmek.

İşte bu görevleri otomatikleştiren ve yöneten sistemlere **konteyner orkestrasyon araçları** denir. Docker Swarm ve Kubernetes en popüler örnekleridir.

## Docker Swarm Nedir?

Docker Swarm, Docker Engine içine **gömülü** olarak gelen, basit ve kullanımı kolay bir konteyner orkestrasyon modudur. Birden fazla Docker host'unu (fiziksel veya sanal makineler) tek bir sanal Docker host gibi davranan bir **küme (cluster)** halinde birleştirmenizi sağlar. Kubernetes'e göre daha az özelliğe sahip olsa da, kurulumu, öğrenmesi ve yönetimi daha basittir ve temel orkestrasyon ihtiyaçları (yüksek erişilebilirlik, ölçekleme, rolling update, servis keşfi) için yeterli olabilir. Mevcut Docker CLI ve Docker Compose dosyaları (küçük değişikliklerle) ile büyük ölçüde uyumludur.

## Swarm Mimarisi

*   **Nodes (Düğümler):** Swarm kümesine katılan her bir Docker Engine instance'ıdır (makinedir). İki tür node vardır:
    *   **Manager Nodes (Yönetici Düğümler):** Kümenin durumunu (Raft konsensüs algoritması kullanarak dağıtık bir veritabanında) korur, yönetim görevlerini (servis oluşturma/güncelleme/silme) yürütür ve görevleri (konteyner çalıştırma işleri) worker node'lara dağıtır (scheduling). Yüksek kullanılabilirlik ve hata toleransı için birden fazla (genellikle tek sayıda, örn: 3 veya 5) manager olması önerilir. Manager'lardan biri *lider (leader)* olarak aktif görev yapar, diğerleri yedektir (standby). Lider çökerse, kalan manager'lar arasından yeni bir lider seçilir.
    *   **Worker Nodes (Çalışan Düğümler):** Manager'lardan aldıkları görevleri (tasks), yani konteynerleri çalıştırmakla yükümlüdürler. Uygulama yükünü asıl taşıyan nodelardır. Manager node'lar aynı zamanda worker olarak da görev yapabilir (varsayılan davranış budur, `docker node update --availability drain <node>` ile engellenebilir).
*   **Services (Servisler):** Swarm kümesinde çalıştırılmak istenen uygulamanın veya bir bileşeninin tanımıdır. Bir servisin hangi Docker imajını kullanacağını, kaç kopyasının (replica) çalışacağını (veya her node'da bir tane mi çalışacağını - global mode), ağ ayarlarını, port yönlendirmelerini, güncelleme stratejilerini, kaynak limitlerini, yeniden başlatma politikalarını vb. belirtir. `docker service create` komutuyla veya Docker Compose dosyasındaki (`deploy` bölümüyle) `docker stack deploy` komutuyla tanımlanır.
*   **Tasks (Görevler):** Bir servisin çalışan her bir konteyner kopyasıdır (instance). Swarm manager, bir servis oluşturulduğunda veya ölçeklendiğinde, servisin tanımına göre (örneğin 3 replica istenmişse) 3 adet task oluşturur ve bunları uygun worker (veya manager) node'lara zamanlar (schedule). Bir task'ın çalıştığı node çökerse veya task'ın kendisi (konteyner) başarısız olursa, manager bunu tespit eder ve servisin istenen durumda (desired state) kalmasını sağlamak için (örneğin başka bir node'da) yeni bir task başlatır (self-healing). Task'lar Swarm'ın en küçük zamanlama birimidir.
*   **Stacks (Yığınlar):** Birbirleriyle ilişkili birden fazla servisi (genellikle tam bir uygulamayı oluşturan bileşenler) tek bir birim olarak tanımlayıp yönetmeyi sağlar. Genellikle Swarm için uyumlu hale getirilmiş (özellikle `deploy` anahtarı eklenmiş) bir `docker-compose.yml` dosyası kullanılarak dağıtılır (`docker stack deploy`). Docker Compose'un Swarm modundaki karşılığıdır ve çoklu servis uygulamalarını Swarm üzerinde yönetmenin standart yoludur.
*   **Load Balancing (Yük Dengeleme):** Swarm, küme içinde çalışan servislere gelen dış istekleri otomatik olarak dağıtmak için dahili bir yük dengeleyiciye sahiptir. Bu iki kısımdan oluşur:
    *   **Ingress Network (Giriş Ağı):** Servis portları yayınlandığında (`docker service create -p <published_port>:<target_port>`), Swarm otomatik olarak `ingress` adında özel bir overlay ağı oluşturur. Kümedeki *herhangi bir* node'un `<published_port>` portuna gelen istekler bu ağ üzerinden alınır.
    *   **Routing Mesh (Yönlendirme Ağı):** Ingress ağına gelen istekler, kümedeki *tüm* node'lar tarafından bilinir ve istek, servisin o an çalışan sağlıklı task'larından birine (hangi node'da çalıştığına bakılmaksızın) dahili bir sanal IP (VIP - Virtual IP) üzerinden yönlendirilir. Bu sayede, istemci herhangi bir node'a bağlanarak servise erişebilir ve Swarm yükü otomatik olarak dağıtır.

    Ayrıca, aynı overlay ağındaki servisler de birbirlerine servis isimleri üzerinden (Docker'ın DNS tabanlı servis keşfi ile) erişebilir ve Swarm bu iç trafiği de ilgili task'lara yönlendirir.

## Temel Swarm Komutları

Swarm modunu etkinleştirmek, kümeyi yönetmek ve servisleri dağıtmak için standart `docker` CLI kullanılır. Bu komutlar genellikle **manager** node üzerinde çalıştırılır (aksi belirtilmedikçe).

**Temel Swarm Komutları:**
```bash
# --- Küme Yönetimi ---
# Mevcut host'u bir Swarm kümesinin ilk manager node'u olarak başlatır
# --advertise-addr: Diğer node'ların bu manager'a bağlanacağı IP adresini belirtir (genellikle zorunlu değil, otomatik algılanır)
# --listen-addr: Swarm kontrol trafiğini dinleyeceği adres (varsayılan 0.0.0.0:2377)
docker swarm init [--advertise-addr <MANAGER-IP>]

# Mevcut host'u bir worker node olarak mevcut Swarm'a katmak için
# TOKEN ve MANAGER-IP:PORT bilgisi 'docker swarm init' çıktısında veya 'docker swarm join-token worker' ile alınır
docker swarm join --token <WORKER-TOKEN> <MANAGER-IP>:<PORT>

# Mevcut host'u bir manager node olarak mevcut Swarm'a katmak için
# Manager token'ını almak için lider manager'da 'docker swarm join-token manager' çalıştırın
docker swarm join --token <MANAGER-TOKEN> <MANAGER-IP>:<PORT>

# Worker veya Manager eklemek için gerekli join token'ını gösterir (Lider manager'da çalıştırılır)
docker swarm join-token worker
docker swarm join-token manager

# Bir node'u Swarm'dan ayrılmaya zorlar (o node üzerinde çalıştırılır)
docker swarm leave [--force] # --force manager'lar için gerekebilir

# Swarm kümesinin genel yapılandırmasını günceller (örn: token rotasyonu, sertifika süreleri)
docker swarm update [OPTIONS]

# Swarm kilidini açmak için gerekli anahtarı gösterir (lider manager'da)
docker swarm unlock-key

# Swarm kilitlendiğinde (örneğin manager quorum kaybedildiğinde) kilidi açar (yeni liderde)
docker swarm unlock --key <UNLOCK-KEY>

# --- Node Yönetimi (Manager'da Çalıştırılır) ---
# Kümedeki tüm node'ları ve durumlarını (Durum, Rol, Erişilebilirlik) listeler
docker node ls

# Bir node hakkında detaylı bilgi gösterir (JSON formatında)
docker node inspect <NODE-ID | NODE-HOSTNAME>

# Bir node'un durumunu (availability: active, pause, drain) veya rolünü (role: worker, manager) günceller
# drain: Node'a yeni task zamanlanmasını engeller ve mevcut task'ları başka node'lara taşır (bakım için)
docker node update --availability drain <NODE-ID>
docker node update --role manager <NODE-ID>

# Bir worker node'u manager rolüne yükseltir
docker node promote <NODE-ID> [<NODE-ID>...]

# Bir manager node'u worker rolüne indirir
docker node demote <NODE-ID> [<NODE-ID>...]

# 'Down' durumdaki bir node'u kümeden kaldırır (Önce 'docker swarm leave' veya makine kapatılmalı)
docker node rm <NODE-ID> [<NODE-ID>...]

# --- Servis Yönetimi (Manager'da Çalıştırılır) ---
# Yeni bir servis oluşturur (docker run'a benzer ama orkestrasyonlu)
docker service create [OPTIONS] IMAGE [COMMAND] [ARG...]
# Örnek: 3 kopyalı bir redis servisi oluşturma ve port yayınlama
# docker service create --name my-redis --replicas 3 -p 6379:6379 redis:alpine
# Örnek: Her node'da bir tane çalışacak global modda bir servis
# docker service create --name monitoring-agent --mode global my-agent-image

# Kümede çalışan servisleri listeler
docker service ls

# Bir servis hakkında detaylı bilgi gösterir (JSON formatında)
docker service inspect [OPTIONS] SERVICE [SERVICE...]
# Örnek: Sadece yayınlanan portları görme
# docker service inspect --format '{{range .Endpoint.Ports}}{{.PublishedPort}}:{{.TargetPort}} {{end}}' my-redis
# Örnek: Pretty formatta gösterme
# docker service inspect --pretty my-redis

# Bir servisin çalışan task'larını (konteynerlerini) ve durumlarını listeler
docker service ps SERVICE [SERVICE...]
# Örnek: my-redis servisinin task'ları hangi node'larda çalışıyor?
# docker service ps my-redis

# Bir servisin loglarını gösterir (varsayılan olarak tüm task'lardan toplanır)
docker service logs [OPTIONS] SERVICE
# Örnek: Logları takip etme
# docker service logs -f my-app

# Çalışan bir servisi kaldırır (tüm task'ları durdurur ve kaldırır)
docker service rm SERVICE [SERVICE...]

# Bir servisin replica sayısını değiştirir (ölçekleme) (sadece replicated moddaki servisler için)
docker service scale SERVICE=REPLICAS [SERVICE=REPLICAS...]
# Örnek: my-redis servisini 5 kopyaya çıkar
# docker service scale my-redis=5

# Çalışan bir servisin ayarlarını günceller (imaj, port, env, limitler, güncelleme politikası vb.)
docker service update [OPTIONS] SERVICE
# Örnek: my-redis servisinin imajını güncelleme (rolling update yapar)
# docker service update --image redis:latest my-redis
# Örnek: Güncelleme paralel程度ini ayarlama
# docker service update --update-parallelism 2 --update-delay 10s my-app

# Bir servisi hemen önceki yapılandırmasına geri alır (rollback)
docker service rollback [OPTIONS] SERVICE

# --- Stack Yönetimi (Manager'da Çalıştırılır) ---
# Bir Compose dosyası kullanarak bir uygulama yığınını dağıtır veya günceller
docker stack deploy [OPTIONS] -c <COMPOSE-FILE> STACK_NAME
# Örnek:
# docker stack deploy -c docker-compose.yml my-app-stack
# Örnek: Registry kimlik bilgileriyle (eğer özel registry ise)
# docker stack deploy --with-registry-auth -c docker-compose.prod.yml prod-stack

# Çalışan stack'leri listeler
docker stack ls

# Bir stack'e ait servisleri listeler
docker stack services [OPTIONS] STACK_NAME

# Bir stack'e ait task'ları (konteynerleri) listeler
docker stack ps [OPTIONS] STACK_NAME

# Bir stack'i ve ona ait tüm kaynakları (servisler, ağlar, secret'lar) kaldırır
docker stack rm STACK_NAME [STACK_NAME...]

# --- Secret ve Config Yönetimi (Manager'da Çalıştırılır) ---
# Yeni bir secret oluşturur (dosyadan veya stdin'den)
docker secret create [OPTIONS] SECRET file|-
# echo "mypassword" | docker secret create db_password -

# Secret'ları listeler
docker secret ls

# Bir secret'ı kaldırır
docker secret rm SECRET [SECRET...]

# Bir secret'ı inceler (içeriği GÖSTERMEZ)
docker secret inspect SECRET [SECRET...]

# Yeni bir config oluşturur (dosyadan veya stdin'den)
docker config create [OPTIONS] CONFIG file|-
# docker config create my_config ./config.json

# Config'leri listeler
docker config ls

# Bir config'i kaldırır
docker config rm CONFIG [CONFIG...]

# Bir config'i inceler (içeriği GÖSTERİR)
docker config inspect CONFIG [CONFIG...]
```

## Replication vs Global Services

Servis oluştururken (`docker service create` veya Compose dosyasında `deploy` bölümünde) iki dağıtım modu seçilebilir:

*   **Replicated (Varsayılan):** `--replicas N` ile (veya `deploy.replicas` içinde) belirtilen sayıda task (konteyner kopyası) oluşturulur ve Swarm bunları kaynak ve kısıtlama (constraints/preferences) kurallarına göre uygun node'lara dağıtır. Bir node çökerse, üzerindeki task'lar başka uygun node'larda yeniden başlatılır. Yük dengeleme ve yüksek erişilebilirlik için standart moddur.
*   **Global:** `--mode global` ile (veya `deploy.mode: global` içinde) belirtilir. Swarm, kümedeki *her* uygun (kısıtlamaları karşılayan ve 'active' durumda olan) node üzerinde bu servisten *tam olarak bir* task çalıştırılmasını sağlar. Yeni bir node eklendiğinde veya bir node uygun hale geldiğinde, o node üzerinde otomatik olarak bir task başlatılır. Genellikle izleme ajanları (monitoring agents - örn: node-exporter), log toplayıcılar (örn: fluentd), ağ eklentileri veya her node'da çalışması gereken altyapı servisleri için kullanılır.

## Rolling Updates and Rollbacks

Bir servisi güncellerken (`docker service update --image ...` veya `docker stack deploy` ile yeni konfigürasyon içeren bir compose dosyası) Swarm, varsayılan olarak **rolling update** stratejisini kullanır:

1.  Swarm, task'ları gruplar halinde günceller (paralellik `--update-parallelism` ile ayarlanır, varsayılan 1).
2.  Seçilen gruptaki eski task'ları durdurur.
3.  Yerine yeni konfigürasyonla yeni task'lar başlatır.
4.  Yeni task'ların sağlıklı çalıştığını kontrol eder (healthcheck tanımlıysa ona göre, yoksa 'running' durumuna geçmesine göre). Başarısız olursa `--update-failure-action` (varsayılan: 'pause') devreye girer.
5.  Başarılıysa, bir sonraki gruba geçmeden önce belirli bir süre bekler (`--update-delay`, varsayılan 0).
6.  Bu işlem tüm task'lar güncellenene veya bir hata nedeniyle duraklatılana kadar devam eder.

Bu sayede güncelleme sırasında servis tamamen kesintiye uğramaz. `docker service rollback <service>` komutu ile bir servis kolayca bir önceki stabil yapılandırmasına geri döndürülebilir. Güncelleme ve rollback davranışları `deploy.update_config` ve `deploy.rollback_config` bölümlerinde Compose dosyasında detaylı olarak yapılandırılabilir.

# Güvenlik En İyi Uygulamaları

Konteynerler izolasyon sağlasa da, bu tam bir güvenlik çözümü değildir ve yanlış yapılandırıldığında ciddi riskler oluşturabilir. Hem imajlarınızı, hem konteynerlerinizi hem de Docker host ortamınızı güvende tutmak için bilinçli ve dikkatli olmanız gerekir.

## İmaj Güvenliği

*   **Minimal Temel İmaj Kullanın (`alpine`, `distroless`, `scratch`):** İhtiyacınız olmayan paketleri, kütüphaneleri ve hatta kabuk (shell) gibi araçları içermeyen mümkün olan en küçük temel imajları kullanın. Saldırı yüzeyini (attack surface) ve potansiyel güvenlik açığı sayısını azaltır. `distroless` imajları (Google tarafından sağlanır) sadece uygulamanızı ve onun çalışma zamanı bağımlılıklarını içerir, paket yöneticisi veya shell barındırmaz. `scratch` boş bir imajdır, statik derlenmiş uygulamalar için kullanılabilir.
*   **Resmi ve Doğrulanmış İmajları Tercih Edin:** Docker Hub'daki "Official Images" (resmi olarak desteklenen ve bakımı yapılan) veya güvendiğiniz yazılım sağlayıcılarının (Microsoft, Red Hat, Bitnami vb.) imajlarını kullanın. Kaynağı belirsiz, popüler olmayan veya uzun süredir güncellenmemiş imajlardan kaçının.
*   **İmajları Güncel Tutun (Patching):** Temel imajlardaki ve uygulama bağımlılıklarındaki (OS paketleri, kütüphaneler) güvenlik yamalarını almak için imajlarınızı düzenli olarak yeniden build edin. Dockerfile'da paket yöneticisinin güncelleme (`apt-get update/upgrade`, `apk update/upgrade`) ve temizleme adımlarını ekleyin. Bağımlılıkları (`npm update`, `pip install --upgrade`, `mvn versions:use-latest-releases`) güncel tutun. Bu süreci CI/CD pipeline'larınızda otomatikleştirin.
*   **İmaj Tarama (Vulnerability Scanning) Araçları Kullanın:** İmajlarınızı oluşturduktan sonra (ve ideal olarak CI/CD sürecinde) bilinen güvenlik açıklarına (CVE'lere - Common Vulnerabilities and Exposures) karşı tarayın. Popüler araçlar:
    *   **Docker Scout:** Docker Desktop, Docker Hub ve Sysdig entegrasyonu ile çalışan, güvenlik açıkları, lisans uyumluluğu ve en iyi pratikler konusunda analiz sunan bir Docker hizmetidir.
    *   **Trivy (Aqua Security):** Açık kaynaklı, popüler, hızlı ve kullanımı kolay bir zafiyet ve yanlış yapılandırma tarayıcısıdır. CI/CD ile kolayca entegre olur.
    *   **Grype (Anchore):** Açık kaynaklı başka bir popüler zafiyet tarayıcısı.
    *   **Snyk:** Kapsamlı bir geliştirici güvenlik platformudur (kod, bağımlılıklar, imajlar, IaC taraması). Ticari bir üründür ancak açık kaynaklı projeler ve sınırlı kullanım için ücretsiz planları vardır.
    Bu taramaları CI/CD sürecine entegre ederek güvensiz imajların registry'ye push edilmesini veya dağıtılmasını engelleyebilirsiniz.
*   **Multi-stage Build Kullanın:** Derleme araçlarını (JDK, Go compiler, Node.js dev dependencies), test bağımlılıklarını, kaynak kodunu ve geçici dosyaları son (final) üretim imajına dahil etmemek için multi-stage build'leri kullanın. Sadece uygulamanın çalışması için gerekli olan artefaktları ve minimal çalışma zamanını içeren küçük bir imaj oluşturun. Bu, imaj boyutunu küçültür ve saldırı yüzeyini önemli ölçüde azaltır.
*   **Hassas Bilgileri İmaja Gömme! (ÇOK ÖNEMLİ):** API anahtarları, şifreler, özel sertifikalar, token'lar gibi hassas bilgileri ASLA doğrudan Dockerfile'a (ne `ENV` ile ne de `ARG` ile) veya imaj katmanlarına yazmayın (`COPY secrets.txt /app` gibi). Bu bilgiler imajı inceleyen herkes tarafından görülebilir. Hassas verileri çalışma zamanında güvenli bir şekilde sağlamak için ortam değişkenleri (dikkatli kullanımla), Docker secrets (Swarm/K8s), volume mount'lar (host'ta güvenli saklanıyorsa) veya HashiCorp Vault gibi harici secret yönetim araçları kullanın. Build sırasında geçici olarak secret'a ihtiyaç varsa BuildKit'in `--mount=type=secret` özelliğini kullanın.
*   **Dockerfile'ı Lint Edin (örn: Hadolint):** Dockerfile'ınızdaki yaygın hataları, en iyi pratiklere aykırı durumları ve potansiyel güvenlik sorunlarını tespit etmek için `hadolint` gibi lint araçlarını kullanın.
*   **LABEL ile Meta Veri Ekleyin:** İmajın kaynağını, sürümünü, sahibini, VCS referansını (commit hash) ve diğer önemli bilgileri `LABEL` direktifi ile ekleyin. Bu, imajın takibini ve yönetimini kolaylaştırır. Open Container Initiative (OCI) standart etiketlerini (<https://github.com/opencontainers/image-spec/blob/main/annotations.md>) kullanmayı düşünün.

## Konteyner Çalışma Zamanı Güvenliği

*   **Root Olmayan Kullanıcı ile Çalıştırın (`USER` direktifi / `docker run -u`):** Konteyner içindeki ana süreci asla `root` (UID 0) olarak çalıştırmayın. Bu, en temel ve en önemli güvenlik önlemlerinden biridir. Dockerfile'da `RUN groupadd ... && useradd ...` ile özel, yetkileri kısıtlı bir kullanıcı/grup oluşturun ve Dockerfile'ın sonuna doğru `USER` direktifi ile bu kullanıcıya geçin. Bu, konteynerden kaçış (container escape) veya konteyner içindeki bir zafiyetin sömürülmesi durumunda saldırganın host üzerindeki yetkilerini sınırlar (Least Privilege Prensibi). `docker run -u <user>:<group>` ile de çalışma zamanında kullanıcı değiştirilebilir.
*   **Salt Okunur (Read-Only) Root Dosya Sistemi Kullanın (`--read-only`):** Mümkünse, konteynerin kök dosya sistemini salt okunur olarak başlatın (`docker run --read-only`). Bu, konteyner içine zararlı yazılım yüklenmesini, konfigürasyonun izinsiz değiştirilmesini veya mevcut dosyaların üzerine yazılmasını engeller. Uygulamanızın geçici olarak yazması gereken dizinler varsa (örn: `/tmp`, cache dizinleri, log dizinleri), bunlar için `--tmpfs` (bellekte geçici) veya isimlendirilmiş volume (`-v my-writable-data:/app/data`) kullanın.
*   **Linux Yeteneklerini (Capabilities) Sınırlayın (`--cap-drop`, `--cap-add`):** Docker, varsayılan olarak konteynerlere `root`'un sahip olduğu birçok yeteneğin (capabilities) bir alt kümesini verir. `docker run --cap-drop=ALL` ile tüm bu varsayılan yetenekleri kaldırıp, sadece uygulamanızın çalışması için kesinlikle gerekli olanları `--cap-add=<CAPABILITY_NAME>` ile tek tek ekleyin (Least Privilege). Örneğin, ping atmak için `NET_RAW`, 80 gibi düşük portları dinlemek için `NET_BIND_SERVICE` (genellikle root olmayan kullanıcılar için gerekmez, port yönlendirme kullanılır) gerekebilir. Hangi yeteneklerin varsayılan olduğunu ve hangilerinin gerekli olduğunu dikkatlice analiz edin.
*   **Kaynak Limitleri Belirleyin (`--memory`, `--cpus`, `--pids-limit`):** Konteynerlerin kullanabileceği maksimum bellek (`--memory="512m"`), CPU (`--cpus="0.5"`), ve oluşturabileceği process/thread sayısı (`--pids-limit=100`) gibi kaynakları sınırlayın. Bu, tek bir konteynerin tüm host kaynaklarını tüketerek diğerlerini veya host'un kendisini etkilemesini (Denial of Service - DoS saldırısı veya kaynak tükenmesi) önler.
*   **Yeni Yetki Kazanmayı Engelle (`--security-opt no-new-privileges`):** Bu önemli güvenlik seçeneği, konteyner içindeki süreçlerin `setuid` veya `setgid` bitleri olan programları çalıştırarak veya başka yollarla mevcut yetkilerinden daha fazlasını kazanmasını engeller. Mutlaka kullanılması önerilir.
*   **Güvenlik Profilleri Kullanın (`--security-opt`):** Linux güvenlik modüllerinden yararlanın:
    *   **Seccomp (Secure Computing Mode):** Konteynerin yapabileceği sistem çağrılarını (syscalls) kısıtlar. Docker varsayılan olarak makul derecede kısıtlayıcı bir seccomp profili kullanır. Daha sıkı özel profiller oluşturup (`--security-opt seccomp=<profile.json>`) uygulayarak kernel saldırı yüzeyini daha da azaltabilirsiniz.
    *   **AppArmor** veya **SELinux (Security-Enhanced Linux):** Zorunlu Erişim Kontrolü (Mandatory Access Control - MAC) mekanizmalarıdır. Konteynerin hangi dosyalara (okuma/yazma/çalıştırma), ağ kaynaklarına veya diğer yeteneklere erişebileceğini daha detaylı ve kural tabanlı olarak kontrol ederler. Docker varsayılan olarak (eğer host'ta etkinse) `docker-default` adında bir AppArmor profili uygular. Özel profiller oluşturup (`--security-opt apparmor=<profile_name>` veya `--security-opt label=type:your_selinux_type`) daha granüler kontrol sağlayabilirsiniz.
*   **`--privileged` Moddan Mutlaka Kaçının!**: Bu seçenek konteynere host üzerindeki TÜM cihazlara (`/dev`) erişim ve neredeyse tüm kernel yeteneklerini verir. Konteyner izolasyonunu tamamen ortadan kaldırır ve host'u ele geçirmeyi çok kolaylaştırır. Sadece çok özel ve kaçınılmaz durumlarda (örneğin Docker içinde Docker çalıştırmak gibi çok spesifik senaryolar) ve riskleri tam olarak anlayarak kullanılmalıdır. Genellikle daha güvenli alternatifler (örneğin belirli cihazları `--device` ile eklemek, yetenekleri `--cap-add` ile vermek) vardır.
*   **Gereksiz Portları Açmayın ve Host'a Bağlamayın:** Dockerfile'da sadece uygulamanın ihtiyaç duyduğu portları `EXPOSE` edin. Konteyneri çalıştırırken (`docker run -p`), sadece dışarıdan veya host'tan erişilmesi gereken portları host'a bağlayın. Mümkünse sadece belirli bir IP'ye (`-p 127.0.0.1:host:container`) veya sadece konteynerler arası iletişim için kullanıcı tanımlı ağları kullanın.

## Secret Yönetimi

Hassas bilgilerin (veritabanı şifreleri, API anahtarları, TLS sertifikaları) güvenli bir şekilde yönetilmesi kritiktir.

*   **İmaja Gömme (Yanlış!):** Asla hardcode etmeyin.
*   **Ortam Değişkenleri (`-e`, `environment`):** Yaygın kullanılır ancak bazı riskleri vardır: `docker inspect` ile veya link edilmiş (eski yöntem) konteynerler tarafından görülebilirler. Bazı dillerde/frameworklerde process ortamından kolayca sızdırılabilirler. Zorunlu olmadıkça hassas veriler için ilk tercih olmamalıdır. Eğer kullanılacaksa, değerlerin CI/CD ortam değişkenlerinden veya güvenli bir yerden enjekte edildiğinden emin olun.
*   **Docker Secrets (Swarm veya Kubernetes):** Orkestrasyon araçlarının sunduğu dahili secret yönetim mekanizmalarıdır. Secret'lar orkestratör tarafından şifreli olarak (at rest) saklanır ve sadece ilgili servisin konteynerlerine çalışma zamanında geçici olarak (genellikle `/run/secrets/` altında salt okunur dosya olarak) mount edilir. En güvenli yöntemlerden biridir. Uygulamanın bu dosyalardan okuyacak şekilde adapte edilmesi gerekir.
    ```bash
    # Swarm'da secret oluşturma ve kullanma
    echo "my-super-secret-password" | docker secret create db_password -
    docker service create --name mydb --secret db_password ... postgres:14
    # Konteyner içinde /run/secrets/db_password dosyasından okunur
    ```
*   **Harici Secret Yönetim Araçları (Vault, AWS/Azure/GCP Secrets Manager):** HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, Google Secret Manager gibi araçlar merkezi, denetlenebilir ve güvenli secret yönetimi sunar (şifreleme, rotasyon, erişim kontrolü vb.). Uygulamaların veya başlatma script'lerinin bu servislerle entegre olarak (API veya agent aracılığıyla) secret'ları alması gerekir. Genellikle en iyi ve en ölçeklenebilir çözümdür.
*   **Volume Mounts (Dikkatli):** Hassas konfigürasyon dosyalarını veya sertifikaları içeren bir volume'ü konteynere mount etmek bir seçenektir. Ancak bu durumda host üzerindeki dosyanın/volume'ün kendisinin güvenliğinin (izinler, şifreleme) sağlanması ve erişimin sıkı bir şekilde kontrol edilmesi gerekir.

## Network Güvenliği

*   **Kullanıcı Tanımlı Ağlar Kullanın:** Konteynerleri varsayılan `bridge` ağı yerine, mantıksal olarak ilişkili servis grupları için özel kullanıcı tanımlı köprü ağlarına (`docker network create ...`) yerleştirin. Bu, ağ segmentasyonu sağlar ve gereksiz yere tüm konteynerlerin birbirini görmesini engeller. Farklı ağlardaki konteynerler varsayılan olarak birbirleriyle iletişim kuramaz.
*   **Ağ Politikaları (İleri Seviye - K8s, Calico vb.):** Kubernetes gibi platformlar, hangi pod'ların (konteyner grupları) hangi portlar ve protokoller üzerinden birbirleriyle veya dış kaynaklarla iletişim kurabileceğini detaylı olarak tanımlayan ağ politikaları (Network Policies) sunar. Docker Swarm'da bu yetenek daha sınırlıdır, ancak Calico gibi CNI eklentileri Swarm ile de kullanılabilir.
*   **Giriş Kontrolü (Ingress Controller / Reverse Proxy):** Konteynerlerinize doğrudan dışarıdan erişim vermek yerine, Nginx, Traefik, HAProxy gibi bir ters proxy veya bir API Gateway kullanarak gelen trafiği yönetin ve filtreleyin. Bu katman SSL/TLS sonlandırma, kimlik doğrulama/yetkilendirme, hız sınırlama (rate limiting), WAF (Web Application Firewall) entegrasyonu gibi güvenlik görevlerini üstlenebilir.
*   **Host Güvenlik Duvarı (Firewall):** Host makinesinin güvenlik duvarında (iptables, firewalld, ufw) Docker tarafından otomatik olarak eklenen kuralları (özellikle `DOCKER` ve `DOCKER-USER` zincirleri) anlayın ve gerekiyorsa özelleştirin. Sadece Docker'ın ve gerekli servislerin kullandığı portlara dışarıdan erişime izin verin. `DOCKER-USER` zinciri, Docker'ın otomatik kurallarından önce çalışan özel kurallar eklemek için kullanılabilir.
*   **Docker Daemon Portunu Açığa Çıkarmayın:** Docker daemon'ın TCP portunu (genellikle 2375/2376) güvensiz bir şekilde ağa açmayın. Eğer uzaktan erişim gerekiyorsa, mutlaka TLS kimlik doğrulaması (`--tlsverify`, `--tlscacert`, `--tlscert`, `--tlskey` seçenekleri) ile koruyun.

## Host ve Daemon Güvenliği

*   **Host İşletim Sistemini Güvenli Tutun (Hardening):** Host OS'yi güncel tutun (güvenlik yamaları), gereksiz servisleri ve yazılımları kaldırın/kapatın, güvenlik duvarını yapılandırın, erişimi (SSH vb.) sıkılaştırın (güçlü şifreler, anahtar tabanlı kimlik doğrulama, fail2ban vb.) ve düzenli olarak güvenlik taramaları yapın. Host ele geçirilirse, üzerindeki tüm konteynerler ve veriler tehlikeye girer. CIS Benchmark'ları gibi standartları takip etmeyi düşünün.
*   **Docker Daemon Erişimini Sınırlayın:** Docker daemon soketine (`/var/run/docker.sock`) erişim, host üzerinde *root erişimi ile eşdeğerdir*. Çünkü bu soket üzerinden `--privileged` konteynerler veya host dizinlerini mount eden konteynerler çalıştırılabilir.
    *   Docker soketine erişimi sadece kesinlikle güvendiğiniz ve bu yetkiye ihtiyacı olan kullanıcılarla (genellikle sadece `root` ve `docker` grubu) sınırlayın. Geliştiricilere veya CI/CD sistemlerine doğrudan soket erişimi vermek yerine daha kontrollü mekanizmalar (orkestrasyon araçları, özel API'ler) kullanmayı düşünün.
    *   `docker` grubuna eklediğiniz kullanıcıların aslında host üzerinde tam yetkiye sahip olduğunu unutmayın.
*   **Rootless Docker Kullanımını Değerlendirin:** Mümkünse, Docker daemon'ı ve konteynerleri root olmayan bir kullanıcı olarak çalıştırmayı sağlayan Rootless modu kullanın. Bu, potansiyel bir konteyner kaçışı durumunda host üzerindeki etkiyi önemli ölçüde azaltır. Bazı kısıtlamaları olsa da (host ağı kullanamama, düşük portları bind edememe, cgroups limitlerinde kısıtlamalar vb.), güvenlik açısından önemli bir adımdır. (<https://docs.docker.com/engine/security/rootless/>)
*   **Docker Sürümlerini Güncel Tutun:** Docker Engine, Docker Compose ve diğer Docker araçlarının en son stabil ve yamalı sürümlerini kullanın. Yeni sürümler genellikle güvenlik düzeltmeleri ve iyileştirmeleri içerir.
*   **Docker Daemon Konfigürasyonunu Güvenlileştirin (`daemon.json`):** `/etc/docker/daemon.json` dosyasındaki ayarları gözden geçirin. Örneğin, varsayılan `ulimit`'leri ayarlayabilir, log sürücüsünü ve seçeneklerini yapılandırabilir, live restore'u etkinleştirebilir/devre dışı bırakabilir, güvenlik seçeneklerini (seccomp, apparmor) varsayılan olarak ayarlayabilirsiniz.
*   **Yetkilendirme Eklentileri (Authorization Plugins):** Docker Engine API'sine yapılan istekleri daha granüler bir şekilde kontrol etmek için yetkilendirme eklentileri kullanılabilir. Bu eklentiler, hangi kullanıcının/servisin hangi Docker işlemlerini (konteyner başlatma, imaj silme vb.) yapabileceğini belirleyen politikalar uygulayabilir. Open Policy Agent (OPA) gibi araçlarla entegrasyon mümkündür.

# Monitoring ve Logging

## Neden Önemli?

Dağıtılmış ve dinamik konteyner ortamlarında, sistemin ve üzerinde çalışan uygulamaların sağlığını, performansını ve davranışını anlamak kritik öneme sahiptir. Monitoring (izleme - genellikle metrikler ve olaylar) ve Logging (kayıt tutma - genellikle olayların detaylı metin kayıtları):

*   **Sorun Tespiti ve Uyarı (Alerting):** Hataları, çökmeleri, performans düşüşlerini veya anormal davranışları proaktif olarak (hatta gerçekleşmeden önce trendlere bakarak) tespit etmenizi ve ilgili ekipleri otomatik olarak uyarmanızı sağlar.
*   **Hata Ayıklama (Debugging) ve Kök Neden Analizi (RCA):** Bir sorun oluştuğunda, sorunun kaynağını bulmak için gerekli olan detaylı bilgileri (loglar, metrikler, olaylar) sağlar. "Neden yavaşladı?", "Hangi servis hata verdi?", "Ne zaman başladı?" gibi sorulara cevap bulmaya yardımcı olur.
*   **Performans Optimizasyonu:** Sistemdeki darboğazları (CPU, bellek, ağ, disk G/Ç, uygulama içi darboğazlar) belirlemenize ve kaynak kullanımını (limitler, replika sayısı) optimize etmenize olanak tanır.
*   **Kapasite Planlaması:** Kaynak kullanım trendlerini analiz ederek gelecekteki ihtiyaçları tahmin etmenize yardımcı olur.
*   **Güvenlik Denetimi ve Analizi:** Şüpheli aktiviteleri, yetkisiz erişim denemelerini veya güvenlik olaylarını tespit etmek ve analiz etmek için loglar kritik öneme sahiptir.
*   **Sistem Davranışını Anlama:** Normal çalışma koşullarında sistemin nasıl davrandığını anlamak, anormallikleri tespit etmeyi kolaylaştırır.

Konteynerlerin kısa ömürlü (ephemeral) doğası ve sayılarının hızla artıp azalabilmesi, geleneksel izleme ve loglama yöntemlerini yetersiz kılar. Bu nedenle konteyner ortamları için özel olarak tasarlanmış merkezi ve dinamik çözümlere ihtiyaç vardır.

## Docker Dahili Araçlar

Docker, temel izleme ve loglama için bazı dahili komutlar sunar:

*   **`docker logs`**: Belirli bir konteynerin standart çıktı (stdout) ve standart hata (stderr) akışını gösterir. Anlık logları veya geçmiş logları almak için kullanılır. (*Detaylar Konteyner Yönetimi bölümünde verildi.*) Logların ne kadar süreyle veya ne kadar boyutta saklanacağı kullanılan logging driver'a bağlıdır (varsayılan `json-file` için sınırlıdır).
*   **`docker stats`**: Çalışan konteynerlerin CPU, RAM (kullanım/limit), Ağ G/Ç, Disk G/Ç (destekleyen storage driver'lar için) gibi temel kaynak kullanım metriklerini gerçek zamanlı olarak bir terminal arayüzünde gösterir. Hızlı bir genel bakış için faydalıdır ancak geçmiş verileri saklamaz veya detaylı analiz sunmaz. (*Detaylar Konteyner Yönetimi bölümünde verildi.*)
*   **`docker events`**: Docker daemon tarafından üretilen olayları (konteyner başlatma/durdurma/çökme, imaj çekme/silme, ağ oluşturma/silme, volume mount/unmount vb.) gerçek zamanlı olarak akış halinde gösterir. Otomasyon, denetim veya anlık bildirimler için kullanılabilir. Filtreleme seçenekleri vardır.
    ```bash
    # Konteyner başlatma ve durdurma olaylarını izle
    docker events --filter 'type=container' --filter 'event=start' --filter 'event=stop'

    # Belirli bir imajla ilgili olayları izle
    docker events --filter 'image=my-app:latest'
    ```
*   **`docker top KONTEYNER`**: Bir konteyner içinde çalışan süreçleri (PID, USER, CPU%, MEM%, COMMAND vb.) listeler (host'taki `ps` komutuna benzer). (*Detaylar Konteyner Yönetimi bölümünde verildi.*)
*   **`docker inspect`**: Konteynerler, imajlar, ağlar, volume'ler hakkında detaylı yapılandırma ve durum bilgisi (IP adresi, portlar, bağlı volume'ler, sağlık durumu, çıkış kodu vb.) sağlar. Sorun gidermede çok değerlidir. (*Detaylar ilgili bölümlerde verildi.*)
*   **Docker Daemon Metrikleri (Experimental / Prometheus):** Docker daemon'ın kendisi, Prometheus formatında detaylı iç metrikler (`engine_daemon_*` gibi) sunacak şekilde yapılandırılabilir (`daemon.json` içinde `"metrics-addr": "0.0.0.0:9323"` ayarı ve `"experimental": true` ile). Bu, daemon'ın kendi performansını (API istekleri, goroutine'ler, dosya tanıtıcıları vb.) ve durumunu izlemek için kullanılır.

Bu dahili araçlar temel ihtiyaçlar, hızlı kontroller ve manuel sorun giderme için faydalıdır ancak büyük ölçekli, otomatikleştirilmiş veya üretim ortamları için genellikle yeterli değildir. Geçmiş verileri saklama, merkezi toplama, korelasyon, gelişmiş görselleştirme ve otomatik uyarı gibi yetenekler eksiktir.

## Logging Mimarileri ve Stratejileri

**En İyi Pratik: Logları stdout/stderr'a Yönlendirin**
Konteynerleştirilmiş uygulamalar için en yaygın ve önerilen loglama yaklaşımı, uygulama loglarını dosyalara yazmak yerine doğrudan standart çıktı (`stdout` - genellikle bilgi/debug mesajları için) ve standart hata (`stderr` - genellikle hata/warning mesajları için) akışlarına yazdırmaktır. Docker, bu akışları otomatik olarak yakalar ve yapılandırılan logging driver aracılığıyla yönetir. Bu yaklaşım:

*   Uygulama kodunu basitleştirir (log rotasyonu, dosya yönetimi gibi işlerle uğraşmaz).
*   Logların Docker ekosistemiyle doğal entegrasyonunu sağlar.
*   Merkezi loglama çözümlerinin logları toplamasını kolaylaştırır.

Birçok modern framework ve kütüphane bu şekilde loglamayı destekler veya kolayca yapılandırılabilir.

**Docker Logging Drivers (Sürücüleri):**
Docker, konteynerlerden gelen stdout/stderr loglarını nasıl işleyeceğini ve nereye göndereceğini belirleyen farklı loglama sürücüleri sunar. Varsayılan sürücü genellikle `json-file`'dır (logları host üzerinde JSON formatında dosyalara yazar). Sürücü, Docker daemon genelinde (`daemon.json` içinde `"log-driver": "..."` ve `"log-opts": {...}`) veya her konteyner için ayrı ayrı (`docker run --log-driver <driver> --log-opt <key>=<value> ...`) yapılandırılabilir. Konteyner bazlı ayar daemon ayarını ezer.

Bazı popüler logging sürücüleri:

*   **`json-file` (Varsayılan):** Logları host üzerinde (genellikle `/var/lib/docker/containers/<container_id>/<container_id>-json.log`) JSON dosyalarına yazar. Basittir ancak merkezi loglama için genellikle host üzerine bir ajan kurmak gerekir. Disk alanı yönetimi önemlidir; `max-size` (örn: "10m") ve `max-file` (örn: "3") seçenekleri ile log rotasyonu ve saklama limiti yapılandırılmalıdır, aksi takdirde disk dolabilir. `docker logs` komutu bu sürücüyle çalışır.
*   **`journald`:** Logları host sisteminin systemd journal'ına gönderir (sadece systemd kullanan Linux host'larda). `journalctl` komutu ile kolayca sorgulanabilir ve filtrelenebilir. Merkezi loglama için journald'den logları çeken bir ajan (örn: fluentd, promtail) kullanılabilir. `docker logs` komutu bu sürücüyle çalışır.
*   **`syslog`:** Logları standart syslog protokolü üzerinden host'taki veya (daha yaygın olarak) uzaktaki bir merkezi syslog sunucusuna (örn: Rsyslog, Syslog-ng) veya syslog uyumlu bir log yönetim sistemine gönderir. Adres (`syslog-address`), format (`syslog-format`) gibi seçenekleri vardır. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`fluentd`:** Logları popüler açık kaynaklı veri toplayıcı Fluentd'ye (genellikle TCP veya UDP üzerinden) iletir. Fluentd, logları işleyip (parsing, filtering, enriching) Elasticsearch, Kafka, S3, MongoDB gibi birçok farklı hedefe gönderebilen çok esnek bir araçtır. Merkezi loglama için güçlü bir seçenektir. `fluentd-address`, `tag` gibi seçenekleri vardır. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`gelf` (Graylog Extended Log Format):** Logları Graylog veya Logstash gibi GELF uyumlu log yönetim sistemlerine UDP veya TCP üzerinden gönderir. Yapılandırılmış loglar için tasarlanmıştır. `gelf-address`, `tag` gibi seçenekleri vardır. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`awslogs`:** Logları doğrudan Amazon CloudWatch Logs'a gönderir. AWS ortamlarında merkezi loglama için kullanışlı bir entegrasyondur. IAM izinleri, log grubu (`awslogs-group`), log stream (`awslogs-stream`) ve bölge (`awslogs-region`) gibi yapılandırmalar gerektirir. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`gcplogs`:** Logları Google Cloud Logging'e (eski adıyla Stackdriver) gönderir. GCP ortamları için benzer bir entegrasyon sunar. Proje ID, log etiketleri gibi ayarlar gerektirir. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`splunk`:** Logları Splunk Enterprise veya Splunk Cloud'a HTTP Event Collector (HEC) üzerinden gönderir. Splunk token'ı (`splunk-token`), URL (`splunk-url`) gibi yapılandırmalar gerektirir. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`etwlogs`:** Logları Windows'taki Event Tracing for Windows (ETW) sistemine gönderir. Sadece Windows konteynerleri için geçerlidir. `docker logs` komutu bu sürücüyle **çalışmaz**.
*   **`none`:** Loglamayı tamamen devre dışı bırakır. Konteynerden hiçbir log toplanmaz ve saklanmaz. Performansın çok kritik olduğu veya logların hiçbir şekilde gerekli olmadığı özel durumlar için kullanılabilir. `docker logs` komutu bu sürücüyle doğal olarak hiçbir şey göstermez.

**Not:** `json-file` ve `journald` dışındaki çoğu loglama sürücüsü kullanıldığında, `docker logs` komutu artık o konteynerin loglarını gösteremez, çünkü loglar doğrudan Docker daemon tarafından yönetilmeyip harici bir sisteme gönderilir.

**Merkezi Log Yönetimi:**
Üretim ortamlarında veya çok sayıda konteynerin olduğu durumlarda, tüm konteynerlerden ve host'lardan gelen logların tek bir merkezi yerde toplanması, saklanması, aranabilir hale getirilmesi, görselleştirilmesi ve analiz edilmesi şiddetle önerilir. Popüler merkezi loglama yığınları (stacks):

*   **ELK Stack / Elastic Stack:** Elasticsearch (dağıtık arama ve analiz motoru), Logstash (log toplama, işleme, filtreleme ve yönlendirme sunucusu) ve Kibana (görselleştirme ve dashboard arayüzü). Genellikle Filebeat (hafif log gönderici ajan) ile birlikte kullanılır (EFK yerine artık yaygın olarak Beats+Elasticsearch+Kibana). Çok güçlü ve esnektir ancak kaynak ihtiyacı yüksek olabilir.
*   **EFK Stack:** Elasticsearch, Fluentd (Logstash'a alternatif, daha hafif ve eklenti tabanlı log toplayıcı/yönlendirici) ve Kibana. Özellikle Kubernetes ortamlarında popülerdir.
*   **Loki + Grafana + Promtail:** Grafana Labs tarafından geliştirilen, Prometheus ile benzer etiket tabanlı bir yaklaşıma sahip, daha basit ve depolama açısından (özellikle indeksleme konusunda) daha verimli olabilen bir loglama çözümüdür. Promtail logları toplar ve etiketler ekleyerek Loki'ye gönderir, Loki logları saklar ve indeksler (metin içeriği yerine sadece etiketleri), Grafana ise hem metrikleri (Prometheus'tan) hem de logları (Loki'den) aynı arayüzde görselleştirir ve sorgular (LogQL).
*   **Graylog:** Açık kaynaklı (ve ticari sürümlü) başka bir popüler log yönetim platformudur. GELF formatını destekler ve kendi arama, görselleştirme, uyarı yeteneklerini sunar.

Bu sistemlerde genellikle host üzerine bir log ajanı (Filebeat, Fluentd, Promtail vb.) kurulur (genellikle kendisi de bir Docker konteyneri olarak veya DaemonSet olarak Kubernetes'te). Bu ajanlar, Docker log dosyalarını (`json-file` sürücüsü kullanılıyorsa) veya doğrudan Docker daemon API'sini dinleyerek (bazı sürücülerle entegrasyonları varsa) logları toplar, işler (parse etme, etiket ekleme) ve merkezi log sunucusuna (Elasticsearch, Loki, Graylog vb.) gönderir.

## Monitoring Araçları ve Yaklaşımları

Konteyner ortamlarını izlemek için genellikle metrik tabanlı bir yaklaşım kullanılır. Amaç, sistemin ve uygulamaların performansını, kaynak kullanımını ve sağlığını sayısal verilerle takip etmektir.

**Metrik Kaynakları:**

*   **Konteyner Metrikleri:** Her bir konteynerin CPU kullanımı, bellek kullanımı (rss, cache, limitler), ağ trafiği (gönderilen/alınan byte/paket), disk G/Ç (okuma/yazma byte/operasyon) gibi işletim sistemi seviyesindeki metrikleri.
*   **Host Metrikleri:** Konteynerlerin çalıştığı ana makinelerin (node'ların) genel sağlık durumu ve kaynak kullanımı (toplam CPU, RAM, Disk alanı/IOPS, Ağ bant genişliği, yük ortalaması vb.).
*   **Docker Daemon Metrikleri:** Docker Engine'in kendi iç durumu ve performansı (çalışan/duran konteyner sayısı, API performansı, build sayıları vb.).
*   **Uygulama Metrikleri (İş/APM Metrikleri):** Konteyner içinde çalışan uygulamanın kendi ürettiği iş mantığına özel metrikler. Bunlar genellikle en değerli metriklerdir. Örnekler: saniyedeki istek sayısı (RPS), istek gecikme süreleri (latency - ortalama, p95, p99), hata oranları (HTTP 5xx, 4xx), kuyruk uzunlukları, veritabanı bağlantı havuzu kullanımı, işlenen mesaj sayısı, aktif kullanıcı sayısı vb. Bunlar genellikle uygulamanın koduna eklenen istemci kütüphaneleri (Prometheus client library, OpenTelemetry SDK, APM ajanları) aracılığıyla sağlanır ve belirli bir endpoint (`/metrics` gibi) üzerinden sunulur.

**Popüler Monitoring Araçları:**
Genellikle bir arada kullanılan ve birbirini tamamlayan araçlardan oluşan bir ekosistem kurulur:

*   **cAdvisor (Container Advisor):** Google tarafından geliştirilen açık kaynaklı bir araçtır. Çalıştığı host üzerindeki tüm çalışan konteynerler hakkında otomatik olarak kaynak kullanım metriklerini (CPU, bellek, dosya sistemi, ağ) toplar ve genellikle bir web arayüzü veya (daha önemlisi) Prometheus formatında (`/metrics` endpoint'i üzerinden) sunar. Docker daemon içine entegre edilebilir veya (daha yaygın olarak) her host üzerinde ayrı bir konteyner olarak çalıştırılır.
*   **Node Exporter:** Prometheus ekosisteminin bir parçasıdır ve en yaygın kullanılan exporter'lardan biridir. Host makinesinin (node) donanım ve işletim sistemi seviyesindeki metriklerini (CPU, disk, ağ, bellek, dosya sistemi, yük ortalaması, sistem saati vb.) toplar ve Prometheus'un çekebileceği (scrape) bir formatta (`/metrics` endpoint'i üzerinden, genellikle 9100 portunda) sunar. Genellikle her host üzerinde bir konteyner veya sistem servisi olarak çalıştırılır.
*   **Prometheus:** CNCF (Cloud Native Computing Foundation) altında geliştirilen, açık kaynaklı, metrik toplama, saklama ve sorgulama sistemidir. Orkestrasyon ve konteyner dünyasında fiili standart haline gelmiştir. Belirlenen hedeflerden (Node Exporter, cAdvisor, uygulama `/metrics` endpoint'leri, diğer exporter'lar) HTTP üzerinden periyodik olarak metrikleri çeker (pull modeli), verimli bir zaman serisi veritabanında (TSDB) saklar ve güçlü bir sorgu dili (PromQL) ile bu verileri analiz etme ve sorgulama imkanı sunar. Ayrıca tanımlanan kurallara göre uyarı (alerting) tetikleme yeteneğine sahiptir.
*   **Grafana:** Açık kaynaklı, çok popüler bir görselleştirme ve dashboard platformudur. Prometheus, Loki, Elasticsearch, InfluxDB, MySQL, PostgreSQL gibi birçok farklı veri kaynağından metrikleri, logları ve diğer verileri alarak interaktif, özelleştirilebilir ve paylaşılabilir dashboard'lar oluşturmayı sağlar. Metrikleri anlamlı grafiklere, tablolara, göstergelere dönüştürmek ve zaman içindeki trendleri görselleştirmek için kullanılır.
*   **Alertmanager:** Prometheus ile entegre çalışan bir uyarı (alert) yönetim aracıdır. Prometheus tarafından tanımlanan uyarı kuralları tetiklendiğinde gönderilen uyarıları alır, bunları gruplar (grouping), yinelenenleri engeller (deduplication), sessize alır (silencing) ve yapılandırılmış rotalara göre e-posta, Slack, PagerDuty, OpsGenie gibi farklı bildirim kanallarına yönlendirir.

**Monitoring Mimarisi Örneği (Prometheus + Grafana):**
1.  Her Docker host'una (node) **Node Exporter** konteyneri kurulur (veya servis olarak çalıştırılır) ve 9100 portundan metrik sunar.
2.  Her Docker host'una **cAdvisor** konteyneri kurulur (veya Docker daemon'ın kendi metrik endpoint'i kullanılır) ve konteyner metriklerini sunar (genellikle 8080 veya farklı bir portta `/metrics`).
3.  Uygulama konteynerleri, kendi iş metriklerini (örn: Prometheus istemci kütüphanesi kullanarak) `/metrics` gibi bir endpoint'te Prometheus formatında sunacak şekilde geliştirilir ve yapılandırılır.
4.  **Prometheus** sunucusu (genellikle ayrı bir host'ta veya konteyner olarak çalışır), yapılandırma dosyasında belirtilen hedefleri (tüm Node Exporter'lar, cAdvisor'lar, uygulama `/metrics` endpoint'leri) düzenli aralıklarla (scrape interval) tarayarak metrikleri toplar ve kendi zaman serisi veritabanında saklar. Servis keşfi (service discovery) mekanizmaları (örn: Swarm veya Kubernetes API ile entegrasyon) ile hedeflerin dinamik olarak bulunması sağlanabilir.
5.  **Grafana**, veri kaynağı (datasource) olarak Prometheus'u kullanacak şekilde yapılandırılır. Kullanıcılar Grafana arayüzünden PromQL sorguları kullanarak dashboard'lar oluşturur ve host, konteyner, Docker daemon ve uygulama metriklerini görselleştirir.
6.  Prometheus üzerinde kritik durumlar (yüksek CPU/bellek kullanımı, disk doluluğu, servis erişilemezliği, yüksek hata oranı vb.) için PromQL tabanlı uyarı kuralları (`alerting rules`) tanımlanır. Bu kurallar tetiklendiğinde **Alertmanager**'a gönderilir.
7.  **Alertmanager**, gelen uyarıları yapılandırılmış kurallara göre işler (gruplama, sessize alma, yönlendirme) ve ilgili kişilere/ekiplere e-posta, Slack mesajı, PagerDuty çağrısı vb. yoluyla bildirim gönderir.

# CI/CD Pipeline'larında Docker Kullanımı

## Neden Docker CI/CD İçin İdealdir?

Sürekli Entegrasyon (Continuous Integration - CI) ve Sürekli Dağıtım/Teslimat (Continuous Deployment/Delivery - CD), modern yazılım geliştirmenin temel pratikleridir. Amaç, kod değişikliklerini sık sık entegre etmek, otomatik olarak test etmek ve güvenilir bir şekilde üretime veya staging ortamlarına dağıtmaktır. Docker, bu CI/CD süreçlerini önemli ölçüde iyileştirir, hızlandırır ve daha güvenilir hale getirir:

*   **Tutarlı ve Tekrarlanabilir Ortamlar:** Docker, geliştiricinin lokal makinesi, CI sunucusu, test ortamı ve üretim ortamı arasında tamamen aynı veya çok benzer çalışma ortamlarının kullanılmasını sağlar. Dockerfile ortamı kod olarak tanımlar. Bu, "benim makinemde çalışıyordu ama CI sunucusunda/üretimde patladı" gibi can sıkıcı ve zaman kaybettiren sorunları büyük ölçüde ortadan kaldırır. Build ve testler her zaman öngörülebilir, izole ve temiz bir ortamda çalışır.
*   **Bağımlılık Yönetimi Kolaylığı:** Uygulamanın ve build/test süreçlerinin ihtiyaç duyduğu tüm araçlar (belirli bir dil sürümü, derleyiciler, kütüphaneler, veritabanları, test framework'leri, lint araçları vb.) Docker imajına dahil edilebilir veya CI/CD sırasında Docker Compose gibi araçlarla yan servisler olarak kolayca ayağa kaldırılabilir. Bu, CI sunucusuna veya farklı ortamlara manuel olarak karmaşık bağımlılıklar kurma ve yönetme ihtiyacını ortadan kaldırır veya büyük ölçüde azaltır.
*   **Standart Paketleme ve Dağıtım Birimi (Artefakt):** Docker imajları, uygulamanın kodunu, çalışma zamanını, sistem araçlarını, kütüphanelerini ve diğer bağımlılıklarını içeren, taşınabilir ve kendi kendine yeterli standart bir paketleme formatı sunar. Bu imaj, CI sürecinde oluşturulan ve test edilen ana artefakt olur ve tüm dağıtım aşamalarında (test, staging, production) tutarlı bir şekilde kullanılır.
*   **Hızlı Build ve Test Döngüleri:** Docker'ın katmanlı dosya sistemi ve build cache mekanizmaları, Dockerfile'da değişiklik olmayan katmanların yeniden kullanılmasını sağlayarak imaj build sürelerini önemli ölçüde kısaltabilir (özellikle Dockerfile doğru yapılandırıldıysa). Testler için gerekli olan veritabanı, mesaj kuyruğu gibi harici servisler Docker konteynerleri olarak saniyeler içinde başlatılıp test bitiminde kaldırılabilir, bu da test süreçlerini hızlandırır.
*   **Kolay ve Güvenilir Dağıtım (Deployment):** CI sürecinde başarıyla test edilen ve bir Docker Registry'ye (Docker Hub, AWS ECR, Google GCR, Azure ACR, GitLab Registry vb.) yüklenen (push) Docker imajının dağıtımı, bu imajın hedef ortama (staging, production sunucuları veya Kubernetes/Swarm kümesi) çekilip (pull) çalıştırılmasından ibarettir. Bu süreç otomatikleştirmesi kolaydır ve tutarlıdır. Geri alma (rollback) işlemi de genellikle önceki stabil imaj etiketine sahip konteynerleri çalıştırmak kadar basittir.
*   **Altyapıyı Kod Olarak Yönetme (Infrastructure as Code - IaC):** Dockerfile ve docker-compose.yml gibi dosyalar, uygulamanın çalışacağı ortamı ve (Compose ile) basit altyapı tanımlarını kod olarak ifade eder. Bu dosyalar versiyon kontrol sisteminde (Git) kodla birlikte yönetilebilir, değişiklikler incelenebilir (code review), geçmişe dönük takip edilebilir ve tekrarlanabilir build/deploy süreçleri garanti altına alınır.

## Tipik CI/CD Akışı (Docker ile)

Docker kullanan bir CI/CD pipeline (iş akışı) genellikle şu adımları içerir (kullanılan araca ve projenin karmaşıklığına göre değişebilir):

1.  **Kod Değişikliği ve Tetikleme (Trigger):** Geliştirici kodu değiştirir ve Git deposuna push eder (örn: feature branch'ine veya `main`/`master`'a merge eder) veya bir Pull Request/Merge Request açar. Bu olay (webhook veya polling ile) CI/CD platformunu (Jenkins, GitLab CI, GitHub Actions, CircleCI, Travis CI, Azure DevOps vb.) tetikler.
2.  **Kod İndirme (Checkout):** CI sunucusu (veya agent/runner), ilgili kod deposunun pipeline'ı tetikleyen son halini (belirli commit/branch) kendi çalışma alanına çeker.
3.  **Linting ve Statik Analiz (Code Quality):** Kod kalitesini, stilini ve potansiyel hataları kontrol etmek için lint araçları (örn: ESLint, Pylint, Checkstyle, RuboCop) ve statik analiz araçları (örn: SonarQube, CodeQL) çalıştırılır. Bu adım genellikle ilgili dil/araç için hazırlanmış bir Docker konteyneri içinde veya doğrudan CI runner üzerinde yapılır. Başarısız olursa pipeline durur.
4.  **Birim Testleri (Unit Tests):** Uygulamanın küçük, izole birimlerinin (fonksiyonlar, sınıflar, modüller) doğruluğunu test eden otomatik testler çalıştırılır. Bu testler genellikle harici bağımlılık (veritabanı, API) gerektirmez ve uygulamanın kendi Docker imajı içinde (`docker build` içinde bir aşama olarak veya build sonrası `docker run` ile) veya özel bir test ortamı sağlayan bir Docker imajı içinde çalıştırılabilir. Başarısız olursa pipeline durur.
5.  **Docker İmajı Oluşturma (Build):** Birim testleri başarılı olursa, uygulamanın `Dockerfile`'ı kullanılarak yeni bir Docker imajı oluşturulur (`docker build`). İmaj genellikle pipeline'ı tetikleyen commit hash'i, branch adı, tag veya sürüm numarası gibi benzersiz ve anlamlı bir etiketle (tag) etiketlenir (örn: `registry.example.com/my-app:latest`, `registry.example.com/my-app:1.2.0-rc1`, `registry.example.com/my-app:feature-x-abc1234`). Cache kullanımı (`--cache-from`) build süresini optimize etmek için önemlidir.
6.  **İmaj Tarama (Scan):** (Önemli Güvenlik Adımı) Oluşturulan Docker imajı, bilinen güvenlik açıklarına (CVE'ler) ve potansiyel yanlış yapılandırmalara karşı Trivy, Docker Scout, Grype, Snyk gibi araçlarla taranır. Eğer belirlenen eşik değerini (severity level) aşan kritik açıklar bulunursa pipeline durdurulabilir ve geliştiriciye bildirim gönderilebilir.
7.  **Docker İmajını Yayınlama (Push):** Güvenlik taramasından geçen ve testleri başarılı olan imaj, merkezi bir Docker Registry'ye (Docker Hub, AWS ECR, Google GCR, Azure ACR, GitLab Container Registry, Harbor vb.) yüklenir (`docker push`). Bu registry, imajların saklandığı ve dağıtım için çekileceği yerdir. Genellikle hem benzersiz etiket (commit hash) hem de daha genel bir etiket (`latest`, branch adı) ile push edilir.
8.  **Entegrasyon/Kabul Testleri (Integration/Acceptance Tests):** Uygulamanın diğer servislerle (veritabanı, harici API'ler, mesaj kuyrukları) doğru bir şekilde entegre olup olmadığını veya belirli kullanıcı senaryolarını (end-to-end tests) karşılayıp karşılamadığını test etmek için daha kapsamlı otomatik testler çalıştırılır. Bu adım genellikle Docker Compose veya bir test orkestrasyon aracı kullanılarak uygulamanın (yeni push edilen imajla) ve bağımlı servislerin (veritabanı, Redis vb. için standart veya özel imajlarla) geçici bir ortamda (genellikle CI runner üzerinde veya ayrı bir test kümesinde) ayağa kaldırılmasıyla yapılır. Başarısız olursa pipeline durur.
9.  **Dağıtım (Deployment):** Tüm önceki adımlar başarılı olursa, yeni Docker imajı hedef ortama (Staging/UAT - Kullanıcı Kabul Testi, veya doğrudan Production) dağıtılır. Bu işlem, hedefin ne olduğuna bağlı olarak değişir:
    *   **Basit Ortamlar (Tek Sunucu):** Hedef sunucuya SSH ile bağlanıp `docker pull <yeni_imaj>`, `docker stop <eski_konteyner>`, `docker rm <eski_konteyner>` ve `docker run <yeni_imaj>` (veya `docker compose down && docker compose up -d`) komutlarını çalıştırmak.
    *   **Orkestrasyon Ortamları (Kubernetes, Swarm):** Orkestrasyon aracına ilgili Deployment/Service tanımını yeni imaj etiketiyle güncelleme komutu göndermek (`kubectl set image deployment/...`, `helm upgrade ...`, `docker service update ...`, `docker stack deploy ...`). Orkestratör, rolling update gibi stratejilerle güncellemeyi yönetir.
    Dağıtım genellikle önce Staging ortamına yapılır, manuel/otomatik testlerden sonra onay alınarak Production'a yapılır (Continuous Delivery). Veya her başarılı build doğrudan Production'a gidebilir (Continuous Deployment - daha riskli, yüksek otomasyon ve güven gerektirir).
10. **Dağıtım Sonrası Kontroller (Post-Deployment Checks / Smoke Tests):** Dağıtımın başarılı olduğunu ve uygulamanın temel işlevlerinin çalıştığını doğrulamak için basit otomatik kontroller (sağlık kontrolü endpoint'ini çağırma, ana sayfayı kontrol etme vb.) çalıştırılır. Başarısız olursa otomatik geri alma (rollback) tetiklenebilir.

## Docker ve Popüler CI/CD Araçları

*   **Jenkins:** Çok esnek, yaygın kullanılan ve eklenti tabanlı açık kaynaklı bir CI/CD sunucusudur. Jenkins Pipeline (`Jenkinsfile` - Groovy tabanlı) kullanarak Docker build, tag, push, run, exec gibi adımlar programatik olarak tanımlanabilir. Jenkins, Docker daemon ile doğrudan soket üzerinden veya TCP ile etkileşime geçebilir (güvenlik dikkat gerektirir) veya Jenkins agent'ları (build işlemini yapan worker'lar) dinamik olarak Docker konteynerleri içinde çalıştırılabilir (`agent { docker { image '...' } }`). Docker, Docker Pipeline, Docker Compose Build Step, Kubernetes gibi birçok eklentisi mevcuttur.
    **Örnek Jenkinsfile (Declarative Pipeline):**
    ```groovy
      pipeline {
          agent any // Veya agent { label 'docker-host' } veya agent { docker { ... } }

          environment {
              REGISTRY = 'your-registry.example.com/your-app'
              // Docker Hub için: REGISTRY = 'yourdockerhubuser/your-app'
              REGISTRY_CREDENTIALS_ID = 'your-registry-credentials-id' // Jenkins'te tanımlı credential ID
          }

          stages {
              stage('Checkout') {
                  steps {
                      checkout scm
                  }
              }
              stage('Lint & Test') {
                  // Bu adımlar için uygun bir Docker imajı kullanılabilir
                  // agent { docker { image 'node:18' } }
                  steps {
                      sh 'npm install'
                      sh 'npm run lint'
                      sh 'npm test'
                  }
              }
              stage('Build Docker Image') {
                  steps {
                      script {
                          // Commit hash veya build numarası ile etiketle
                          def imageTag = env.BUILD_TAG // Jenkins'in verdiği etiket (job_name-build_number)
                          // Veya commit hash: sh(script: 'git rev-parse --short HEAD', returnStdout: true).trim()
                          docker.build("${REGISTRY}:${imageTag}", ".")
                      }
                  }
              }
              // stage('Scan Docker Image') { ... Trivy, Snyk vb. çalıştırma ... }
              stage('Push Docker Image') {
                  steps {
                      script {
                          def imageTag = env.BUILD_TAG
                          docker.withRegistry("https://${your-registry.example.com}", REGISTRY_CREDENTIALS_ID) {
                              docker.image("${REGISTRY}:${imageTag}").push()
                              // Opsiyonel: 'latest' veya branch adıyla da push et
                              if (env.BRANCH_NAME == 'main') {
                                 docker.image("${REGISTRY}:${imageTag}").push('latest')
                              }
                          }
                      }
                  }
              }
              stage('Deploy to Staging') {
                  when { branch 'main' } // Sadece main branch'inde çalışsın
                  steps {
                      // Deploy adımları (örn: ssh ile remote docker komutları, kubectl apply, helm upgrade vb.)
                      echo "Deploying ${REGISTRY}:${env.BUILD_TAG} to Staging..."
                      // sh 'ssh staging-server "docker pull ${REGISTRY}:${env.BUILD_TAG} && docker-compose up -d --force-recreate web"'
                  }
              }
              // stage('Deploy to Production') { ... }
          }
          post {
              always {
                  // Pipeline bitince yapılacaklar (temizlik vb.)
                  echo 'Pipeline finished.'
              }
              success {
                  // Başarılı bitince bildirim vs.
              }
              failure {
                  // Hata durumunda bildirim vs.
              }
          }
      }
    ```

*   **GitLab CI/CD:** GitLab ile sıkı entegre gelen, güçlü ve kullanımı kolay bir CI/CD çözümüdür. Pipeline'lar projenin kök dizinindeki `.gitlab-ci.yml` dosyası ile YAML formatında tanımlanır. Her iş (job), belirtilen bir Docker imajı (`image:` anahtar kelimesi) içinde çalıştırılır. İşler için gerekli yan servisler (veritabanı, Redis vb.) `services:` anahtar kelimesi ile kolayca tanımlanabilir ve job konteyneri ile aynı ağda çalışır. Docker komutlarını çalıştırmak için genellikle `docker:stable` imajı ve Docker-in-Docker (`docker:stable-dind`) servisi kullanılır (veya runner'ın Docker soketine erişimi sağlanır). GitLab'ın kendi entegre ve ücretsiz Docker Container Registry'si de bulunur, bu da imaj yönetimini basitleştirir.
    **Örnek .gitlab-ci.yml:**
    ```yaml
      stages:
        - build
        - test
        - scan # Güvenlik taraması için ayrı stage
        - publish
        - deploy_staging
        - deploy_production

      variables:
        # CI_REGISTRY_IMAGE GitLab tarafından otomatik sağlanır (registry.gitlab.com/user/project)
        # CI_COMMIT_REF_SLUG branch/tag adının URL uyumlu hali
        # CI_COMMIT_SHORT_SHA kısa commit hash
        IMAGE_TAG_COMMIT: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA
        IMAGE_TAG_LATEST: $CI_REGISTRY_IMAGE:latest
        DOCKER_TLS_CERTDIR: "/certs" # Docker-in-Docker için

      default:
        tags: # Kullanılacak GitLab Runner etiketleri (örn: docker, linux)
          - docker

      build_job:
        stage: build
        image: node:18-alpine # Build için Node imajı
        script:
          - echo "Building the app..."
          - npm install
          - npm run build
        artifacts: # Build çıktılarını sonraki aşamalara aktar
          paths:
            - dist/
          expire_in: 1 hour # İsteğe bağlı

      test_job:
        stage: test
        image: node:18-alpine
        services: # Test için PostgreSQL servisi
          - name: postgres:14-alpine
            alias: db-test # Servise bu isimle erişilebilir
        variables:
          POSTGRES_DB: testdb
          POSTGRES_USER: testuser
          POSTGRES_PASSWORD: testpassword
          DATABASE_URL: "postgres://testuser:testpassword@db-test:5432/testdb"
        script:
          - echo "Running tests..."
          - npm install
          - npm test

      # Güvenlik Taraması (Trivy Örneği)
      scan_image_job:
        stage: scan
        image: # Docker komutları ve Trivy için
          name: alpine:latest # Veya daha uygun bir imaj
        services:
          - docker:20.10-dind
        variables:
          # TRIVY_VERSION, TRIVY_SEVERITY vb. ayarlanabilir
        before_script:
          # Docker'a ve GitLab Registry'ye login (eğer build publish'ten önce yapılıyorsa)
          # - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
          # Trivy'yi kur
          - apk add --no-cache curl docker-cli bash
          - curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b /usr/local/bin v0.30.4
          # Önceki aşamada build edilen imajı yükle (eğer publish edilmediyse)
          # VEYA publish edilmişse pull et: docker pull $IMAGE_TAG_COMMIT
        script:
          - echo "Scanning image $IMAGE_TAG_COMMIT..."
          # Örnek: docker build -t $IMAGE_TAG_COMMIT . # Eğer build bu aşamada yapılacaksa
          - trivy image --exit-code 1 --severity HIGH,CRITICAL $IMAGE_TAG_COMMIT
        needs: [build_job] # Build işinden sonra çalışır (eğer publish öncesi scan ise)

      publish_job:
        stage: publish
        image: docker:20.10
        services:
          - docker:20.10-dind
        before_script:
          - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
        script:
          - echo "Building and pushing image..."
          - docker build -t $IMAGE_TAG_COMMIT .
          - docker push $IMAGE_TAG_COMMIT
          # Sadece default branch (main/master) ise latest etiketini de push et
          - |
            if [ "$CI_COMMIT_BRANCH" == "$CI_DEFAULT_BRANCH" ]; then
              docker tag $IMAGE_TAG_COMMIT $IMAGE_TAG_LATEST
              docker push $IMAGE_TAG_LATEST
            fi
        needs: [build_job, test_job] # Scan de eklenebilir: needs: [build_job, test_job, scan_image_job]

      deploy_staging_job:
        stage: deploy_staging
        image: # kubectl, helm veya ssh gibi dağıtım araçlarını içeren imaj
          name: alpine/k8s:1.24.4
        script:
          - echo "Deploying to staging..."
          # - kubectl config set-context ...
          # - kubectl set image deployment/my-app my-app=$IMAGE_TAG_COMMIT -n staging
          # Veya: helm upgrade --install my-app ./charts/my-app --namespace staging --set image.tag=$CI_COMMIT_SHORT_SHA
        environment: # GitLab Environment tanımlaması
          name: staging
          url: https://staging.example.com
        only: # Sadece main/master branch'inden tetiklenince çalışsın
          - main
          - master
        needs: [publish_job]

      deploy_production_job:
        stage: deploy_production
        # ... Staging'e benzer deploy script'leri ...
        script:
          - echo "Deploying to production..."
        environment:
          name: production
          url: https://example.com
        when: manual # Sadece manuel olarak tetiklenince çalışsın (güvenlik önlemi)
        only:
          - main
          - master
        needs: [deploy_staging_job] # Staging başarılı olduktan sonra
    ```

*   **GitHub Actions:** GitHub ile sıkı entegre, olay tabanlı (event-driven) bir CI/CD platformudur. İş akışları (workflows) projenin `.github/workflows/` dizinindeki YAML dosyaları ile tanımlanır. İşler (jobs) GitHub tarafından sağlanan sanal makinelerde (Ubuntu, Windows, macOS) veya self-hosted runner'larda çalıştırılabilir. Docker işlemleri için (login, setup-buildx, build-push) GitHub ve Docker tarafından sağlanan hazır Action'lar (tekrar kullanılabilir otomasyon birimleri) mevcuttur, bu da Docker pipeline'larını kurmayı çok kolaylaştırır. GitHub Packages, Docker imajları dahil olmak üzere paketler için bir registry olarak kullanılabilir veya Docker Hub, ECR gibi harici registry'ler de rahatlıkla entegre edilebilir. Secret yönetimi için GitHub Secrets kullanılır.
    **Örnek GitHub Actions Workflow:**
    ```yaml
      name: Docker CI/CD Pipeline

      on:
        push:
          branches: [ "main" ] # Main branch'e push yapıldığında
          tags: [ 'v*.*.*' ]   # vX.Y.Z formatında tag push yapıldığında
        pull_request:
          branches: [ "main" ] # Main branch'e PR açıldığında/güncellendiğinde

      env:
        # Docker Hub veya başka bir registry adı
        REGISTRY: docker.io # Docker Hub için
        IMAGE_NAME: ${{ github.repository }} # GitHub repo adı (user/repo)

      jobs:
        lint-and-test:
          name: Lint and Test
          runs-on: ubuntu-latest
          steps:
            - name: Checkout code
              uses: actions/checkout@v4

            - name: Set up Node.js # Örnek Node.js projesi için
              uses: actions/setup-node@v4
              with:
                node-version: '18'
                cache: 'npm' # npm bağımlılıklarını cache'le

            - name: Install dependencies
              run: npm ci

            - name: Run linters
              run: npm run lint

            - name: Run unit tests
              run: npm test

        build-scan-push:
          name: Build, Scan and Push Docker Image
          runs-on: ubuntu-latest
          needs: lint-and-test # Önceki job başarılı olursa çalışır
          # Sadece main'e push veya tag push durumunda çalışsın (PR'da sadece build yapsın)
          if: github.event_name == 'push' || github.event_name == 'pull_request'

          steps:
            - name: Checkout code
              uses: actions/checkout@v4

            - name: Set up QEMU # Multi-platform build için (opsiyonel)
              uses: docker/setup-qemu-action@v3

            - name: Set up Docker Buildx # BuildKit'i kullanmak için
              uses: docker/setup-buildx-action@v3

            - name: Log in to Docker Hub # Sadece push yapılacaksa login ol
              if: github.event_name == 'push'
              uses: docker/login-action@v3
              with:
                username: ${{ secrets.DOCKERHUB_USERNAME }}
                password: ${{ secrets.DOCKERHUB_TOKEN }} # GitHub secrets'tan alınır

            - name: Extract metadata (tags, labels) for Docker
              id: meta
              uses: docker/metadata-action@v5
              with:
                images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
                # Tag oluşturma kuralları:
                # - main branch ise 'latest'
                # - tag push ise tag adı (vX.Y.Z)
                # - Her durumda commit sha
                tags: |
                  type=schedule
                  type=ref,event=branch
                  type=ref,event=pr
                  type=semver,pattern={{version}}
                  type=sha

            - name: Build and push Docker image
              id: build-push
              uses: docker/build-push-action@v5
              with:
                context: .
                # Sadece main'e push veya tag push ise registry'ye push et
                push: ${{ github.event_name == 'push' }}
                tags: ${{ steps.meta.outputs.tags }}
                labels: ${{ steps.meta.outputs.labels }}
                cache-from: type=gha # GitHub Actions cache'ini kullan
                cache-to: type=gha,mode=max # Cache'i yaz

            # Trivy ile güvenlik taraması (örnek)
            - name: Run Trivy vulnerability scanner
              uses: aquasecurity/trivy-action@master
              with:
                # Push edilen imajı kullan (steps.meta.outputs.tags içinden uygun olanı seçmek gerekebilir)
                # Basitlik için build-push adımından çıkan digest'i kullanabiliriz:
                image-ref: '${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}@${{ steps.build-push.outputs.digest }}'
                format: 'table'
                exit-code: '1' # Yüksek/Kritik açık bulunursa pipeline'ı durdur
                ignore-unfixed: true
                vuln-type: 'os,library'
                severity: 'HIGH,CRITICAL'
              # Sadece main'e push veya tag push durumunda çalıştır (opsiyonel)
              if: github.event_name == 'push'

        deploy-staging:
            name: Deploy to Staging
            runs-on: ubuntu-latest
            needs: build-scan-push
            if: github.ref == 'refs/heads/main' && github.event_name == 'push' # Sadece main branch'e push yapıldığında
            environment: # GitHub Environment tanımlaması
              name: staging
              url: https://staging.yourdomain.com
            steps:
              - name: Deploy to staging environment
                # Deploy komutları buraya (örn: kubectl, helm, ssh)
                run: |
                  echo "Deploying image ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ github.sha }} to Staging..."
                  # ssh user@staging-server 'docker pull ... && docker run ...'

        deploy-production:
            name: Deploy to Production
            runs-on: ubuntu-latest
            needs: build-scan-push # Staging'e deploy başarılı olduktan sonra da olabilir: needs: deploy-staging
            if: startsWith(github.ref, 'refs/tags/v') # Sadece vX.Y.Z tag'i push edilince
            environment:
              name: production
              url: https://yourdomain.com
            steps:
              - name: Deploy to production environment
                run: |
                  echo "Deploying image ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ github.ref_name }} to Production..."
                  # ssh user@production-server 'docker pull ... && docker run ...'
    ```

## Dağıtım Stratejileri (Deployment Strategies)

Docker imajları ve orkestrasyon araçları, farklı dağıtım stratejilerini uygulamayı kolaylaştırır:

*   **Recreate (Yeniden Oluştur):** En basit ama kesintiye neden olan yöntem. Eski sürüm tamamen durdurulur (`docker stop/rm` veya `kubectl scale deployment --replicas=0`), sonra yeni sürüm başlatılır (`docker run` veya `kubectl scale deployment --replicas=N`). Uygulama kısa bir süre erişilemez olur. Genellikle geliştirme veya bakım pencereleri için uygundur.
*   **Rolling Update (Kademeli Güncelleme):** Orkestrasyon araçlarının (Swarm, Kubernetes) varsayılan ve en yaygın yöntemidir. Yeni sürüm konteynerleri (veya Pod'ları) yavaş yavaş başlatılırken, eski sürüm konteynerleri aynı anda yavaş yavaş durdurulur. Örneğin, 5 replika varsa, önce 1 eski durdurulur, 1 yeni başlatılır, yeni sağlıklı olunca sonraki 1 eski durdurulur ve bu şekilde devam eder. Kullanıcılar için kesintisiz veya minimum kesintiyle güncelleme sağlar. Güncelleme hızı ve aynı anda kaç tanesinin güncelleneceği yapılandırılabilir (`maxUnavailable`, `maxSurge` - Kubernetes; `parallelism`, `delay` - Swarm).
*   **Blue/Green Deployment (Mavi/Yeşil Dağıtım):** İki tane birebir aynı (veya çok benzer) üretim ortamı (*Mavi* - mevcut aktif sürüm, *Yeşil* - yeni sürüm) hazırlanır. Yeni sürüm tamamen Yeşil ortamına dağıtılır ve orada test edilir (canlı trafik almadan). Tüm testler başarılı olduğunda, yük dengeleyici (load balancer) veya yönlendirici (router) gelen tüm trafiği anında Mavi'den Yeşil'e yönlendirir. Yeşil artık yeni aktif (Mavi) olur, eski Mavi ise yedek (Yeşil) olarak kalır. Sorun olursa trafik hızla eski ortama geri çevrilebilir (rollback çok hızlıdır). Kesintisizdir ancak yaklaşık iki kat kaynak (sunucu, veritabanı vb.) gerektirir.
*   **Canary Deployment (Kanarya Dağıtımı):** Yeni sürüm önce kullanıcıların veya isteklerin çok küçük bir yüzdesine (%1, %5 gibi - "kanarya" grubu) sunulur. Bu sırada hem yeni sürümün hem de eski sürümün metrikleri (hata oranı, gecikme, kaynak kullanımı) ve iş metrikleri yakından izlenir. Eğer kanarya grubunda her şey yolundaysa, yeni sürüm yavaş yavaş daha büyük bir yüzdelik dilime veya sonunda tüm kullanıcılara dağıtılır. Eğer sorun tespit edilirse, yeni sürüm geri çekilir ve sadece eski sürüm çalışmaya devam eder. Riskleri aşamalı olarak azaltmak için kullanılır, özellikle büyük değişikliklerde veya A/B testlerinde faydalıdır. Yük dengeleyicinin veya service mesh'in (Istio, Linkerd gibi) trafiği ağırlıklı olarak yönlendirme yeteneği gerektirir.

Docker ve orkestrasyon araçları, bu stratejileri uygulamak için gerekli olan imaj etiketleme, servis/deployment tanımları, sağlık kontrolleri, yük dengeleme ve trafik yönlendirme mekanizmalarını sağlar.

# Sorun Giderme ve Debugging

Docker ile çalışırken kaçınılmaz olarak sorunlarla karşılaşacaksınız: konteynerlerin başlamaması, ağ bağlantı hataları, izin sorunları, build hataları veya beklenmedik davranışlar. İşte yaygın sorunları teşhis etmek ve çözmek için kullanılabilecek komutlar, stratejiler ve yaygın senaryolar:

## Temel Sorun Giderme Komutları (Tekrar)

Daha önceki bölümlerde detayları verilen ancak sorun gidermede ilk başvurulacak ve sıkça kullanılan komutlar şunlardır:

*   **`docker ps -a`**: Tüm konteynerleri (çalışan ve durmuş) listeler. Bir konteynerin neden hemen durduğunu (`Exited` durumu ve çıkış kodu) veya hiç başlamadığını (`Created` durumu) anlamak için ilk bakılacak yerlerden biridir. `STATUS` sütunu önemlidir.
*   **`docker logs <konteyner_id_veya_adı>`**: Konteynerin standart çıktı (stdout) ve standart hata (stderr) akışlarını gösterir. Uygulama hataları, konfigürasyon sorunları veya başlatma scripti hataları genellikle buradaki mesajlarda bulunur. `-f` ile canlı takip, `--tail N` ile son N satır, `-t` ile zaman damgası ekleme, `--since` ve `--until` ile zaman aralığı belirtme gibi seçenekler çok faydalıdır.
*   **`docker inspect <konteyner|imaj|ağ|volume>`**: İlgili Docker nesnesinin yapılandırması ve anlık durumu hakkında çok detaylı JSON çıktısı verir. Konteynerler için IP adresi, bağlı volume'ler ve mount noktaları, ortam değişkenleri, ağ ayarları, port yönlendirmeleri, sağlık durumu (`State.Health`), çıkış kodu (`State.ExitCode`), hata mesajı (`State.Error`) gibi kritik bilgileri kontrol etmek için kullanılır. `jq` gibi bir araçla çıktıyı filtrelemek ve işlemek kolaylaşır.
*   **`docker exec -it <konteyner> <kabuk>`**: Çalışan bir konteynerin içine girip (`bash`, `sh` veya uygulamanın kullandığı kabuk) interaktif olarak durumu incelemek, dosyalara bakmak (`ls`, `cat`), konfigürasyonu kontrol etmek, ağ bağlantılarını test etmek (`ping`, `curl`, `netstat`, `nslookup`) veya diagnostic komutları çalıştırmak için en etkili yöntemlerden biridir.
*   **`docker stats [<konteyner>...]`**: Çalışan konteynerlerin CPU, RAM (kullanım/limit), Ağ G/Ç, Disk G/Ç (destekleniyorsa) gibi temel kaynak kullanımını canlı olarak gösterir. Performans sorunlarını (aşırı kaynak tüketimi) veya kaynak limitlerine ulaşılıp ulaşılmadığını teşhis etmek için kullanılır.
*   **`docker diff <konteyner>`**: Konteynerin ilk oluşturulduğu andan itibaren dosya sisteminde yapılan değişiklikleri (A: eklenen, C: değiştirilen, D: silinen dosya/dizin) listeler. Beklenmedik dosya değişikliklerini, geçici dosyaların nereye yazıldığını veya konfigürasyonun üzerine yazılıp yazılmadığını anlamak için kullanılabilir.
*   **`docker cp <konteyner>:<konteyner_yolu> <host_yolu>`** veya **`docker cp <host_yolu> <konteyner>:<konteyner_yolu>`**: Konteyner içindeki log dosyalarını, konfigürasyon dosyalarını veya diğer önemli dosyaları daha detaylı incelemek üzere host'a kopyalamak (veya tersi) için kullanılır.
*   **`docker system df [-v]`**: Docker'ın host üzerinde kapladığı disk alanını nesne türlerine göre (imajlar, konteynerler, volume'ler, build cache) özetler. Özellikle "RECLAIMABLE" (geri kazanılabilir) alan miktarını göstererek disk alanı sorunlarını teşhis etmeye ve temizlik ihtiyacını belirlemeye yardımcı olur (`-v` daha detaylı liste verir).
    ```
    # Örnek Çıktı
    docker system df
    TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
    Images          55        10        15.5GB    10.2GB (65%) # Aktif olmayan ve dangling imajlar
    Containers      10        3         1.2GB     800MB (66%) # Durdurulmuş konteynerler
    Local Volumes   15        5         5.8GB     2.1GB (36%) # Kullanılmayan isimlendirilmiş volume'ler
    Build Cache     150       0         12.3GB    12.3GB (100%)# Tüm build cache
    ```
*   **`docker system prune [-a --volumes -f]`**: Kullanılmayan Docker nesnelerini (durdurulmuş konteynerler, dangling imajlar, kullanılmayan ağlar, build cache) toplu olarak temizleyerek disk alanı açar. `-a` ile aktif konteynerler tarafından kullanılmayan tüm imajlar, `--volumes` ile kullanılmayan tüm lokal volume'ler de silinir (**Dikkat: `--volumes` veri kaybına yol açabilir!**). `-f` onay sormadan siler. Disk sorunlarında veya genel temizlik için sıkça kullanılır.
*   **`docker network inspect <ağ_adı_veya_id>`**: Belirli bir Docker ağının yapılandırmasını (sürücü, subnet, gateway vb.) ve o ağa hangi konteynerlerin hangi IP adresleriyle bağlı olduğunu detaylı olarak gösterir. Konteynerler arası bağlantı sorunlarında kullanılır.
*   **`docker volume inspect <volume_adı_veya_id>`**: Belirli bir Docker volume'ünün host üzerindeki bağlantı noktasını (`Mountpoint`), sürücüsünü ve diğer detaylarını gösterir. Volume ile ilgili sorunlarda veya volume'ün host'taki yerini bulmak için kullanılır.

## Yaygın Hatalar ve Çözümleri

*   **Sorun: Konteyner Başlar Başlamaz Duruyor (`Exited (0)` veya `Exited (non-zero)`)**
    *   **Olası Nedenler ve Anlamları:**
        *   **`Exited (0)`:** Konteynerin ana süreci (Dockerfile'daki `CMD` veya `ENTRYPOINT` ile belirtilen veya `docker run` ile verilen komut) başarılı bir şekilde görevini tamamlayıp normal olarak çıkış yapmıştır. Bu, tek seferlik bir iş (örn: bir script çalıştırma, veri işleme) yapan konteynerler için beklenen bir davranıştır. Ancak sürekli çalışması gereken bir servis (web sunucusu, veritabanı, API) için bu durum, sürecin ön planda (foreground) kalması gerekirken arka plana geçtiğini (daemonize olduğunu) veya hemen bittiğini gösterir. Servisler genellikle döngüde kalmalı veya sinyal beklemelidir.
        *   **`Exited (non-zero)`, örn: `Exited (1)`, `Exited (127)`, `Exited (137)`:** Ana süreç bir hata nedeniyle anormal bir şekilde sonlanmıştır. Çıkış kodları genellikle ipucu verir:
            *   `1`: Genel hata (script hatası, konfigürasyon sorunu vb.). Loglara bakılmalı.
            *   `126`: Komut çalıştırılamadı (izin sorunu?).
            *   `127`: Komut bulunamadı (PATH sorunu veya komut imajda yok?).
            *   `137`: Süreç SIGKILL (9) sinyali ile öldürüldü. Genellikle Linux OOM (Out-Of-Memory) Killer tarafından bellek limitini aştığı için sonlandırıldığını gösterir. `docker inspect` ile `OOMKilled` durumu kontrol edilebilir.
            *   `139`: Süreç SIGSEGV (11) sinyali aldı (Segmentation Fault - uygulama içi çökme).
            *   Diğer kodlar (`128 + sinyal_numarası`): Belirli bir sinyalle sonlandığını gösterir (örn: 130 = SIGINT/Ctrl+C, 143 = SIGTERM).
        *   Yanlış komut veya argümanlar verilmiş olabilir.
        *   Gerekli bir dosya, konfigürasyon veya ortam değişkeni eksik veya yanlış olabilir.
        *   Bağımlı bir servis (örn: veritabanı) henüz hazır olmayabilir (özellikle Docker Compose'da `depends_on` sadece başlatma sırasını kontrol eder, hazır olmayı değil - `condition: service_healthy` kullanılmalı veya entrypoint script'inde bekleme mekanizması olmalı).
    *   **Çözüm Adımları:**
        1.  **Loglara Bakın:** `docker logs <konteyner_id>` komutu ile konteynerin son loglarına bakın. Hata mesajı, stack trace veya neden çıktığına dair ipucu genellikle buradadır. Durmuş konteynerin ID'sini `docker ps -a` ile bulabilirsiniz.
        2.  **Etkileşimli Kabuk Deneyin:** Konteyneri `docker run` ile çalıştırırken asıl `CMD/ENTRYPOINT`'i geçersiz kılıp etkileşimli bir kabuk (`bash`, `sh`) açarak (`docker run -it --rm --entrypoint sh <imaj>`) konteynerin içine girin. İçeride manuel olarak ana süreci (veya ilgili komutları) çalıştırmayı deneyin ve hatayı canlı olarak gözlemleyin. Dosyaların yerinde olup olmadığını, izinleri, ortam değişkenlerini kontrol edin.
        3.  **Inspect ile Detayları Kontrol Edin:** `docker inspect <konteyner_id>` ile konteynerin durumunu kontrol edin. Özellikle `State` bölümündeki `ExitCode`, `Error` (varsa), `StartedAt`, `FinishedAt`, `OOMKilled` alanlarına bakın. Ayrıca `Config.Cmd`, `Config.Entrypoint`, `Config.Env`, `Mounts` gibi yapılandırma detaylarını doğrulayın.
        4.  **Dockerfile ve Entrypoint/CMD Kontrolü:** Dockerfile'daki `CMD` ve `ENTRYPOINT` direktiflerini dikkatlice kontrol edin. Servislerin ön planda çalıştığından emin olun (arka plana geçmemeli). Shell script'leri kullanılıyorsa, `set -e` ile hatalarda hemen çıkmasını sağlayın ve debug için `set -x` ekleyin. Exec form (`CMD ["executable", ...]`) genellikle shell formuna (`CMD command ...`) göre daha öngörülebilirdir.
        5.  **Kaynak Limitleri:** Eğer çıkış kodu 137 ise veya bellek sorunundan şüpheleniyorsanız, konteynere atanan bellek limitini (`docker run --memory=...` veya Compose'da `deploy.resources.limits.memory`) kontrol edin veya artırın. `docker stats` ile çalışma anındaki tüketimi izleyin.
        6.  **Bağımlılık Bekleme:** Eğer konteyner başka bir servise bağımlıysa (örn: veritabanı), diğer servisin tamamen hazır olmasını beklediğinden emin olun. Docker Compose'da `condition: service_healthy` kullanın (hedef servisin HEALTHCHECK'i olmalı) veya konteynerin başlangıç script'ine (entrypoint) bir bekleme döngüsü (örn: `wait-for-it.sh` veya benzeri bir script ile porta veya sağlık kontrolüne bağlanmayı deneyerek) ekleyin.

*   **Sorun: Port Çakışması ("Bind for 0.0.0.0:<port> failed: port is already allocated" veya "address already in use")**
    *   **Neden:** `docker run -p <host_port>:<container_port>` ile belirtilen `<host_port>` numaralı port, host makinesinde başka bir süreç (başka bir Docker konteyneri, host'ta çalışan normal bir uygulama veya sistem servisi) tarafından zaten kullanılıyor ve dinleniyor. Aynı anda iki süreç aynı IP:Port kombinasyonunu dinleyemez.
    *   **Çözüm:**
        *   **Farklı Host Portu Kullanın:** Konteyneri çalıştırırken host tarafında farklı, boş bir port numarası kullanın: `docker run -p 8081:80 ...`
        *   **Mevcut Süreci Durdurun/Değiştirin:** Eğer o portu kullanan diğer süreç gereksizse veya başka bir porta taşınabiliyorsa, onu durdurun veya yapılandırmasını değiştirin. Host'ta belirli bir portu hangi sürecin kullandığını bulmak için:
            *   **Linux:** `sudo ss -tulnp | grep ':<port>'` veya `sudo netstat -tulnp | grep ':<port>'`
            *   **macOS:** `sudo lsof -i :<port>`
            *   **Windows (CMD):** `netstat -ano | findstr "<port>"` (çıkan PID'yi Task Manager'da bulun)
            *   **Windows (PowerShell):** `Get-Process -Id (Get-NetTCPConnection -LocalPort <port>).OwningProcess`
            Eğer portu başka bir Docker konteyneri kullanıyorsa `docker ps` ile bulup `docker stop/rm` yapabilirsiniz.
        *   **Belirli Host IP Kullanın:** Eğer host'ta birden fazla IP adresi varsa ve çakışma sadece belirli bir IP'de ise, konteyneri sadece başka bir IP adresine bağlayabilirsiniz: `docker run -p <specific_host_ip>:<host_port>:<container_port> ...` Veya sadece localhost'a bağlamak için: `docker run -p 127.0.0.1:<host_port>:<container_port> ...`

*   **Sorun: "Cannot connect to the Docker daemon. Is the docker daemon running?"**
    *   **Nedenler:**
        *   Docker servisi (daemon - `dockerd`) host makinesinde çalışmıyor veya yanıt vermiyor.
        *   Mevcut kullanıcının Docker daemon soketine (`/var/run/docker.sock`) erişim izni yok (Linux'ta çok yaygın).
        *   Docker Desktop (Windows/macOS) düzgün başlamamış, çökmüş veya arka plandaki sanal makine/WSL entegrasyonunda sorun var.
        *   Docker CLI, `DOCKER_HOST` ortam değişkeni veya `docker context` ayarları nedeniyle yanlış bir daemon adresine bağlanmaya çalışıyor olabilir.
    *   **Çözüm:**
        *   **Linux:**
            1.  Servis durumunu kontrol edin: `sudo systemctl status docker` veya `sudo service docker status`.
            2.  Çalışmıyorsa başlatın: `sudo systemctl start docker` veya `sudo service docker start`.
            3.  Hata varsa loglara bakın: `sudo journalctl -u docker.service`.
            4.  İzinleri kontrol edin: Mevcut kullanıcının `docker` grubuna üye olduğundan emin olun (`groups` komutu ile kontrol edin). Değilse `sudo usermod -aG docker $USER` ile ekleyin ve ardından **oturumu kapatıp tekrar açın** veya `newgrp docker` komutunu (geçici çözüm) deneyin. `ls -l /var/run/docker.sock` komutu ile soket dosyasının grup sahipliğinin `docker` olduğundan emin olun.
        *   **Windows/macOS:**
            1.  Docker Desktop uygulamasının çalıştığından ve ikonunun (genellikle sistem tepsisinde) stabil olduğundan emin olun.
            2.  Çalışmıyorsa veya yanıt vermiyorsa, uygulamayı kapatıp yeniden başlatmayı deneyin.
            3.  Docker Desktop ayarlarından (Troubleshoot / Reset) fabrika ayarlarına sıfırlamayı veya yeniden kurmayı deneyin (bu işlem imajları/konteynerleri silebilir, dikkatli olun).
            4.  WSL 2 backend kullanılıyorsa, WSL'in kendisinin çalıştığından emin olun (`wsl --list --verbose` komutu PowerShell'de). Gerekirse WSL'i yeniden başlatın.
            5.  Docker Desktop loglarına bakın (Ayarlar menüsünden veya belirli dosya konumlarından erişilebilir).
        *   `DOCKER_HOST` ortam değişkeninin ayarlı olup olmadığını kontrol edin (`echo $DOCKER_HOST` veya `env | grep DOCKER_HOST`). Ayarlıysa ve lokal daemon'a bağlanmak istiyorsanız, değişkeni kaldırın (`unset DOCKER_HOST`).
        *   Docker context'ini kontrol edin (`docker context ls`) ve doğru context'in aktif olduğundan emin olun (`docker context use <context_name>`).

*   **Sorun: Ağ Sorunları (Konteynerler Birbirine Erişemiyor, Dışarı Çıkamıyor, DNS Çözümlemesi Çalışmıyor)**
    *   **Nedenler:**
        *   İletişim kurması gereken konteynerler farklı Docker ağlarında olabilirler veya hiç bir ağa bağlı olmayabilirler (`--network=none`).
        *   Konteynerler varsayılan `bridge` ağında ise, birbirlerine isimleriyle güvenilir bir şekilde erişemeyebilirler (IP ile erişim denenmeli). Kullanıcı tanımlı ağlar isim çözümlemesi için tercih edilir.
        *   Host güvenlik duvarı (firewall) konteynerler arası (özellikle farklı ağlardaysa) veya konteynerden dışarı giden trafiği engelliyor olabilir.
        *   Konteyner içindeki DNS çözümlemesi çalışmıyor olabilir (yanlış DNS sunucusu ayarı, ağ geçidine erişememe).
        *   Docker ağ alt sisteminde (iptables kuralları, sanal arayüzler) bir sorun olabilir.
        *   Overlay ağları (Swarm) kullanılıyorsa, node'lar arasındaki kontrol/veri düzlemi iletişiminde sorun olabilir (gerekli portlar açık olmayabilir).
    *   **Çözüm:**
        1.  **Ağları Kontrol Et:** İlgili konteynerlerin hangi ağlara bağlı olduğunu `docker inspect <konteyner>` (`Networks` bölümü) veya `docker network inspect <ağ>` ile kontrol edin.
        2.  **Aynı Ağa Bağla:** İletişim kurması gereken konteynerlerin aynı **kullanıcı tanımlı köprü ağında** (`docker network create mynet && docker run --network mynet ...`) olduğundan emin olun. Farklı ağlardalarsa, ya aynı ağa taşıyın ya da bir konteyneri diğerinin ağına bağlayın (`docker network connect <hedef_ağ> <konteyner>`).
        3.  **Temel Bağlantı Testi (ping):** Bir konteynerden diğerine `docker exec -it <kaynak_konteyner> ping <hedef_konteyner_adı_veya_ip>` ile ping atmayı deneyin. Kullanıcı tanımlı ağda isimle ping çalışmalıdır.
        4.  **Port Bağlantı Testi (curl/telnet):** Eğer bir servis belirli bir portta çalışıyorsa, diğer konteynerden o porta erişmeyi deneyin: `docker exec -it <kaynak_konteyner> curl <hedef_konteyner_adı_veya_ip>:<port>` veya `docker exec -it <kaynak_konteyner> nc -zv <hedef_konteyner_adı_veya_ip> <port>` (`netcat` kuruluysa).
        5.  **Dış Bağlantı Testi:** Konteynerin dış dünyaya çıkıp çıkamadığını test edin: `docker exec -it <konteyner> ping 8.8.8.8` (Google DNS) ve `docker exec -it <konteyner> curl google.com`. İlki çalışıp ikincisi çalışmıyorsa DNS sorunudur.
        6.  **DNS Kontrolü:** Konteyner içindeki DNS ayarlarını kontrol edin: `docker exec -it <konteyner> cat /etc/resolv.conf`. Genellikle Docker'ın gömülü DNS sunucusunu (127.0.0.11 - kullanıcı tanımlı ağlarda) veya host'un DNS sunucularını gösterir. Gerekirse `docker run --dns=<dns_server_ip>` ile özel DNS ayarlayabilirsiniz. Host'taki DNS'in çalıştığından emin olun.
        7.  **Host Firewall Kontrolü:** Host makinesindeki güvenlik duvarı kurallarını kontrol edin. Docker genellikle kendi `iptables` kurallarını yönetir, ancak özel kurallar veya başka güvenlik yazılımları (firewalld, ufw) Docker trafiğini engelleyebilir. Özellikle `FORWARD` zincirini ve `DOCKER`, `DOCKER-ISOLATION-STAGE-1/2`, `DOCKER-USER` zincirlerini inceleyin (`sudo iptables -L -n -v`). Gerekirse Docker servisinin yeniden başlatılması kuralları düzeltebilir.
        8.  **Docker Ağını Yeniden Oluşturma:** Sorun devam ederse, sorunlu görünen kullanıcı tanımlı ağı (`docker network inspect <ağ>` ile inceledikten sonra) silip (`docker network rm <ağ>`) yeniden oluşturmayı (`docker network create <ağ>`) deneyin (önce bağlı tüm konteynerleri durdurup/kaldırmanız veya ağdan çıkarmanız gerekir).
        9.  **Docker Servisini Yeniden Başlatma:** Son çare olarak Docker daemon'ı yeniden başlatmak (`sudo systemctl restart docker`) bazen ağ sorunlarını çözebilir, ancak çalışan tüm konteynerleri durduracaktır.

*   **Sorun: Volume/Bind Mount İzin Hataları ("Permission denied", "Cannot open file", "Read-only file system")**
    *   **Neden (Genellikle Linux Host'ta):** Host makinesinden bind mount edilen bir dizin veya dosyanın sahip/grup bilgisi (UID/GID) ve izinleri (okuma/yazma/çalıştırma), konteyner içinde çalışan sürecin kullanıcı ID'si (UID) ve grup ID'si (GID) ile uyumsuz. Konteynerdeki (genellikle root olmayan) süreç, host'taki dosyaya erişmeye çalıştığında Linux çekirdeği izinleri kontrol eder ve eşleşmezse "Permission denied" hatası verir. İsimlendirilmiş Volume'lerde bu sorun genellikle yaşanmaz çünkü Docker volume içeriğini başlangıçta doğru UID/GID ile (genellikle konteynerdeki kullanıcının) oluşturur veya yönetir. `Read-only file system` hatası ise ya `docker run --read-only` kullanılıp yazmaya çalışılıyordur ya da mount seçeneği (`-v host:container:ro`) ile salt okunur bağlanmıştır.
    *   **Çözüm:**
        *   **Host İzinlerini Ayarlama (Bind Mount):** En doğrudan yöntem, host üzerindeki bind mount kaynağının (`<host_path>`) sahipliğini (`sudo chown <UID>:<GID> <host_path>`) ve/veya izinlerini (`sudo chmod ... <host_path>`) konteyner içindeki kullanıcının UID/GID'sine uygun olacak şekilde ayarlamaktır. Konteyner içindeki kullanıcının UID/GID'sini `docker exec -it <konteyner> id` ile öğrenebilirsiniz. Bu, host dosya sistemini değiştirdiği için dikkatli yapılmalıdır.
        *   **Konteynerde Aynı UID/GID Kullanma:** Konteyneri çalıştırırken veya Dockerfile'da `USER` direktifini kullanırken, host'taki ilgili dizine erişimi olan kullanıcının UID/GID'sini belirtin (`docker run -u <UID>:<GID> ...`). Bu, özellikle geliştirme ortamlarında yaygındır.
        *   **Entrypoint ile İzin Ayarlama:** Konteynerin başlangıç script'inde (entrypoint), konteynerdeki kullanıcının UID/GID'sini alıp (eğer `-u` ile dinamik olarak veriliyorsa) ilgili volume/mount dizininin sahipliğini konteyner içinde `chown` ile ayarlayabilirsiniz.
        *   **İsimlendirilmiş Volume Kullanma:** İzin sorunlarından kaçınmanın en temiz yolu genellikle isimlendirilmiş Docker Volume'leri (`docker run -v mydata:/app/data`) kullanmaktır. Docker bunları yönetir ve genellikle izin sorunları yaşanmaz.
        *   **Salt Okunur Kontrolü:** Eğer `Read-only file system` hatası alıyorsanız, konteynerin `--read-only` seçeneği ile çalıştırılmadığından veya ilgili mount'un `:ro` (read-only) olarak bağlanmadığından emin olun. Eğer salt okunur gerekiyorsa, uygulamanın yazması gereken yerlere `tmpfs` veya ayrı bir yazılabilir volume bağlayın.
        *   **Docker Desktop (Mac/Win):** Bu platformlarda kullanılan dosya sistemi sanallaştırma katmanları (gRPC FUSE, VirtioFS) genellikle UID/GID eşlemesini otomatik olarak yapar ve izin sorunları daha az yaşanır. Ancak bu katmanlar nedeniyle I/O performansı Linux host'a göre daha düşük olabilir.

*   **Sorun: İmaj Build Hataları**
    *   **Nedenler:**
        *   Dockerfile sözdizimi hatası (`docker build` hemen hata verir).
        *   `RUN` komutlarından birinin başarısız olması (çıkış kodu sıfır değil): Paket bulunamadı (repository güncel değil, paket adı yanlış, repo erişimi yok), derleme hatası (kod hatası, bağımlılık eksik), script hatası.
        *   `COPY` veya `ADD` için kaynak dosyanın build bağlamında (context) bulunamaması (yol yanlış, dosya yok, `.dockerignore` tarafından dışlanmış).
        *   Ağ sorunları: Temel imaj veya `RUN` komutunda indirilen dosyalar/paketler için registry/repository'ye erişilemiyor (proxy, firewall, DNS sorunu).
        *   Yetersiz disk alanı veya bellek (özellikle büyük imajlar veya derleme işlemleri sırasında).
        *   Build cache ile ilgili sorunlar (bozuk katman).
        *   Temel imajın çekilememesi (imaj adı/etiketi yanlış, registry erişimi yok, kimlik doğrulama hatası).
    *   **Çözüm:**
        *   **Hata Mesajını Oku:** Build çıktısındaki hata mesajını dikkatlice okuyun. Genellikle hangi Dockerfile satırında, hangi komutta ve neden hata oluştuğu açıkça belirtilir.
        *   **Sorunlu Komutu İncele:** Hata veren `RUN` komutunu veya ondan önceki komutları inceleyin. Komutu manuel olarak çalıştırmayı deneyin (ya lokalde ya da başarılı olan son katmandan bir konteyner başlatıp içinde deneyerek: `docker run -it --rm <son_başarılı_katman_id> sh`). Paket yöneticisi komutlarında `apt-get update` veya `apk update` yapıldığından emin olun. Paket adlarının doğru olduğunu kontrol edin.
        *   **COPY/ADD Yollarını Kontrol Et:** Kaynak ve hedef yolların doğru yazıldığından, kaynak dosyanın build komutunu çalıştırdığınız dizine (build context) göre doğru yolda olduğundan ve `.dockerignore` dosyasında dışlanmadığından emin olun. Build context'in ne olduğunu (`docker build .` komutundaki `.`) kontrol edin.
        *   **Ağ Bağlantısını Kontrol Et:** CI sunucusunun veya lokal makinenizin ilgili registry'lere ve paket depolarına erişimi olduğundan emin olun. Proxy ayarları gerekiyorsa, `docker build --build-arg HTTP_PROXY=... --build-arg HTTPS_PROXY=...` ile veya Docker daemon yapılandırmasında ayarlayın. DNS sorunlarını kontrol edin. Gerekirse geçici olarak `docker build --network=host` seçeneğini deneyin (güvenlik riski oluşturabilir).
        *   **Kaynakları Kontrol Et:** Disk alanını (`df -h`, `docker system df`) ve build sırasında sistem belleğini kontrol edin. `docker system prune` ile yer açmayı deneyin.
        *   **Cache'i Temizle:** Bazen build cache'indeki bozuk bir katman sorunlara yol açabilir. `docker build --no-cache ...` seçeneği ile cache kullanmadan build yapmayı deneyin (daha uzun sürer). BuildKit kullanıyorsanız daha granüler cache yönetimi seçenekleri vardır.
        *   **Temel İmajı Kontrol Et:** `FROM` satırındaki imaj adının ve etiketinin doğru olduğundan, imajın registry'de var olduğundan ve erişiminiz olduğundan (gerekirse `docker login`) emin olun.

*   **Sorun: Disk Alanının Dolması ("no space left on device")**
    *   **Neden:** Docker, zamanla host üzerinde önemli miktarda disk alanı kaplayabilir. Bunun ana nedenleri şunlardır:
        *   **Kullanılmayan İmajlar:** Eski sürümler, deneme amaçlı indirilenler veya etiketini kaybetmiş (dangling) imajlar birikebilir.
        *   **Durdurulmuş Konteynerler:** `docker run` ile `--rm` olmadan çalıştırılıp durdurulan konteynerler diskte yer kaplamaya devam eder (özellikle yazılabilir katmanları).
        *   **Kullanılmayan Volume'ler:** Özellikle anonim volume'ler veya artık kullanılmayan isimlendirilmiş volume'ler veri içermeye devam edebilir.
        *   **Build Cache:** Başarısız veya başarılı her build işlemi sırasında oluşan ara katmanlar cache olarak saklanır ve zamanla büyük boyutlara ulaşabilir.
        *   **Log Dosyaları:** Eğer `json-file` log sürücüsü kullanılıyorsa ve log rotasyonu (`max-size`, `max-file`) yapılandırılmadıysa, konteyner log dosyaları kontrolsüzce büyüyebilir.
    *   **Çözüm:**
        1.  **Teşhis:** `docker system df [-v]` komutu ile hangi Docker nesne türünün en çok yer kapladığını ve ne kadarının geri kazanılabileceğini belirleyin. Host işletim sisteminin disk kullanımını da kontrol edin (`df -h` veya eşdeğeri). Docker'ın veri dizininin (`/var/lib/docker` - Linux) boyutuna bakın.
        2.  **Toplu Temizlik (Prune):** En etkili ve hızlı yöntem `docker system prune` komutunu kullanmaktır:
            *   `docker system prune`: Durdurulmuş tüm konteynerleri, kullanılmayan tüm ağları, tüm dangling imajları ve tüm build cache'ini siler. Genellikle güvenlidir.
            *   `docker system prune -a`: Yukarıdakilere ek olarak, herhangi bir konteyner tarafından kullanılmayan *tüm* imajları (dangling olmayanlar dahil) siler. Daha agresiftir, sık kullanmadığınız imajları yeniden indirmeniz gerekebilir.
            *   `docker system prune --volumes`: Yukarıdakilere ek olarak (eğer `-a` da varsa), herhangi bir konteyner tarafından kullanılmayan *tüm* lokal isimlendirilmiş volume'leri siler. **Bu komut kalıcı veri kaybına neden olabilir, çok dikkatli olun ve silinecek volume'leri önceden kontrol edin!**
            Bu komutlar genellikle ne kadar yer açılacağını tahmin eder ve onay ister (`-f` ile onay atlanabilir).
        3.  **Hedefli Temizlik:** Belirli nesne türlerini ayrı ayrı temizleyebilirsiniz:
            *   `docker container prune`: Durdurulmuş tüm konteynerleri siler.
            *   `docker image prune [-a]`: Kullanılmayan imajları siler (`-a` ile tüm referanssızları). Filtreleme (`--filter "until=..."`) ile belirli bir tarihten eski imajları silmek de mümkündür.
            *   `docker volume prune`: Kullanılmayan tüm lokal volume'leri siler (**Dikkat!**).
            *   `docker network prune`: Kullanılmayan tüm ağları siler (genellikle az yer kaplar).
            *   `docker builder prune`: Tüm build cache'ini temizler.
        4.  **Manuel Silme:** Belirli eski veya gereksiz imajları (`docker rmi <imaj>`), konteynerleri (`docker rm <konteyner>`), volume'leri (`docker volume rm <volume>`) seçerek manuel olarak silebilirsiniz. Listeleme komutlarını (`docker images`, `docker ps -a`, `docker volume ls`) kullanarak nelerin silineceğini belirleyebilirsiniz.
        5.  **Log Rotasyonu Yapılandırma:** Eğer varsayılan `json-file` log sürücüsünü kullanıyorsanız, Docker daemon yapılandırmasında (`daemon.json`) veya her konteyner için `docker run` / Compose dosyasında log boyutunu ve dosya sayısını sınırlayın: `"log-opts": {"max-size": "10m", "max-file": "3"}` veya `--log-opt max-size=10m --log-opt max-file=3`.
        6.  **Docker Veri Dizini Taşıma:** Eğer `/var/lib/docker` dizininin bulunduğu disk bölümü küçükse, Docker'ı durdurup bu dizini daha büyük bir diske taşıyabilir ve Docker'ı yeni konumu kullanacak şekilde yapılandırabilirsiniz (detayları Docker dokümantasyonunda bulunur).

# İleri Seviye Konular ve Ekosistem

Bu bölümde, Docker'ın temel kullanımının ötesine geçen bazı konulara ve Docker ekosistemindeki diğer önemli teknolojilere daha yakından bakacağız.

## Kubernetes ile Docker Entegrasyonu

*   **Kubernetes (K8s) Nedir?:** Google tarafından başlatılan ve şu anda CNCF (Cloud Native Computing Foundation) tarafından yönetilen, açık kaynaklı, konteyner orkestrasyonunda endüstri standardı haline gelmiş bir platformdur. Uygulamaların dağıtımını, ölçeklenmesini ve yönetimini otomatikleştirmek için tasarlanmıştır. Docker Swarm'a göre çok daha kapsamlı özellikler, daha fazla esneklik ve daha büyük bir ekosistem sunar (gelişmiş zamanlama algoritmaları, karmaşık self-healing mekanizmaları, yatay ve dikey otomatik ölçekleme, gelişmiş service discovery ve load balancing seçenekleri, secret/config yönetimi, stateful uygulamalar için storage orkestrasyonu, genişletilebilirlik için operatörler vb.). Genellikle daha büyük ölçekli, dağıtık, mikroservis tabanlı ve karmaşık uygulamaları yönetmek için tercih edilir, ancak öğrenme eğrisi Swarm'a göre daha diktir.
*   **Docker ve K8s İlişkisi: Konteyner Çalışma Zamanı (Runtime):** Kubernetes, temel olarak konteynerleri çalıştırmak ve yönetmek için bir *konteyner çalışma zamanına (container runtime)* ihtiyaç duyar. Tarihsel olarak Docker Engine (içindeki `containerd` ile birlikte) en popüler ve varsayılan runtime idi. Kubernetes, Docker tarafından oluşturulan OCI (Open Container Initiative) uyumlu konteyner imajlarını sorunsuz bir şekilde çalıştırabilir. Yani, `Dockerfile` kullanarak `docker build` ile oluşturduğunuz standart Docker imajları doğrudan bir Kubernetes kümesinde (Pod'lar içinde) kullanılabilir. Docker, imaj oluşturma ve geliştirme sürecinin vazgeçilmez bir parçası olmaya devam etmektedir.
*   **Runtime Değişiklikleri ve CRI:** Kubernetes v1.20'den itibaren, Docker Engine'in doğrudan entegrasyonu (dockershim) deprecated oldu ve v1.24'te kaldırıldı. Bunun yerine Kubernetes, CRI (Container Runtime Interface) adlı standart bir arayüz üzerinden container runtime'larla konuşur. Docker Engine'in içinden çıkan ve bağımsız bir proje haline gelen `containerd` ve Red Hat tarafından geliştirilen `CRI-O` gibi runtime'lar doğrudan CRI uyumludur ve günümüzde Kubernetes kümelerinde yaygın olarak kullanılırlar. Bu değişiklik, çoğu son kullanıcı ve geliştirici için büyük ölçüde **şeffaftır**. Docker ile imaj build etmeye devam edersiniz ve bu OCI uyumlu imajlar `containerd` veya `CRI-O` tarafından sorunsuz bir şekilde çalıştırılır. Yani Kubernetes'in Docker Engine'i doğrudan runtime olarak kullanmaması, Docker ile imaj oluşturma pratiğini değiştirmez.
*   **Yerel Geliştirme ve Test:** Geliştiricilerin uygulamalarını lokal makinelerinde Kubernetes ortamında test etmeleri ve geliştirmeleri için çeşitli araçlar mevcuttur:
    *   **Docker Desktop:** Windows ve macOS için Docker Desktop, isteğe bağlı olarak tek node'lu bir Kubernetes kümesini kolayca etkinleştirme özelliği sunar. Geliştirme için çok pratiktir.
    *   **Minikube:** Lokal bir sanal makine veya Docker konteyneri içinde tek node'lu bir Kubernetes kümesi çalıştırır. Popüler ve esnek bir seçenektir.
    *   **Kind (Kubernetes in Docker):** Docker konteynerlerini Kubernetes node'ları olarak kullanarak lokal bir küme oluşturur. Hızlı kurulum ve test için idealdir.
    *   **K3s (Rancher):** Hafif, sertifikalı bir Kubernetes dağıtımıdır. Özellikle kaynak kısıtlı ortamlar (IoT, Edge) ve geliştirme için tasarlanmıştır. Kolayca kurulabilir.
*   **Sonuç:** Docker, konteyner imajlarını oluşturmak, paketlemek ve paylaşmak için temel araç ve standart olmaya devam ederken, Kubernetes bu imajları büyük ölçekte çalıştırmak, yönetmek, ölçeklemek ve orkestre etmek için endüstri standardı platform haline gelmiştir. İkisi birbirini tamamlayan teknolojilerdir.

## Docker API ve SDK'lar

*   **Docker Engine API:** Docker Daemon (`dockerd`), tüm işlevselliğini (imaj indirme/build etme, konteyner başlatma/durdurma, ağ/volume yönetimi vb.) bir RESTful HTTP API üzerinden sunar. Kullandığımız `docker` komut satırı arayüzü (CLI) aslında arka planda bu API ile konuşan bir istemcidir.
*   **Kullanım Alanları:** Bu API'yi doğrudan (örn: `curl` ile) veya SDK'lar aracılığıyla kullanarak:
    *   Docker işlemlerini programatik olarak otomatikleştirebilirsiniz (kendi CI/CD scriptlerinizde, özel yönetim araçlarınızda).
    *   Özel Docker yönetim arayüzleri veya dashboard'lar geliştirebilirsiniz.
    *   Docker'ı diğer sistemlerle (izleme sistemleri, altyapı yönetim araçları) entegre edebilirsiniz.
    API, varsayılan olarak Linux'ta bir Unix soketi (`/var/run/docker.sock`) üzerinden veya yapılandırılırsa TLS ile korunan bir TCP portu (genellikle 2376) üzerinden erişilebilir. Soket erişimi root yetkisi gerektirir veya kullanıcının `docker` grubunda olmasını gerektirir. TCP erişimi mutlaka TLS ile korunmalıdır.
*   **SDK'lar (Software Development Kits):** Docker Engine API'sini farklı programlama dillerinden kolayca ve dile özgü (idiomatic) bir şekilde kullanmak için resmi ve topluluk tarafından geliştirilmiş SDK'lar mevcuttur. Bunlar API çağrılarını soyutlayarak kullanımı kolaylaştırır. Popüler olanlar:
    *   **Python:** `docker` ([`docker-py.readthedocs.io`](https://docker-py.readthedocs.io/)) - Çok popüler ve yaygın kullanılır.
    *   **Go:** `moby/moby/client` ([`pkg.go.dev/github.com/docker/docker/client`](https://pkg.go.dev/github.com/docker/docker/client)) - Docker'ın kendisinin yazıldığı dil olduğu için resmi ve tam özellikli.
    *   **Java:** `docker-java` ([`github.com/docker-java/docker-java`](https://github.com/docker-java/docker-java)) - Popüler bir topluluk projesi.
    *   **JavaScript/Node.js:** `dockerode` ([`github.com/apocas/dockerode`](https://github.com/apocas/dockerode)) - Yaygın kullanılan bir Node.js kütüphanesi.
    *   **Ruby:** `docker-api` ([`github.com/swipely/docker-api`](https://github.com/swipely/docker-api)) - Popüler bir Ruby gem'i.
    *   **.NET/C#:** `Docker.DotNet` ([`github.com/dotnet/Docker.DotNet`](https://github.com/dotnet/Docker.DotNet))
*   **API Dokümantasyonu:** API endpoint'leri, parametreleri ve yanıt formatları hakkında detaylı bilgi için resmi dokümantasyona başvurun: <https://docs.docker.com/engine/api/>

## Özel (Custom) Network ve Volume Sürücüleri (Plugins)

*   **Eklenti (Plugin) Mimarisi:** Docker, temel işlevselliğini genişletmek için bir eklenti (plugin) sistemi sunar. Bu sayede üçüncü parti geliştiriciler veya topluluk, Docker'ın ağ (network) ve depolama (volume) yeteneklerini farklı teknolojilerle entegre etmek için özel sürücüler geliştirebilir ve dağıtabilir. Yetkilendirme (authorization) ve loglama (logging) için de eklentiler mümkündür.
*   **Özel Network Sürücüleri:** Docker'ın varsayılan bridge, host, overlay gibi ağ modlarının ötesinde, farklı ağ topolojileri, gelişmiş ağ politikaları veya SDN (Software-Defined Networking) çözümleriyle entegrasyon sağlamak için kullanılır. Örneğin:
    *   **Calico, Weave Net, Cilium:** Kubernetes dünyasında popüler olan bu CNI (Container Network Interface) eklentileri, genellikle Docker Swarm veya bağımsız Docker host'ları için de network sürücüleri sunarak granüler ağ politikaları (firewalling), segmentasyon ve bazen şifreli iletişim sağlarlar.
    *   **Macvlan / Ipvlan:** Docker içine gömülü olsalar da, bunlar da aslında özel kullanım durumları için farklı ağ davranışları sağlayan sürücülerdir.
    *   Bulut sağlayıcılarının özel entegrasyonları (örn: AWS VPC CNI).
*   **Özel Volume Sürücüleri:** Konteyner verilerini Docker'ın varsayılan `local` sürücüsü (host dosya sistemi üzerinde saklar) yerine farklı paylaşımlı veya harici depolama sistemlerinde saklamak ve yönetmek için kullanılır. Bu, verilerin birden fazla host arasında paylaşılmasını, daha yüksek dayanıklılık (redundancy), anlık görüntü (snapshot) alma veya merkezi yedekleme gibi yetenekler kazandırılmasını sağlar. Örnekler:
    *   **NFS (Network File System):** Paylaşımlı ağ dosya sistemlerine bağlanmak için.
    *   **CIFS/Samba:** Windows dosya paylaşımlarına bağlanmak için.
    *   **GlusterFS, Ceph:** Dağıtık dosya sistemlerine bağlanmak için.
    *   **Bulut Depolama Entegrasyonları:** AWS EBS (Elastic Block Store), EFS (Elastic File System), Azure Disk, Azure Files, Google Persistent Disk gibi bulut sağlayıcılarının depolama servislerini doğrudan Docker volume'leri olarak kullanmak için (genellikle ilgili sağlayıcının eklentisi ile).
    *   **RexRay, Portworx, StorageOS:** Gelişmiş depolama yönetimi özellikleri sunan ticari veya açık kaynaklı depolama orkestrasyon çözümleri.
*   **Kurulum ve Yönetim:** Eklentiler genellikle Docker Hub veya diğer registry'lerden bir Docker imajı gibi çekilerek kurulur (`docker plugin install <plugin_name_or_url> --grant-all-permissions`) ve yönetilir (`docker plugin ls`, `docker plugin enable/disable/rm <plugin>`). Bir eklenti kurulduktan sonra, ağ veya volume oluştururken `--driver <plugin_driver_name>` veya Compose dosyasında `driver:` seçeneği ile bu özel sürücü belirtilir. Eklentilerin kendileri de genellikle Docker konteynerleri olarak çalışır.

## BuildKit ve Gelişmiş Build Seçenekleri

*   **BuildKit Nedir?:** Docker'ın klasik build motorunun yerini alan, Moby projesi kapsamında geliştirilmiş yeni nesil, daha modern, performanslı ve özellik açısından zengin imaj oluşturma motorudur (backend). Eski build motoruna göre birçok önemli avantaj sunar:
    *   **Paralel Build İşlemleri:** Dockerfile'daki bağımsız build aşamalarını (örneğin farklı `RUN` komutları veya multi-stage build'deki farklı aşamalar) aynı anda çalıştırarak toplam build sürelerini önemli ölçüde kısaltır.
    *   **Gelişmiş ve Atlanabilir Cache Yönetimi:** Daha verimli cache kullanımı sağlar. Kullanılmayan build aşamalarını ve komutları atlar. Build cache'ini harici bir registry'ye (inline, registry veya gha - GitHub Actions cache) aktarma (`--cache-to`) ve başka build'lerde kullanma (`--cache-from`) yeteneği sunar, bu da CI/CD ortamlarında cache'i paylaşmayı mümkün kılar.
    *   **Atlanabilir Kullanılmayan Aşamalar (Skip Unused Stages):** Multi-stage build'lerde, sadece hedeflenen son aşama (`--target <stage_name>`) için gerçekten gerekli olan önceki aşamaları build eder, gereksiz aşamaları atlar.
    *   **Build Sırasında Secret Yönetimi (`--mount=type=secret`):** Build işlemi sırasında (örneğin özel bir paketi indirmek için token veya özel bir Git deposuna erişim için SSH anahtarı gibi) hassas bilgilere güvenli bir şekilde erişim sağlar. Bu secret'lar sadece mount edildikleri `RUN` komutu sırasında erişilebilir olur ve son imaj katmanlarına veya imaj geçmişine **sızmaz**.
        ```dockerfile
        # syntax=docker/dockerfile:1
        # ...
        RUN --mount=type=secret,id=mysecret,dst=/etc/secret/key \
            cat /etc/secret/key > /app/config && \
            my_build_command --key-file=/app/config
        # Build komutu: docker build --secret id=mysecret,src=mysecret.txt .
        ```
    *   **Build Sırasında SSH Agent veya Anahtar Kullanımı (`--mount=type=ssh`):** Build sırasında özel Git depolarına veya diğer SSH gerektiren kaynaklara, host'taki SSH agent'ını veya belirli SSH anahtarlarını güvenli bir şekilde ileterek erişim sağlar. Anahtarlar imaja kopyalanmaz.
        ```dockerfile
        # syntax=docker/dockerfile:1
        # ...
        RUN --mount=type=ssh \
            git clone git@github.com:my-private-repo/app.git /app
        # Build komutu: docker build --ssh default . (varsayılan agent'ı kullanır)
        ```
    *   **Daha İyi Çıktı Formatları:** Build sürecinin ilerlemesini daha anlaşılır gösteren farklı çıktı formatları (`--progress=plain|tty`) sunar.
    *   **'Here Documents' Desteği:** Dockerfile içinde `RUN <<EOF ... EOF` veya `COPY <<EOF ... EOF` gibi yapılarla çok satırlı script'ler veya dosyalar oluşturmayı kolaylaştırır.
*   **Etkinleştirme:** Modern Docker sürümlerinde (Docker Engine v18.09+ ve Docker Desktop'ın güncel sürümleri) BuildKit genellikle varsayılan olarak etkindir. Durumu `docker build --help` komutunun çıktısında veya `docker info | grep BuildKit` ile kontrol edilebilir. Değilse, ortam değişkeni ile etkinleştirilebilir (`export DOCKER_BUILDKIT=1`) veya Docker daemon yapılandırmasında (`daemon.json`) `"features": {"buildkit": true}` ayarı ile kalıcı hale getirilebilir.
*   **Buildx (Docker Build CLI Plugin):** Docker CLI için BuildKit'in tüm gelişmiş yeteneklerini (özellikle multi-platform build, yeni build seçenekleri, farklı builder instance'ları yönetme) tam olarak kullanmayı sağlayan resmi bir eklentidir. Genellikle modern Docker sürümleriyle birlikte gelir. `docker buildx build ...` komutu ile kullanılır ve standart `docker build`'in yerine geçebilir/genişletebilir. `docker buildx create --use` ile farklı builder instance'ları (örn: Docker konteyneri içinde çalışan veya uzak bir makinede çalışan) oluşturulabilir ve yönetilebilir.

## Windows Konteynerları

*   **Genel Bakış:** Docker, sadece Linux tabanlı konteynerleri değil, aynı zamanda Windows işletim sistemi üzerinde çalışan **Windows konteynerlerini** de destekler. Bu, özellikle .NET Framework uygulamaları, IIS web sunucuları, SQL Server veritabanları gibi geleneksel Windows tabanlı uygulamaları ve servisleri modernize etmek, paketlemek ve dağıtmak için kullanılır.
*   **Çalışma Mantığı ve Kernel Paylaşımı:** Linux konteynerlerinin host'un Linux kernel'ini paylaştığı gibi, Windows konteynerleri de host'un Windows kernel'ini (ve bazı sistem kütüphanelerini) paylaşır. Bu nedenle, Windows konteynerleri sadece Windows host'lar üzerinde çalıştırılabilir (Windows 10/11 Pro/Enterprise veya Windows Server 2016 ve sonrası sürümler). Linux üzerinde Windows konteyneri (veya tersi) çalıştırmak mümkün değildir (sanallaştırma katmanı olmadan).
*   **İzolasyon Modları:** Windows konteynerleri, farklı izolasyon seviyeleri ve uyumluluk ihtiyaçları için iki temel mod sunar:
    *   **Process Isolation (Süreç İzolasyonu - Varsayılan):** Linux konteynerlerine en yakın olan moddur. Konteynerler host kernel'ini paylaşır, izolasyon process, dosya sistemi, registry ve ağ seviyesinde sağlanır. Daha hızlı başlar, daha az kaynak (bellek, disk) tüketir ve daha yüksek yoğunluk sağlar. Host ile aynı Windows sürümünü ve kernel versiyonunu gerektirir.
    *   **Hyper-V Isolation (Hyper-V İzolasyonu):** Her konteyner, Microsoft'un Hyper-V hipervizörü kullanılarak oluşturulan çok hafif ve optimize edilmiş bir sanal makine (Utility VM) içinde çalıştırılır. Her konteyner kendi Windows kernel kopyasına sahip olur. Bu, host ile konteyner arasında çok daha güçlü bir güvenlik izolasyonu sağlar (kernel seviyesinde). Ayrıca host'tan farklı (ancak uyumlu) Windows kernel sürümlerini çalıştırmaya olanak tanır. Süreç izolasyonuna göre biraz daha yavaş başlar ve daha fazla kaynak tüketir. Güvenlik açısından kritik uygulamalar veya uyumluluk sorunları olduğunda tercih edilir. `docker run --isolation=hyperv ...` seçeneği ile etkinleştirilir.
*   **Temel İmajlar (Base Images):** Windows konteynerleri için temel imajlar Microsoft tarafından Container Registry (`mcr.microsoft.com`) üzerinde sağlanır. En yaygın kullanılanlar:
    *   **`mcr.microsoft.com/windows/servercore:<tag>`:** Geleneksel Windows Server uygulamalarıyla en yüksek uyumluluğu sunar. Daha büyüktür (birkaç GB). Full .NET Framework, PowerShell gibi bileşenleri içerir.
    *   **`mcr.microsoft.com/windows/nanoserver:<tag>`:** Çok daha küçük (birkaç yüz MB), optimize edilmiş bir Windows sürümüdür. Özellikle .NET Core, Node.js, Python gibi modern uygulamalar için tasarlanmıştır. Daha az API yüzeyi sunar, GUI yoktur.
    *   **`mcr.microsoft.com/windows:<tag>`:** Windows 10/11 uyumluluğu için (Server Core'a benzer ama farklı lisanslama).
    *   Ayrıca IIS, SQL Server, .NET Framework SDK gibi hazır uygulama imajları da bulunur.
*   **Dockerfile Direktifleri ve Kullanım:** Linux Dockerfile'larındaki direktiflerin (`FROM`, `RUN`, `COPY`, `WORKDIR`, `EXPOSE`, `CMD`, `ENTRYPOINT`, `ENV`) çoğu Windows konteynerleri için de geçerlidir. Ancak:
    *   `RUN` komutları Windows kabuğunda (varsayılan `cmd /S /C`) veya PowerShell'de (`SHELL ["powershell", "-Command"]`) çalıştırılır. Komutlar Windows sözdiziminde olmalıdır (`RUN mkdir C:\app`, `RUN powershell -Command Install-WindowsFeature Web-Server`).
    *   Dosya yolları Windows formatında (`C:\path\to\file`) kullanılır.
    *   Temel imaj `FROM mcr.microsoft.com/...` ile başlar.
    *   Docker Desktop veya Docker Engine'in Windows konteyner moduna geçirilmesi gerekir (genellikle Docker Desktop tepsisindeki ikon üzerinden "Switch to Windows containers..." seçeneği ile).

## ARM Mimarisi ve Multi-Arch İmajlar

*   **Artan ARM Mimarisi Kullanımı:** Geleneksel olarak sunucular ve masaüstü bilgisayarlar Intel/AMD'nin x86\_64 (veya amd64) mimarisini kullanırken, son yıllarda ARM mimarisi (arm64, aarch64) özellikle mobil cihazlar, IoT cihazları (Raspberry Pi gibi), bazı dizüstü bilgisayarlar (Apple Silicon M1/M2/M3 çipli Mac'ler) ve hatta bulut sunucularında (AWS Graviton işlemcileri, Azure Ampere Altra) giderek daha popüler hale gelmiştir. ARM genellikle daha düşük güç tüketimi ve bazen daha iyi fiyat/performans oranı sunar.
*   **Mimari Uyumluluğu Sorunu:** Bir CPU mimarisi için derlenmiş bir program (ve dolayısıyla bir Docker imajı) doğrudan başka bir mimaride çalışmaz. Örneğin, standart bir amd64 Ubuntu imajı bir Raspberry Pi (arm) üzerinde çalışmaz veya tersi.
*   **Docker Desteği:** Docker, hem ARM mimarisi üzerinde Docker Engine'in çalışmasını (Docker Engine for ARM) hem de farklı mimariler için imaj oluşturmayı ve çalıştırmayı destekler.
*   **Multi-Arch İmajlar (Manifest Lists):** Bu sorun için en zarif çözüm, "multi-arch" veya "multi-platform" imajlar kullanmaktır. Bu, aslında tek bir imaj etiketi (`ubuntu:latest` veya `my-app:1.0` gibi) altında birden fazla mimariye (amd64, arm64v8, arm32v7 vb.) özel imajların bir listesini (manifest list) tutan bir yapıdır. Bir istemci (`docker pull`) bu etiketi istediğinde, Docker daemon veya registry, istemcinin kendi çalıştığı mimariye uygun olan imajı manifest listesinden otomatik olarak seçer ve indirir. Bu sayede kullanıcılar farklı mimarileri düşünmek zorunda kalmaz, aynı etiketi kullanırlar. Docker Hub'daki resmi imajların çoğu artık multi-arch desteklidir.
*   **Multi-Arch Build (`docker buildx`):** Kendi uygulamanız için multi-arch imajlar oluşturmak eskiden karmaşıktı, ancak Docker'ın `buildx` eklentisi (BuildKit tabanlı) bunu çok kolaylaştırmıştır. `docker buildx build` komutu, `--platform` seçeneği ile hedef alınacak mimarilerin bir listesini alır ve tek bir komutla tüm bu platformlar için imajları (gerekiyorsa QEMU emülasyonu kullanarak cross-compiling ile) oluşturup bunları tek bir multi-arch manifest altında birleştirerek registry'ye push edebilir.
    ```bash
    # Örnek: Hem amd64 hem de arm64 için build edip Docker Hub'a push etme
    # Önce bir buildx builder oluşturmak gerekebilir (varsayılan kullanılmıyorsa):
    # docker buildx create --name mybuilder --use
    docker buildx build --platform linux/amd64,linux/arm64/v8 \
      -t yourdockerhubuser/my-multiarch-app:latest \
      -t yourdockerhubuser/my-multiarch-app:1.0 \
      --push .
    # --push seçeneği build bittikten sonra imajları ve manifest listesini registry'ye yükler.
    ```
    Bu sayede uygulamanız farklı donanımlarda sorunsuz çalışabilir.

## Rootless Docker

*   **Amaç ve Motivasyon:** Standart Docker kurulumunda, Docker daemon (`dockerd`) genellikle `root` kullanıcısı olarak çalışır. Bu, daemon'a host sistemi üzerinde geniş yetkiler verir (ağları yönetme, dosya sistemine erişme, kernel ile etkileşim kurma). Eğer daemon'da veya onunla etkileşimde (API üzerinden) bir güvenlik açığı bulunursa veya bir konteynerden kaçış (container escape) başarılırsa, saldırgan host üzerinde `root` yetkileri elde edebilir. Rootless Docker, bu riski azaltmak amacıyla Docker daemon'ı ve dolayısıyla onun tarafından yönetilen konteynerleri *root olmayan* (unprivileged) normal bir kullanıcı olarak çalıştırmayı sağlayan bir moddur.
*   **Nasıl Çalışır?:** Rootless mod, Linux kernel'inin `user namespaces` özelliğini temel alır. User namespaces, bir kullanıcının kendi izole edilmiş namespace'i içinde sanki `root` (UID 0) imiş gibi görünmesini sağlar, ancak bu yetkiler sadece o namespace içinde geçerlidir ve host sistemi üzerinde gerçek `root` yetkilerine sahip olmaz. Rootless Docker, daemon'ı bu kullanıcı namespace'i içinde çalıştırır. Ayrıca ağ için `slirp4netns` gibi userspace ağ çözümleri ve depolama için `fuse-overlayfs` gibi userspace dosya sistemleri kullanır.
*   **Kurulum ve Kullanım:** Rootless modun kurulumu normal Docker kurulumundan biraz farklıdır ve ek bağımlılıklar (`uidmap`, `slirp4netns`, `fuse-overlayfs`) gerektirebilir. Genellikle ilgili kullanıcı için özel bir script çalıştırılarak yapılır. Kurulduktan sonra, ilgili kullanıcı Docker komutlarını (`docker ps`, `docker run` vb.) `sudo` kullanmadan doğrudan kendi oturumunda çalıştırabilir. Docker daemon, kullanıcı oturumuyla birlikte başlar ve biter (veya systemd user service olarak yönetilebilir). Detaylı kurulum adımları resmi dokümantasyonda bulunur: <https://docs.docker.com/engine/security/rootless/>
*   **Kısıtlamalar ve Farklılıklar:** Rootless mod, artan güvenliğe karşılık bazı kısıtlamalar ve farklılıklar getirir:
    *   **Ağ:** `--network=host` modu kullanılamaz. Ayrıcalıklı (privileged) portları (< 1024) doğrudan host'a bind edemez (port yönlendirme veya farklı port kullanma gerekir). Ağ performansı (özellikle `slirp4netns` kullanılıyorsa) normal Docker'a göre daha düşük olabilir.
    *   **Kaynak Limitleri (cgroups):** cgroups v1 ile kaynak (CPU, bellek) limitleri uygulanamaz. cgroups v2 ve systemd entegrasyonu ile limitler uygulanabilir hale gelmiştir, ancak yapılandırma normal Docker'dan farklı olabilir.
    *   **Depolama Sürücüleri:** Tüm depolama sürücüleri desteklenmeyebilir. Genellikle `overlayfs` (kernel desteği varsa) veya `fuse-overlayfs` kullanılır. `vfs` daha yavaş bir alternatiftir.
    *   **Cihaz Erişimi:** `--privileged` modu çalışmaz ve `--device` ile cihaz eklemek genellikle mümkün değildir.
    *   **Bazı Özellikler:** AppArmor, Checkpoint/Restore, Overlay ağları gibi bazı özellikler desteklenmeyebilir veya kısıtlı olabilir.
*   **Öneri:** Güvenliğin en yüksek öncelik olduğu ortamlarda (özellikle çok kullanıcılı sistemlerde veya paylaşılan host'larda) ve yukarıdaki kısıtlamalar kabul edilebilirse, Rootless Docker kullanmak güvenlik duruşunu önemli ölçüde iyileştiren değerli bir pratiktir. Normal geliştirme veya tek kullanıcılı sistemler için standart Docker genellikle yeterli olabilir, ancak risklerin farkında olunmalıdır.

# Sonuç ve Öğrenme Kaynakları

Docker, modern yazılım geliştirme, test etme ve dağıtma (deployment) süreçlerinin temel taşlarından biri haline gelmiştir. Konteynerleştirme teknolojisi, uygulamaları ve bağımlılıklarını standart, taşınabilir ve izole birimler halinde paketleyerek; geliştirme ortamından üretime kadar tutarlılık, hız, verimlilik ve ölçeklenebilirlik gibi sayısız avantaj sunmaktadır. Geliştiricilerin "benim makinemde çalışıyordu" sorunundan kurtulmasını sağlarken, operasyon ekiplerinin de altyapıyı daha verimli yönetmesine ve dağıtımları otomatikleştirmesine olanak tanımıştır.

Bu rehber boyunca, Docker'ın ne olduğundan ve ne olmadığından başlayarak temel kavramlarına (imajlar, konteynerler, volume'ler, ağlar), mimarisine ve kurulumuna değindik. Ardından, Docker CLI komutlarını kullanarak imajları ve konteynerleri nasıl yöneteceğimizi, Dockerfile ile kendi imajlarımızı nasıl oluşturacağımızı ve en iyi pratikleri öğrendik. Docker Compose ile çoklu konteynerli uygulamaları nasıl kolayca tanımlayıp yöneteceğimizi gördük. Docker Swarm ile konteyner orkestrasyonunun temellerine bir giriş yaptık. Konteyner güvenliğinin önemini vurgulayarak imaj, çalışma zamanı, secret yönetimi, ağ ve host güvenliği konularındaki en iyi uygulamaları tartıştık. Son olarak, konteyner ortamlarında izleme (monitoring) ve loglama (logging) stratejilerini, CI/CD süreçlerine Docker entegrasyonunu, yaygın sorunları giderme yöntemlerini ve bazı ileri seviye konuları ele aldık.

Unutmayın ki Docker gibi pratik bir teknolojiyi öğrenmenin ve gerçekten ustalaşmanın en etkili yolu, sürekli olarak **pratik yapmaktır**. Kendi projeleriniz için Dockerfile'lar yazın, farklı temel imajları ve Dockerfile direktiflerini deneyin, Docker Compose ile farklı uygulama yığınlarını modelleyin, Docker Swarm veya yerel bir Kubernetes kümesi (Docker Desktop, Minikube, Kind, K3s) üzerinde denemeler yaparak orkestrasyon kavramlarını pekiştirin. Karşılaştığınız sorunları araştırarak ve çözmeye çalışarak en kalıcı öğrenmeyi sağlarsınız.

Docker ve etrafındaki konteyner ekosistemi (Kubernetes, OCI, CRI, CNI, CSI, Service Mesh, Serverless vb.) sürekli olarak gelişmekte ve yenilenmektedir. Yeni araçlar, özellikler, standartlar ve en iyi uygulamalar düzenli olarak ortaya çıkmaktadır. Bu dinamik alanda güncel kalmak ve öğrenmeye devam etmek, teknolojiden en iyi şekilde faydalanmak için önemlidir.

Bu rehberin, Docker dünyasına adım atarken veya mevcut bilgilerinizi pekiştirirken size sağlam bir temel ve yol haritası sunmasını umuyoruz. Konteynerleştirme yolculuğunuzda başarılar dileriz!

## Faydalı Kaynaklar

Docker ve ilgili konteyner teknolojileri hakkında daha fazla bilgi edinmek, güncel kalmak ve sorunlarınıza çözüm bulmak için başvurabileceğiniz bazı değerli kaynaklar:

*   **Resmi Docker Dokümantasyonu:** Her zaman ilk başvurulması gereken, en kapsamlı, doğru ve güncel bilgi kaynağıdır. Öğreticiler, kavram açıklamaları, komut referansları, API belgeleri ve en iyi pratikler burada bulunur.
    *   Ana Sayfa: <https://docs.docker.com/>
    *   Get Started Tutorial: <https://docs.docker.com/get-started/>
    *   Docker Engine CLI Referansı: <https://docs.docker.com/engine/reference/commandline/cli/>
    *   Dockerfile Referansı: <https://docs.docker.com/engine/reference/builder/>
    *   Compose File Referansı: <https://docs.docker.com/compose/compose-file/>
    *   Dockerfile Best Practices: <https://docs.docker.com/develop/develop-images/dockerfile_best-practices/>
    *   Docker Security: <https://docs.docker.com/engine/security/>
    *   Rootless Mode: <https://docs.docker.com/engine/security/rootless/>
*   **Docker Hub:** Halka açık Docker imajlarının ana deposu. Resmi imajları, topluluk imajlarını aramak, keşfetmek ve kendi imajlarınızı yayınlamak için kullanılır: <https://hub.docker.com/>
*   **Play with Docker (PWD):** Tarayıcı üzerinden ücretsiz, sınırlı süreli Docker ortamları (terminal erişimi olan sanal makineler) sunan harika bir öğrenme platformudur. Hızlıca komutları denemek veya Docker Swarm kümesi kurmak için idealdir: <https://labs.play-with-docker.com/>
*   **Docker Blog:** Docker'dan en son haberler, duyurular, yeni özellikler ve teknik makaleler için: <https://www.docker.com/blog/>
*   **Awesome Docker (GitHub Listesi):** Docker ile ilgili harika araçların, kütüphanelerin, kaynakların, öğreticilerin ve projelerin derlendiği, topluluk tarafından yönetilen kapsamlı bir liste: <https://github.com/veggiemonk/awesome-docker>
*   **Stack Overflow (Docker Etiketi):** Karşılaştığınız spesifik sorunlara çözüm bulmak veya sorular sormak için en popüler platformlardan biri: <https://stackoverflow.com/questions/tagged/docker>
*   **KodeKloud, A Cloud Guru, Udemy, Coursera vb.:** Docker ve Kubernetes üzerine interaktif laboratuvarlar ve video kursları sunan birçok online eğitim platformu bulunmaktadır (bazıları ücretli).
*   **Kubernetes Dokümantasyonu:** Konteyner orkestrasyonunda bir sonraki adımı atmak isteyenler için Kubernetes'in resmi dokümantasyonu vazgeçilmezdir: <https://kubernetes.io/docs/>
*   **CNCF (Cloud Native Computing Foundation):** Kubernetes, Prometheus, Fluentd, containerd gibi birçok önemli konteyner ekosistemi projesinin evi olan vakfın web sitesi ve projeleri: <https://www.cncf.io/>

Bu rehberin Docker yolculuğunuzda size faydalı olmasını umuyoruz. Başarılar!

---

# Komut Referansı

Bu bölümde, rehber boyunca bahsedilen temel Docker ve Docker Compose komutları, hızlı başvuru amacıyla kategorize edilmiş bir şekilde listelenmektedir. Her komutun tüm seçenekleri burada yer almamaktadır; daha detaylı bilgi için komutun kendisine `--help` seçeneğini ekleyerek (`docker <komut> --help`) veya resmi Docker dokümantasyonuna başvurarak inceleyebilirsiniz.

## Docker Kurulum, Bilgi ve Oturum Komutları

1.  **`docker --version`**
    *   **Açıklama:** Yüklü Docker istemci (CLI) sürümünü kısaca gösterir.

2.  **`docker version`**
    *   **Açıklama:** Hem Docker İstemcisi hem de Docker Motoru (Daemon/Server) için ayrıntılı sürüm ve API bilgilerini gösterir.

3.  **`docker info`**
    *   **Açıklama:** Docker kurulumu hakkında sistem genelinde (konteyner/imaj sayısı, depolama sürücüsü, ağlar, volume'ler, OS, kernel, Swarm durumu vb.) detaylı bilgi gösterir. Sorun gidermede çok önemlidir.

4.  **`docker login [<server>]`**
    *   **Açıklama:** Bir Docker registry'ye (varsayılan olarak Docker Hub) giriş yapar. Özel registry için sunucu adresi belirtilir.

5.  **`docker logout [<server>]`**
    *   **Açıklama:** Bir Docker registry'den çıkış yapar.

## Imaj Yönetimi Komutları

6.  **`docker pull <imaj>[:<etiket>]`**
    *   **Açıklama:** Bir imajı veya depoyu belirtilen etiketle (varsayılan 'latest') registry'den indirir.

7.  **`docker images`** veya **`docker image ls`**
    *   **Açıklama:** Lokal makinede bulunan Docker imajlarını listeler (REPOSITORY, TAG, IMAGE ID, CREATED, SIZE).

8.  **`docker build [SEÇENEKLER] -t <isim>[:<etiket>] <yol|URL|->`**
    *   **Açıklama:** Belirtilen build bağlamındaki (genellikle '.') bir Dockerfile'dan imaj oluşturur ve etiketler. (`-f`, `--build-arg`, `--no-cache`, `--platform`, `--target` sık kullanılan seçenekler)

9.  **`docker tag <kaynak_imaj>[:<etiket>] <hedef_imaj>[:<etiket>]`**
    *   **Açıklama:** Mevcut bir imaja (kaynak) yeni bir isim ve/veya etiket (hedef) verir. Asıl imajı kopyalamaz, sadece referans oluşturur. Registry'ye push etmeden önce kullanılır.

10. **`docker push <isim>[:<etiket>]`**
    *   **Açıklama:** Lokaldeki bir imajı bir Docker registry'ye (genellikle Docker Hub veya özel registry) yükler. (Önce `docker login` gerekir)

11. **`docker rmi <imaj> [<imaj>...]`** veya **`docker image rm <imaj>...`**
    *   **Açıklama:** Bir veya daha fazla lokal imajı (IMAGE ID veya isim:etiket ile) siler. (`-f` ile zorla silme)

12. **`docker image prune [-a] [-f]`**
    *   **Açıklama:** Kullanılmayan imajları siler. Varsayılan olarak sadece dangling (etiketsiz) imajları siler. `-a` ile herhangi bir konteyner tarafından kullanılmayan tüm imajları siler. `-f` onay istemez.

13. **`docker save -o <dosya.tar> <imaj> [<imaj>...]`** veya **`docker image save ... > dosya.tar`**
    *   **Açıklama:** Bir veya daha fazla Docker imajını (tüm katmanlarıyla) bir tar arşiv dosyasına kaydeder.

14. **`docker load -i <dosya.tar>`** veya **`docker image load < dosya.tar`**
    *   **Açıklama:** Bir tar arşivinden (`docker save` ile oluşturulmuş) imaj(lar)ı yükler.

15. **`docker history <imaj>`**
    *   **Açıklama:** Bir imajın katman geçmişini (oluşturma komutları, boyutları vb.) gösterir.

16. **`docker inspect <imaj> [<imaj>...]`** veya **`docker image inspect <imaj>...`**
    *   **Açıklama:** Bir veya daha fazla imaj hakkında yapılandırma, katmanlar, ortam değişkenleri gibi detaylı JSON formatında bilgi gösterir.

## Konteyner Yaşam Döngüsü Komutları

17. **`docker run [SEÇENEKLER] <imaj> [<komut>] [<arg>...]`**
    *   **Açıklama:** Bir imajdan yeni bir konteyner oluşturur ve hemen başlatır. En çok kullanılan komutlardan biridir. (`-d`, `-it`, `-p`, `-v`, `--name`, `--rm`, `-e`, `--network`, `--restart`, `--memory`, `--cpus`, `--user`, `--read-only`, `--cap-add/drop` sık kullanılan seçeneklerdir.)

18. **`docker ps [-a] [-q] [--filter ...]`** veya **`docker container ls [-a] ...`**
    *   **Açıklama:** Çalışan konteynerleri listeler. `-a` ile durdurulmuş olanları da gösterir. `-q` sadece ID'leri listeler. `--filter` ile filtreleme yapılır.

19. **`docker start <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Durdurulmuş bir veya daha fazla konteyneri başlatır.

20. **`docker stop [-t <saniye>] <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Çalışan bir veya daha fazla konteyneri düzgünce durdurur (önce SIGTERM, sonra SIGKILL). `-t` bekleme süresini ayarlar.

21. **`docker kill [-s <sinyal>] <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Çalışan bir veya daha fazla konteynere belirtilen sinyali (varsayılan SIGKILL) göndererek zorla durdurur.

22. **`docker restart [-t <saniye>] <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Bir veya daha fazla konteyneri yeniden başlatır (stop + start).

23. **`docker rm [-f] [-v] <konteyner> [<konteyner>...]`** veya **`docker container rm <konteyner>...`**
    *   **Açıklama:** Bir veya daha fazla (varsayılan olarak durdurulmuş) konteyneri siler. `-f` çalışan konteyneri zorla siler (önce kill eder). `-v` konteynere bağlı anonim volume'leri de siler.

24. **`docker container prune [-f]`**
    *   **Açıklama:** Durdurulmuş tüm konteynerleri tek seferde siler. `-f` onay istemez.

25. **`docker pause <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Bir konteyner içindeki tüm süreçleri geçici olarak duraklatır (cgroups freezer kullanarak).

26. **`docker unpause <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Duraklatılmış bir konteynerdeki süreçleri devam ettirir.

27. **`docker wait <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Belirtilen konteyner(ler) durana kadar bekler ve son konteynerin çıkış kodunu yazdırır. Scripting için kullanışlıdır.

28. **`docker rename <eski_isim> <yeni_isim>`**
    *   **Açıklama:** Bir konteyneri yeniden adlandırır.

29. **`docker update [SEÇENEKLER] <konteyner> [<konteyner>...]`**
    *   **Açıklama:** Çalışan bir veya daha fazla konteynerin kaynak sınırları (`--cpus`, `--memory`, `--restart` politikası vb.) gibi yapılandırmalarını günceller.

30. **`docker create [SEÇENEKLER] <imaj> [<komut>] [<arg>...]`**
    *   **Açıklama:** `docker run` gibi yeni bir konteyner oluşturur ancak başlatmaz. Konteyner `docker start` ile daha sonra başlatılabilir.

## Konteyner Etkileşim ve İnceleme Komutları

31. **`docker exec [SEÇENEKLER] <konteyner> <komut> [<arg>...]`**
    *   **Açıklama:** Halihazırda çalışan bir konteyner içinde yeni bir komut çalıştırır. (`-it` ile etkileşimli kabuk açmak çok yaygındır.)

32. **`docker logs [SEÇENEKLER] <konteyner>`**
    *   **Açıklama:** Bir konteynerin loglarını (stdout/stderr akışını) gösterir. (`-f` ile canlı takip, `--tail`, `--since`, `-t` sık kullanılan seçenekler.)

33. **`docker inspect <konteyner> [<konteyner>...]`** veya **`docker container inspect <konteyner>...`**
    *   **Açıklama:** Bir veya daha fazla konteyner hakkında IP adresi, portlar, volume'ler, ağlar, durum, yapılandırma gibi detaylı JSON formatında bilgi gösterir.

34. **`docker stats [<konteyner>...]`**
    *   **Açıklama:** Çalışan konteynerlerin CPU, RAM, Ağ G/Ç, Disk G/Ç gibi kaynak kullanım istatistiklerini canlı olarak gösteren bir terminal arayüzü sunar.

35. **`docker attach <konteyner>`**
    *   **Açıklama:** Çalışan bir konteynerin standart girdi (stdin), standart çıktı (stdout) ve standart hata (stderr) akışlarına bağlanır. Genellikle `docker run -it` ile başlatılan ve ön planda çalışan interaktif süreçler için kullanılır. (Çıkmak için `Ctrl+P Ctrl+Q`)

36. **`docker cp <kaynak_yol> <konteyner>:<hedef_yol>`**
    **`docker cp <konteyner>:<kaynak_yol> <hedef_yol>`**
    *   **Açıklama:** Host makinesi ile bir konteyner arasında dosya veya dizinleri kopyalar. Konteyner çalışıyor veya durmuş olabilir.

37. **`docker diff <konteyner>`**
    *   **Açıklama:** Konteynerin dosya sisteminde, oluşturulduktan sonra yapılan değişiklikleri (eklenen, değiştirilen, silinen dosyalar) gösterir.

38. **`docker top <konteyner>`**
    *   **Açıklama:** Belirtilen konteyner içinde çalışan süreçleri listeler (host'taki `ps` gibi anlık görüntü).

39. **`docker port <konteyner> [<özel_port>]`**
    *   **Açıklama:** Belirtilen konteyner için port yönlendirmelerini (public port -> private port eşleşmeleri) listeler. Özel port belirtilirse sadece onun eşleşmesini gösterir.

40. **`docker events [SEÇENEKLER]`**
    *   **Açıklama:** Docker daemon tarafından üretilen olayları (konteyner start/stop, imaj pull/delete vb.) gerçek zamanlı olarak akış halinde gösterir. (`--filter` ile filtrelenebilir.)

## Ağ Yönetimi Komutları

41. **`docker network ls`**
    *   **Açıklama:** Mevcut Docker ağlarını listeler (NETWORK ID, NAME, DRIVER, SCOPE).

42. **`docker network create [SEÇENEKLER] <ağ_adı>`**
    *   **Açıklama:** Yeni bir Docker ağı oluşturur. (`--driver bridge|overlay|...`, `--subnet`, `--gateway`, `--attachable` gibi seçenekler) Varsayılan sürücü 'bridge'dir.

43. **`docker network rm <ağ> [<ağ>...]`**
    *   **Açıklama:** Bir veya daha fazla Docker ağını siler. (Ağa bağlı konteyner yoksa silinebilir.)

44. **`docker network prune [-f]`**
    *   **Açıklama:** Herhangi bir konteyner tarafından kullanılmayan tüm ağları siler. `-f` onay istemez.

45. **`docker network inspect <ağ> [<ağ>...]`**
    *   **Açıklama:** Bir veya daha fazla ağ hakkında yapılandırma, bağlı konteynerler, IPAM ayarları gibi detaylı JSON formatında bilgi gösterir.

46. **`docker network connect [SEÇENEKLER] <ağ> <konteyner>`**
    *   **Açıklama:** Çalışan bir konteyneri belirtilen ağa bağlar. Bir konteyner birden fazla ağa bağlanabilir.

47. **`docker network disconnect [-f] <ağ> <konteyner>`**
    *   **Açıklama:** Bir konteynerin belirtilen ağ ile bağlantısını keser. `-f` zorla keser.

## Volume (Birim) Yönetimi Komutları

48. **`docker volume ls [-q] [--filter ...]`**
    *   **Açıklama:** Mevcut Docker volume'lerini listeler (DRIVER, VOLUME NAME). `-q` sadece isimleri listeler.

49. **`docker volume create [SEÇENEKLER] [<volume_adı>]`**
    *   **Açıklama:** Yeni bir Docker volume'u oluşturur. (`--driver`, `--opt` ile özel sürücü ve seçenekler belirtilebilir.) İsim verilmezse rastgele bir isimle oluşturulur.

50. **`docker volume rm [-f] <volume> [<volume>...]`**
    *   **Açıklama:** Bir veya daha fazla Docker volume'ünü siler. (**Dikkat: İçindeki veriler kalıcı olarak silinir!**) `-f` zorla siler (eğer bir konteyner tarafından kullanılıyorsa bile, önerilmez).

51. **`docker volume prune [-f]`**
    *   **Açıklama:** Herhangi bir konteyner tarafından kullanılmayan tüm lokal volume'leri siler. (**Dikkat: Veri kaybına neden olabilir!**) `-f` onay istemez.

52. **`docker volume inspect <volume> [<volume>...]`**
    *   **Açıklama:** Bir veya daha fazla volume hakkında host üzerindeki bağlantı noktası (`Mountpoint`), sürücü, etiketler gibi detaylı JSON formatında bilgi gösterir.

## Docker Compose Komutları (CLI Plugin: `docker compose`)

*Not: Eski `docker-compose` (tireli) komutu yerine modern Docker sürümleriyle gelen `docker compose` (boşluklu) CLI plugin'inin kullanılması tavsiye edilir.*

53. **`docker compose [-f <file>] up [OPTIONS] [<servis>...]`**
    *   **Açıklama:** Compose dosyasındaki servisleri oluşturur (gerekiyorsa build eder), başlatır ve bağlar. Varsayılan olarak logları gösterir. (`-d` arka planda başlatır, `--build` build etmeye zorlar, `--force-recreate` yeniden oluşturur, `--scale <servis>=<sayı>` ölçekler.)

54. **`docker compose [-f <file>] down [OPTIONS]`**
    *   **Açıklama:** `up` ile oluşturulan konteynerleri, ağları durdurur ve kaldırır. (`--volumes` volume'leri de kaldırır - dikkat!, `--rmi <type>` imajları kaldırır, `--remove-orphans` yetim konteynerleri kaldırır.)

55. **`docker compose [-f <file>] ps [<servis>...]`**
    *   **Açıklama:** Compose projesi tarafından yönetilen konteynerlerin durumunu listeler.

56. **`docker compose [-f <file>] logs [OPTIONS] [<servis>...]`**
    *   **Açıklama:** Servislerin loglarını gösterir veya akış halinde takip eder (`-f`, `--tail`, `-t`).

57. **`docker compose [-f <file>] build [OPTIONS] [<servis>...]`**
    *   **Açıklama:** Compose dosyasında `build` direktifi ile tanımlanmış servisler için imajları (yeniden) oluşturur (`--no-cache`, `--pull`).

58. **`docker compose [-f <file>] pull [OPTIONS] [<servis>...]`**
    *   **Açıklama:** Compose dosyasında `image` direktifi ile tanımlanmış servisler için gerekli imajları registry'den çeker veya günceller.

59. **`docker compose [-f <file>] start [<servis>...]`**
    *   **Açıklama:** Daha önce `up` ile oluşturulmuş ve `stop` ile durdurulmuş servis konteynerlerini başlatır.

60. **`docker compose [-f <file>] stop [-t <saniye>] [<servis>...]`**
    *   **Açıklama:** Çalışan servis konteynerlerini kaldırmadan durdurur.

61. **`docker compose [-f <file>] restart [OPTIONS] [<servis>...]`**
    *   **Açıklama:** Servis konteynerlerini yeniden başlatır (stop + start).

62. **`docker compose [-f <file>] rm [OPTIONS] [<servis>...]`**
    *   **Açıklama:** Durdurulmuş servis konteynerlerini kaldırır (`-f` onay istemez, `-s` önce durdurur, `-v` anonim volume'leri siler).

63. **`docker compose [-f <file>] exec [OPTIONS] <servis> <komut> [<arg>...]`**
    *   **Açıklama:** Çalışan bir servis konteynerinin içinde bir komut çalıştırır.

64. **`docker compose [-f <file>] config [OPTIONS]`**
    *   **Açıklama:** Compose dosyasını (varsa `.env` ile birleştirilmiş, enterpolasyon yapılmış ve doğrulanmış) terminale yazdırır. Yapılandırmayı kontrol etmek için kullanışlıdır.

65. **`docker compose [-f <file>] run [OPTIONS] <servis> [<komut>] [<arg>...]`**
    *   **Açıklama:** Belirli bir servis için tek seferlik bir komut çalıştırır (yeni bir konteyner başlatır). Genellikle migration, test veya yönetimsel görevler için kullanılır. (`--rm` otomatik siler, `-e`, `-v`, `-p` seçenekleri kullanılabilir.)

66. **`docker compose version`**
    *   **Açıklama:** Docker Compose CLI Plugin sürümünü gösterir.

## Sistem Yönetimi ve Temizlik Komutları

67. **`docker system prune [OPTIONS]`**
    *   **Açıklama:** Tüm kullanılmayan Docker verilerini (durdurulmuş konteynerler, kullanılmayan ağlar, dangling imajlar, build cache) toplu olarak kaldırır. (`-a` tüm kullanılmayan imajları, `--volumes` tüm kullanılmayan lokal volume'leri de siler - **dikkat!**, `-f` onay istemez.)

68. **`docker system df [-v]`**
    *   **Açıklama:** Docker'ın disk kullanımını nesne türlerine göre özetler. `-v` daha detaylı bilgi verir.

69. **`docker system events [OPTIONS]`** (=`docker events`)
    *   **Açıklama:** Docker daemon'dan sistem geneli olayları akış halinde gösterir.

70. **`docker system info`** (=`docker info`)
    *   **Açıklama:** Docker sistemi hakkında detaylı bilgi gösterir.

## Gelişmiş, Swarm ve Çeşitli Komutlar

71. **`docker commit [SEÇENEKLER] <konteyner> [<depo>[:<etiket>]]`**
    *   **Açıklama:** Çalışan veya durdurulmuş bir konteynerin dosya sistemindeki değişikliklerden yeni bir Docker imajı oluşturur. (Tekrarlanabilirlik için genellikle Dockerfile tercih edilir.)

72. **`docker export -o <dosya.tar> <konteyner>`**
    *   **Açıklama:** Bir konteynerin dosya sistemini (imaj katmanları veya meta veri olmadan) bir tar arşivi olarak dışa aktarır.

73. **`docker import <dosya.tar|URL|-> [<depo>[:<etiket>]]`**
    *   **Açıklama:** Bir tarball içeriğini (`docker export` ile oluşturulan veya başka bir rootfs) tek katmanlı yeni bir imaj olarak içe aktarır.

    **--- Swarm Komutları (Özet - Detaylar Swarm bölümünde) ---**

74. **`docker swarm init`**
    *   **Açıklama:** Swarm modunu başlatır ve mevcut node'u ilk manager yapar.

75. **`docker swarm join`**
    *   **Açıklama:** Mevcut node'u worker veya manager olarak bir Swarm'a katırır.

76. **`docker swarm leave`**
    *   **Açıklama:** Mevcut node'u Swarm'dan ayırır.

77. **`docker node ls`**
    *   **Açıklama:** Swarm'daki node'ları listeler.

78. **`docker service create`**
    *   **Açıklama:** Swarm üzerinde yeni bir servis (konteyner grubu) oluşturur.

79. **`docker service ls`**
    *   **Açıklama:** Swarm'daki servisleri listeler.

80. **`docker service ps <servis>`**
    *   **Açıklama:** Bir servisin task'larını (konteynerlerini) listeler.

81. **`docker service scale <servis>=<sayı>`**
    *   **Açıklama:** Bir servisin replika sayısını değiştirir.

82. **`docker service update`**
    *   **Açıklama:** Bir servisin yapılandırmasını günceller (örn: imaj).

83. **`docker service rm <servis>`**
    *   **Açıklama:** Bir servisi kaldırır.

84. **`docker stack deploy -c <file> <stack>`**
    *   **Açıklama:** Bir Compose dosyası kullanarak uygulama yığınını dağıtır/günceller.

85. **`docker stack ls`**
    *   **Açıklama:** Dağıtılmış stack'leri listeler.

86. **`docker stack rm <stack>`**
    *   **Açıklama:** Bir stack'i ve kaynaklarını kaldırır.

87. **`docker secret create|ls|rm|inspect`**
    *   **Açıklama:** Swarm secret'larını yönetir.

88. **`docker config create|ls|rm|inspect`**
    *   **Açıklama:** Swarm config'lerini yönetir.

    **--- Buildx Komutları (Özet) ---**

89. **`docker buildx build [OPTIONS] PATH | URL | -`**
    *   **Açıklama:** BuildKit ile gelişmiş imaj build işlemi yapar (multi-platform, cache export vb.).

90. **`docker buildx ls`**
    *   **Açıklama:** Kullanılabilir builder instance'larını listeler.

91. **`docker buildx create`**
    *   **Açıklama:** Yeni bir builder instance oluşturur.

92. **`docker buildx use <builder>`**
    *   **Açıklama:** Varsayılan builder instance'ını değiştirir.

    **--- Plugin Komutları (Özet) ---**

93. **`docker plugin install|ls|enable|disable|rm <plugin>`**
    *   **Açıklama:** Docker eklentilerini (ağ, volume sürücüleri vb.) yönetir.

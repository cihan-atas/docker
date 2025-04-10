```markdown
# Kapsamlı Git & GitHub Rehberi

**Yazar:** Cihan Atas
**E-posta:** atascihan115@gmail.com

---

## 1. Önsöz

Bu rehber, Git versiyon kontrol sistemini ve GitHub gibi platformlarla etkileşimini sıfırdan başlayarak öğrenmek veya mevcut bilgisini derinleştirmek isteyen herkes için hazırlanmıştır. Temel kavramlardan başlayarak, günlük kullanımda sıkça ihtiyaç duyulan komutlara, dallanma stratejilerine, takım çalışması prensiplerine ve ileri düzey konulara kadar geniş bir yelpazeyi kapsamaktadır. Amacımız, Git'i etkili bir şekilde kullanmanız için size sağlam bir temel ve pratik bilgiler sunmaktır.

---

## 2. İçindekiler

*   [1. Önsöz](#1-önsöz)
*   [2. İçindekiler](#2-içindekiler)
*   [3. Giriş: Git Dünyasına İlk Adım](#3-giriş-git-dünyasına-ilk-adım)
    *   [3.1 Git Nedir?](#31-git-nedir)
    *   [3.2 Versiyon Kontrol Sistemi (VCS) Nedir?](#32-versiyon-kontrol-sistemi-vcs-nedir)
    *   [3.3 Git’in Avantajları Nelerdir?](#33-gitin-avantajları-nelerdir)
    *   [3.4 Git vs. Diğer VCS’ler](#34-git-vs-diğer-vcsler)
*   [4. Kurulum ve İlk Yapılandırma](#4-kurulum-ve-ilk-yapılandırma)
    *   [4.1 Git Kurulumu](#41-git-kurulumu)
    *   [4.2 Temel Yapılandırma (Zorunlu)](#42-temel-yapılandırma-zorunlu)
    *   [4.3 Metin Editörü Ayarları](#43-metin-editörü-ayarları)
    *   [4.4 SSH Anahtarı Oluşturma ve Platformlara Ekleme](#44-ssh-anahtarı-oluşturma-ve-platformlara-ekleme)
*   [5. Git’in Temel Taşları: Depo ve Temel Komutlar](#5-gitin-temel-taşları-depo-ve-temel-komutlar)
    *   [5.1 Depo (Repository) Kavramı](#51-depo-repository-kavramı)
    *   [5.2 Yeni Depo Başlatma ve Klonlama (`init`, `clone`)](#52-yeni-depo-başlatma-ve-klonlama-init-clone)
    *   [5.3 Değişiklikleri İzleme (The Three States & `status`)](#53-değişiklikleri-izleme-the-three-states--status)
    *   [5.4 Değişiklikleri Hazırlık Alanına Ekleme (Staging & `add`)](#54-değişiklikleri-hazırlık-alanına-ekleme-staging--add)
    *   [5.5 Commit Oluşturma (Değişiklikleri Kaydetme & `commit`)](#55-commit-oluşturma-değişiklikleri-kaydetme--commit)
    *   [5.6 İyi Commit Mesajları Yazma](#56-iyi-commit-mesajları-yazma)
    *   [5.7 Değişiklikleri Görüntüleme (Farklar & `diff`)](#57-değişiklikleri-görüntüleme-farklar--diff)
*   [6. Zaman Makinesi: Geçmişi Yönetme ve Geri Alma](#6-zaman-makinesi-geçmişi-yönetme-ve-geri-alma)
    *   [6.1 Commit Geçmişini Görüntüleme (`git log`)](#61-commit-geçmişini-görüntüleme-git-log)
    *   [6.2 Belirli Bir Commit'i İnceleme (`git show`)](#62-belirli-bir-commiti-inceleme-git-show)
    *   [6.3 Geri Alma İşlemleri](#63-geri-alma-işlemleri)
        *   [6.3.1 Son Commit'i Düzenleme (`--amend`)](#631-son-commiti-düzenleme---amend)
        *   [6.3.2 Hazırlık Alanından Dosya Çıkarma (`reset HEAD`/`restore --staged`)](#632-hazırlık-alanından-dosya-çıkarma-reset-headrestore---staged)
        *   [6.3.3 Çalışma Dizinindeki Değişiklikleri Geri Alma (`checkout --`/`restore`)](#633-çalışma-dizinindeki-değişiklikleri-geri-alma-checkout---restore)
        *   [6.3.4 Bir Commit'in Değişikliklerini Geri Alan Yeni Commit Oluşturma (`revert`)](#634-bir-commitin-değişikliklerini-geri-alan-yeni-commit-oluşturma-revert)
        *   [6.3.5 Geçmişteki Bir Duruma Dönme (`reset`)](#635-geçmişteki-bir-duruma-dönme-reset)
*   [7. Paralel Evrenler: Dallanma ve Birleştirme](#7-paralel-evrenler-dallanma-ve-birleştirme)
    *   [7.1 Branch (Dal) Nedir?](#71-branch-dal-nedir)
    *   [7.2 Branch Oluşturma, Geçiş Yapma ve Listeleme (`branch`, `checkout`)](#72-branch-oluşturma-geçiş-yapma-ve-listeleme-branch-checkout)
    *   [7.3 Branch Birleştirme (`merge`)](#73-branch-birleştirme-merge)
    *   [7.4 Merge Çakışmalarını (Conflict) Çözme](#74-merge-çakışmalarını-conflict-çözme)
    *   [7.5 Geçmişi Yeniden Yazma (`rebase`)](#75-geçmişi-yeniden-yazma-rebase)
    *   [7.6 Merge vs. Rebase: Ne Zaman Hangisini Kullanmalı?](#76-merge-vs-rebase-ne-zaman-hangisini-kullanmalı)
*   [8. Takım Çalışması: Uzak Depolarla Etkileşim](#8-takım-çalışması-uzak-depolarla-etkileşim)
    *   [8.1 Yerel (Local) vs. Uzak (Remote) Depo](#81-yerel-local-vs-uzak-remote-depo)
    *   [8.2 Uzak Depo Yönetimi (`remote`)](#82-uzak-depo-yönetimi-remote)
    *   [8.3 Uzak Depodaki Değişiklikleri Çekmeden Görme](#83-uzak-depodaki-değişiklikleri-çekmeden-görme)
    *   [8.4 Değişiklikleri Uzak Depodan Alma (`fetch`, `pull`)](#84-değişiklikleri-uzak-depodan-alma-fetch-pull)
    *   [8.5 Değişiklikleri Uzak Depoya Gönderme (`push`)](#85-değişiklikleri-uzak-depoya-gönderme-push)
    *   [8.6 Uzak İzleme Dalları (Remote-Tracking Branches)](#86-uzak-izleme-dalları-remote-tracking-branches)
    *   [8.7 Uzak Branch'leri Yönetme](#87-uzak-branchleri-yönetme)
*   [9. Pull Request / Merge Request Süreci](#9-pull-request--merge-request-süreci)
    *   [9.1 PR/MR Nedir?](#91-prmr-nedir)
    *   [9.2 PR/MR Oluşturma Adımları](#92-prmr-oluşturma-adımları)
    *   [9.3 Kod İnceleme (Code Review)](#93-kod-inceleme-code-review)
*   [10. Git Ustalığı: İleri Düzey Konular ve Teknikler](#10-git-ustalığı-ileri-düzey-konular-ve-teknikler)
    *   [10.1 Değişiklikleri Geçici Saklama (`stash`)](#101-değişiklikleri-geçici-saklama-stash)
    *   [10.2 Sürümleri İşaretleme (`tag`)](#102-sürümleri-işaretleme-tag)
    *   [10.3 Commit Ayıklama (`cherry-pick`)](#103-commit-ayıklama-cherry-pick)
    *   [10.4 İnteraktif Rebase (`rebase -i`) ile Geçmişi Düzenleme](#104-interaktif-rebase-rebase--i-ile-geçmişi-düzenleme)
    *   [10.5 Kayıp İşleri Bulma (`reflog`)](#105-kayıp-işleri-bulma-reflog)
    *   [10.6 Hatanın Kaynağını Bulma (`bisect`)](#106-hatanın-kaynağını-bulma-bisect)
    *   [10.7 Alt Modüller (`submodule`)](#107-alt-modüller-submodule)
    *   [10.8 Büyük Dosyaları Yönetme (Git LFS)](#108-büyük-dosyaları-yönetme-git-lfs)
    *   [10.9 Git Kancaları (`hooks`)](#109-git-kancaları-hooks)
*   [11. `.gitignore` Dosyası ve İncelikleri](#11-gitignore-dosyası-ve-incelikleri)
    *   [11.1 `.gitignore` Nasıl Çalışır?](#111-gitignore-nasıl-çalışır)
    *   [11.2 Yaygın Kullanım Desenleri](#112-yaygın-kullanım-desenleri)
    *   [11.3 Zaten Takip Edilen Dosyaları Yoksayma](#113-zaten-takip-edilen-dosyaları-yoksayma)
    *   [11.4 Global `.gitignore`](#114-global-gitignore)
*   [12. Verimli Çalışma: Popüler Git İş Akışları (Workflows)](#12-verimli-çalışma-popüler-git-iş-akışları-workflows)
    *   [12.1 Feature Branch Workflow](#121-feature-branch-workflow)
    *   [12.2 Gitflow Workflow](#122-gitflow-workflow)
    *   [12.3 GitHub Flow / GitLab Flow](#123-github-flow--gitlab-flow)
    *   [12.4 Forking Workflow](#124-forking-workflow)
*   [13. Sorun Giderme ve İpuçları](#13-sorun-giderme-ve-ipuçları)
    *   [13.1 "Detached HEAD" Durumu](#131-detached-head-durumu)
    *   [13.2 Yanlış Commit/Rebase Sonrası Eski Duruma Dönme (`reflog` ve `reset`)](#132-yanlış-commitrebase-sonrası-eski-duruma-dönme-reflog-ve-reset)
    *   [13.3 PR Öncesi Branch'i Güncelleme (`rebase`/`merge`, `--force-with-lease`)](#133-pr-öncesi-branchi-güncelleme-rebasemerge---force-with-lease)
    *   [13.4 Git Kısayolları (`alias`)](#134-git-kısayolları-alias)
*   [14. Git'in İç Yapısı: Temel Objeler (İsteğe Bağlı)](#14-gitin-iç-yapısı-temel-objeler-isteğe-bağlı)
    *   [14.1 Blob, Tree, Commit Objeleri](#141-blob-tree-commit-objeleri)
    *   [14.2 `.git` Klasörüne Kısa Bir Bakış](#142-git-klasörüne-kısa-bir-bakış)
*   [15. Ek Kaynaklar ve Sonraki Adımlar](#15-ek-kaynaklar-ve-sonraki-adım)

---

## 3. Giriş: Git Dünyasına İlk Adım

### 3.1 Git Nedir?

Git, Linus Torvalds tarafından (Linux çekirdeği geliştirilirken) oluşturulan, modern, **dağıtık** bir **versiyon kontrol sistemidir (VCS)**. Proje dosyaları üzerindeki değişiklikleri zaman içinde izlemenizi, farklı versiyonları yönetmenizi, önceki sürümlere dönebilmenizi ve özellikle takım halinde verimli çalışmanızı sağlar.

### 3.2 Versiyon Kontrol Sistemi (VCS) Nedir?

Dosya veya dosya setlerindeki değişiklikleri zaman içinde kaydeden bir sistemdir. Belirli bir versiyona geri dönmenize, değişiklikleri karşılaştırmanıza, kimin ne zaman hangi değişikliği yaptığını görmenize olanak tanır. Hataları ayıklamayı, yeni özellikler geliştirmeyi ve işbirliğini kolaylaştırır.

*   **Türleri:** Yerel VCS (eskiden), Merkezi VCS (CVCS - örn: SVN, CVS), Dağıtık VCS (DVCS - örn: Git, Mercurial). Git, dağıtık yapısıyla öne çıkar.

### 3.3 Git’in Avantajları Nelerdir?

*   **Dağıtık Yapı:** Her geliştiricinin projeyi *tüm geçmişiyle* birlikte tam bir kopyasına sahip olmasını sağlar. Bu, çevrimdışı çalışma, hız, yedeklilik ve esnek iş akışları anlamına gelir.
*   **Hız:** Çoğu işlem (commit, branch oluşturma, merge) yerel olarak yapıldığı için çok hızlıdır. Merkezi sistemlerdeki ağ gecikmeleri yoktur.
*   **Güvenlik:** Tüm veriler (commitler, dosyalar vb.) içeriğine göre SHA-1 hash algoritması ile güvence altına alınır. Veri bütünlüğü kritiktir.
*   **Güçlü Dallanma Modeli:** Özellik geliştirme, hata düzeltme gibi işlemler için bağımsız "dallar" (branch) oluşturup bunlar üzerinde çalışmak ve sonra ana kod tabanıyla birleştirmek (merge/rebase) çok kolay ve verimlidir.
*   **Açık Kaynak ve Popülerlik:** Geniş bir topluluğa sahip olup, endüstri standardı haline gelmiştir. Bol kaynak ve destek bulunur.

### 3.4 Git vs. Diğer VCS’ler

*   **Subversion (SVN):** Merkezi bir sistemdir. Tüm geçmiş merkezi sunucudadır. Çevrimdışı çalışma çok sınırlıdır. Dallanma ve birleştirme Git'e göre daha yavaş ve zahmetlidir.
*   **Mercurial (Hg):** Git gibi dağıtık bir sistemdir ve benzer özelliklere sahiptir. Ancak Git, topluluk desteği ve popülerlik açısından daha yaygın olarak kullanılmaktadır.

---

## 4. Kurulum ve İlk Yapılandırma

### 4.1 Git Kurulumu

*   **Windows:** Git for Windows ([https://gitforwindows.org/](https://gitforwindows.org/)) adresinden indirip kurun. (Kurulumda Git Bash, GUI ve shell entegrasyonu seçeneklerini işaretlemeniz önerilir.)
*   **macOS:**
    *   En kolay yol Homebrew ile: `brew install git`
    *   Alternatif olarak Xcode Command Line Tools ile gelir veya resmi siteden ([https://git-scm.com/download/mac](https://git-scm.com/download/mac)) indirilebilir.
*   **Linux (Debian/Ubuntu):** `sudo apt update && sudo apt install git`
*   **Linux (Fedora):** `sudo dnf install git`

Kurulumu doğrulamak için terminal veya komut istemcisinde aşağıdaki komutu çalıştırın:

```bash
git --version
```

### 4.2 Temel Yapılandırma (Zorunlu)

Git, yaptığınız her commit'e kimlik (ad ve e-posta) bilgilerinizi ekler. Bu, değişikliklerin kim tarafından yapıldığını takip etmek için kritiktir. Bu ayarları yapmadan commit atamazsınız veya atmamalısınız.

```bash
# Global ayar: Bu bilgisayardaki tüm Git depolarınız için geçerli olur
git config --global user.name "Adınız Soyadınız"
git config --global user.email "eposta@adresiniz.com"
```

Ayarlarınızı kontrol etmek için:

```bash
# Tüm ayarları gösterir (yerel, global, sistem)
git config --list
# Sadece global ayarları gösterir
git config --global --list
```

### 4.3 Metin Editörü Ayarları

Git, commit mesajı yazmak veya merge çakışmalarını çözmek gibi durumlarda bir metin editörüne ihtiyaç duyar. Varsayılan editörü değiştirebilirsiniz:

```bash
# VS Code için (komut satırından 'code' ile başlatılabiliyorsa ve kapanana kadar beklemesi için --wait)
git config --global core.editor "code --wait"

# Nano için
git config --global core.editor "nano"

# Vim için (genellikle varsayılan)
git config --global core.editor "vim"

# Sublime Text için (örnek - yolunuza göre değişebilir)
# git config --global core.editor "'C:/Program Files/Sublime Text 3/subl.exe' -w"
```

### 4.4 SSH Anahtarı Oluşturma ve Platformlara Ekleme

GitHub, GitLab, Bitbucket gibi platformlarla HTTPS yerine SSH üzerinden (daha güvenli ve pratik) iletişim kurmak için SSH anahtar çifti kullanılır.

**Anahtar Oluşturma:**

```bash
# Ed25519 (Modern ve önerilen)
ssh-keygen -t ed25519 -C "eposta@adresiniz.com"

# RSA (Eski ama hala yaygın)
# ssh-keygen -t rsa -b 4096 -C "eposta@adresiniz.com"
```

Komut size anahtarın kaydedileceği yeri (genellikle `~/.ssh/id_ed25519` veya `~/.ssh/id_rsa`) ve bir parola (passphrase - önerilir!) soracaktır. Enter'a basarak varsayılan konumu kabul edebilirsiniz. Parola, özel anahtarınızı ek koruma altına alır.

**SSH Agent'a Ekleme (Oturum boyunca parolayı tekrar sormaması için):**

```bash
# Agent'ı başlat (farklı shell'lerde farklı olabilir)
eval "$(ssh-agent -s)"

# Anahtarı agent'a ekle (dosya adını doğru yazdığınızdan emin olun)
ssh-add ~/.ssh/id_ed25519 # Eğer farklı bir isim veya RSA kullandıysanız onu yazın
```

Eğer anahtarı parola ile oluşturduysanız, burada parolayı girmeniz istenecektir.

**Public Key'i Kopyalama:**
Public anahtar (`.pub` uzantılı dosya), platformlara ekleyeceğiniz anahtardır. Private anahtarı (`.pub` olmayan) **ASLA** paylaşmayın!

```bash
# macOS:
pbcopy < ~/.ssh/id_ed25519.pub

# Linux (xclip kuruluysa):
xclip -selection clipboard < ~/.ssh/id_ed25519.pub

# Windows (Git Bash):
cat ~/.ssh/id_ed25519.pub | clip

# Manuel: Dosyayı bir metin editörüyle açıp içeriğini kopyalayın
# cat ~/.ssh/id_ed25519.pub
```

**Platforma Ekleme:**

*   **GitHub:** Settings -> SSH and GPG keys -> New SSH key
*   **GitLab:** User Settings (sağ üst profil ikonu) -> Preferences -> SSH Keys
*   **Bitbucket:** Personal settings (sol alt avatar) -> SSH keys

Kopyaladığınız public anahtarın tamamını (`ssh-ed25519 AAAAC3... eposta@adresiniz.com` gibi) ilgili alana yapıştırın ve bir isim verin (örn: "İş Laptopu", "Ev Bilgisayarı").

---

## 5. Git’in Temel Taşları: Depo ve Temel Komutlar

### 5.1 Depo (Repository) Kavramı

Bir Git deposu (repository veya kısaca "repo"), projenizin tüm dosyalarını, bu dosyaların geçmişini (commit'ler), dallarını (branch) ve diğer tüm Git meta verilerini içeren bir klasördür. Bu bilgilerin çoğu projenizin kök dizinindeki gizli `.git` klasöründe saklanır.

### 5.2 Yeni Depo Başlatma ve Klonlama (`init`, `clone`)

**Yeni Bir Proje İçin Git'i Başlatma (`init`):**
Mevcut bir proje klasörünü Git deposuna dönüştürmek için:

```bash
cd /path/to/your/project
git init
```

Bu komut, bulunduğunuz dizinde `.git` adında gizli bir alt klasör oluşturur ve projenizi Git kontrolüne alır.

**Mevcut Bir Depoyu Klonlama (`clone`):**
Uzak bir sunucudaki (örn: GitHub) bir depoyu kendi bilgisayarınıza kopyalamak için:

```bash
# SSH URL'si (önerilen, SSH ayarı yapıldıysa):
git clone git@github.com:kullaniciadi/depoadi.git

# HTTPS URL'si:
git clone https://github.com/kullaniciadi/depoadi.git

# Belirli bir klasör adı altında klonlamak için:
git clone <url> <yeni_klasor_adi>
```

Bu komut, `depoadi` (veya belirttiğiniz `yeni_klasor_adi`) adında bir klasör oluşturur, içine `.git` klasörünü ve projenin varsayılan branch'inin en son halini indirir. Ayrıca `origin` adında bir remote (uzak depo) bağlantısını otomatik olarak kurar.

### 5.3 Değişiklikleri İzleme (The Three States & `status`)

Git'te dosyalarınız temel olarak üç ana durumda bulunur:

1.  **Working Directory (Çalışma Dizini):** Proje dosyalarınızın diskteki hali. Burada değişiklik yapar, dosya ekler veya silersiniz.
2.  **Staging Area (Hazırlık Alanı / Index):** Bir sonraki commit'e dahil etmek istediğiniz değişikliklerin "hazırlandığı" bir ara alandır. `git add` ile dosyaları buraya eklersiniz. Bu, commit'e sadece istediğiniz değişiklikleri dahil etmenizi sağlar.
3.  **Repository (`.git` directory):** Commit'lediğiniz (yani kalıcı olarak kaydettiğiniz) proje anlık görüntülerinin (snapshot) ve tüm geçmişin saklandığı yerdir. `git commit` ile hazırlık alanındaki değişiklikler buraya kaydedilir.

Dosyaların bu üç alandaki durumunu görmek için en sık kullanacağınız komut:

```bash
git status
```

`git status` çıktısı size şunları söyler:

*   Hangi branch'te olduğunuzu.
*   Yerel branch'inizin uzak branch'e göre durumunu (ileride mi, geride mi, güncel mi).
*   `Changes to be committed`: Hazırlık alanındaki (staging) dosyalar.
*   `Changes not staged for commit`: Çalışma dizininde değiştirilmiş ama hazırlık alanına eklenmemiş dosyalar.
*   `Untracked files`: Git tarafından henüz hiç izlenmeyen yeni dosyalar.

### 5.4 Değişiklikleri Hazırlık Alanına Ekleme (Staging & `add`)

Çalışma dizinindeki değişiklikleri bir sonraki commit'e hazırlamak için `git add` kullanılır:

```bash
# Belirli bir dosyayı hazırlık alanına ekle
git add <dosya_adi.txt>

# Belirli bir klasördeki tüm değişiklikleri ekle
git add <klasor_adi>/

# Çalışma dizinindeki TÜM değişiklikleri (yeni, değiştirilmiş, silinmiş) ekle
git add .

# TÜM değişiklikleri eklemenin diğer yolu
git add -A # veya --all

# Sadece izlenen (tracked) dosyalardaki değişiklikleri ve silinmeleri ekle (yeni dosyaları eklemez)
git add -u # veya --update

# Değişiklikleri interaktif olarak parça parça seçerek ekle (çok kullanışlı!)
# Git size her değişiklik bloğunu gösterir ve [y/n/q/a/d/e/?] sorar.
git add -p # veya --patch
```

### 5.5 Commit Oluşturma (Değişiklikleri Kaydetme & `commit`)

Hazırlık alanındaki değişiklikleri (snapshot) projenin geçmişine kalıcı olarak kaydetmek için `git commit` kullanılır. Her commit, projenin o anki durumunun bir kaydıdır, bir SHA-1 kimliği (hash), yazar bilgisi, tarih ve bir mesaj içerir.

```bash
# Kısa ve açıklayıcı bir mesajla commit oluşturma (en yaygın kullanım)
git commit -m "feat: Kullanıcı profili sayfasını ekle"

# `-m` kullanmazsanız, Git'in ayarladığı metin editörü açılır.
# İlk satıra kısa başlık (max 50 karakter), bir boş satır, sonra detaylı açıklama yazılır.
git commit
```

### 5.6 İyi Commit Mesajları Yazma

Commit mesajları, projenin geçmişini anlamak, hata ayıklamak ve takım iletişimini sağlamak için hayati öneme sahiptir.

*   **Anlamlı Başlık:** İlk satır (konu satırı) kısa (genellikle <50 karakter) olmalı, **emir kipinde** yazılmalı ("Ekle", "Düzelt", "Güncelle" gibi) ve değişikliğin ne yaptığını açıkça özetlemelidir.
*   **Detaylı Açıklama (Gerekiyorsa):** Başlıktan sonra bir boş satır bırakılmalı. Ardından, değişikliğin *neden* yapıldığını, hangi sorunu çözdüğünü veya önemli bağlamları açıklayan daha uzun bir metin yazılabilir. Satırları okunabilirlik için ~72 karaktere sığdırmaya çalışın.
*   **Conventional Commits Standardı:** Takım içinde tutarlılık sağlamak ve otomatik sürüm notu oluşturma gibi araçları kullanmak için popüler bir standarttır. Mesajlar şu formatta yazılır: `tip(kapsam): açıklama`
    *   **Tipler:** `feat` (yeni özellik), `fix` (hata düzeltme), `docs` (dokümantasyon), `style` (formatlama), `refactor` (kod iyileştirme), `perf` (performans), `test` (test ekleme/düzeltme), `build` (yapı sistemi), `ci` (sürekli entegrasyon), `chore` (diğer bakım işleri).
    *   **Kapsam (Opsiyonel):** Değişikliğin etki ettiği alan (örn: `auth`, `ui`, `api`).
    *   **Açıklama:** Başlık kısmındaki gibi emir kipinde kısa açıklama.
    *   **Örnekler:**
        *   `feat(auth): Google ile giriş yapma özelliği eklendi`
        *   `fix: Kullanıcı silindiğinde ilişkili verilerin temizlenmemesi sorunu düzeltildi`
        *   `docs(readme): Kurulum adımları güncellendi`
        *   `refactor(api): Servis katmanındaki kod tekrarları azaltıldı`
        *   `chore: Bağımlılıklar son sürümlere güncellendi`
    *   **Breaking Change:** Eğer değişiklik geriye dönük uyumluluğu bozuyorsa, açıklamanın sonuna `BREAKING CHANGE:` ile başlayan bir not eklenir veya tipin sonuna `!` konur (örn: `feat!: ...`).

### 5.7 Değişiklikleri Görüntüleme (Farklar & `diff`)

Yapılan veya yapılacak olan değişiklikleri satır satır görmek için `git diff` kullanılır:

```bash
# Çalışma dizini ile hazırlık alanı (staging area) arasındaki farklar
# (Yani `git add` YAPMADAN önceki değişiklikler)
git diff

# Belirli bir dosyadaki çalışma dizini <> hazırlık alanı farkları
git diff -- <dosya_yolu>

# Hazırlık alanı ile son commit arasındaki farklar
# (Yani `git add` YAPTIKTAN sonra commit'e neyin gireceği)
git diff --staged
# veya
git diff --cached

# Belirli bir dosyadaki hazırlık alanı <> son commit farkları
git diff --staged -- <dosya_yolu>

# Çalışma dizini ile son commit arasındaki tüm farklar
# (Hem hazırlık alanına eklenen hem eklenmeyen tüm kaydedilmemiş değişiklikler)
git diff HEAD

# İki commit arasındaki farklar
git diff <commit_hash1> <commit_hash2>

# İki branch arasındaki farklar
git diff <branch1>..<branch2>

# Belirli bir dosyadaki branch'ler arası farklar
git diff <branch1>..<branch2> -- <dosya_yolu>
```

---

## 6. Zaman Makinesi: Geçmişi Yönetme ve Geri Alma

Git'in en güçlü yanlarından biri, proje geçmişini yönetme ve hataları geri alma yeteneğidir.

### 6.1 Commit Geçmişini Görüntüleme (`git log`)

Projenin commit geçmişini görmek için `git log` kullanılır. Birçok kullanışlı seçeneği vardır:

```bash
# Tüm commit geçmişi (varsayılan, uzun format)
git log

# Her commit'i tek satırda gösterir (kısa hash ve başlık) - Çok Kullanışlı!
git log --oneline

# Dallanma ve birleşme noktalarını ASCII grafikle gösterir
git log --graph

# `--oneline` ve `--graph` bir arada
git log --graph --oneline

# Her commit için değiştirilen dosyaları ve eklenen/çıkarılan satır sayısını gösterir
git log --stat

# Her commit için yapılan dosya içerik değişikliklerini (diff/patch) gösterir
git log -p
# veya
git log --patch

# Sadece son N commit'i göster
git log -n 5 # Son 5 commit

# Belirli bir yazarın commit'lerini göster (tırnak işareti isimde boşluk varsa önemlidir)
git log --author="Yazar Adı"

# Commit mesajında belirli bir metin içeren commit'leri ara
git log --grep="hata düzeltme"

# Belirli bir tarih aralığındaki commit'leri göster
git log --since="2 weeks ago"
git log --until="2023-10-26"
git log --since="2023-01-01" --until="2023-06-30"

# Belirli bir dosyayı veya klasörü etkileyen commit'leri göster
git log -- <dosya_veya_klasor_yolu>

# Daha okunabilir ve özelleştirilmiş format (örnek) - Alias olarak atanabilir!
# %Cred: kırmızı, %h: kısa hash, %Creset: renk reset, %C(yellow): sarı, %d: ref isimleri (branch, tag),
# %s: konu, %Cgreen: yeşil, %cr: göreceli tarih, %C(bold blue): kalın mavi, %an: yazar adı
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

### 6.2 Belirli Bir Commit'i İnceleme (`git show`)

Tek bir commit'in tüm detaylarını (yazar, tarih, tam mesaj ve yaptığı tüm değişiklikler) görmek için:

```bash
# Belirli bir commit hash'i ile
git show <commit_hash>
# Örnek:
git show a1b2c3d4e5f6

# Son commit'i göster
git show HEAD

# Sondan bir önceki commit'i göster
git show HEAD~1

# Sondan üçüncü commit'i göster
git show HEAD~3

# Sadece commit bilgisini (mesaj, yazar vb.) göster, diff gösterme
git show --no-patch <commit_hash>

# Sadece commit'in değiştirdiği dosyaların listesini göster
git show --name-only <commit_hash>
```

### 6.3 Geri Alma İşlemleri

Hatalar olur! Git, hataları düzeltmek veya değişiklikleri geri almak için çeşitli mekanizmalar sunar:

#### 6.3.1 Son Commit'i Düzenleme (`--amend`)

Son commit'e dosya eklemeyi unuttuysanız, bir hatayı düzelttiyseniz veya sadece commit mesajını değiştirmek istiyorsanız, yeni bir commit oluşturmak yerine son commit'i düzenleyebilirsiniz.

**ÖNEMLİ UYARI:** Bu işlem son commit'in hash'ini değiştirir, yani geçmişi yeniden yazar. **Sadece henüz uzak depoya göndermediğiniz (push etmediğiniz) commit'ler için kullanın.** Başkalarıyla paylaşılan bir branch'teki commit'i `amend` ederseniz, ciddi sorunlara yol açabilirsiniz (onların geçmişiyle sizinki uyumsuz hale gelir).

```bash
# 1. Unutulan dosyayı/değişikliği hazırlık alanına ekleyin
git add unutulan_dosya.txt
git add duzeltilmis_dosya.py

# 2. Commit'i amend ile yeniden oluşturun
# Mevcut mesajı kullanarak (sadece eklenen dosyaları dahil eder):
git commit --amend --no-edit

# Yeni bir mesaj yazarak (editör açılır):
git commit --amend

# Yeni bir mesajı doğrudan komut satırında belirterek:
git commit --amend -m "feat: Kullanıcı girişi tamamlandı (doğrulama eklendi)"
```

#### 6.3.2 Hazırlık Alanından Dosya Çıkarma (`reset HEAD`/`restore --staged`)

`git add` ile yanlışlıkla hazırlık alanına (staging area) eklediğiniz bir değişikliği veya dosyayı commit'lemeden önce geri almak için:

```bash
# Yeni ve önerilen yöntem:
git restore --staged <dosya_adi>

# Tüm hazırlık alanını temizle (tüm eklenenleri geri al)
git restore --staged .

# Eski yöntem (hala çalışır):
# git reset HEAD <dosya_adi>
# git reset HEAD .
```

Bu komutlar çalışma dizininizdeki (working directory) değişikliklere dokunmaz, sadece hazırlık alanını (staging area) temizler veya belirtilen dosyayı çıkarır.

#### 6.3.3 Çalışma Dizinindeki Değişiklikleri Geri Alma (`checkout --`/`restore`)

Çalışma dizininde (working directory) yaptığınız ama henüz commit'lemediğiniz (hatta belki `add` bile yapmadığınız) değişiklikleri iptal etmek ve dosyanın son commit'teki haline dönmesini sağlamak için:

**UYARI:** Bu işlem, çalışma dizinindeki o dosyaya ait kaydedilmemiş tüm değişiklikleri kalıcı olarak siler. Geri alınamaz. Çok dikkatli olun!

```bash
# Yeni ve önerilen yöntem:
git restore <dosya_adi>

# Çalışma dizinindeki TÜM değişiklikleri geri al (çok tehlikeli!)
# git restore .

# Eski yöntem (daha kafa karıştırıcı olabilir):
# git checkout -- <dosya_adi>
# git checkout -- . # Çok tehlikeli!
```

#### 6.3.4 Bir Commit'in Değişikliklerini Geri Alan Yeni Commit Oluşturma (`revert`)

Geçmişteki belirli bir commit'in yaptığı değişiklikleri tersine çeviren **yeni bir commit** oluşturur. Proje geçmişini değiştirmez (yani eski commit'i silmez), sadece o commit'in etkilerini ortadan kaldıran zıt bir değişiklik ekler.

Bu yöntem, **uzak depoya gönderilmiş (push edilmiş)** veya başkalarıyla paylaşılan branch'lerdeki hataları düzeltmek için **en güvenli yoldur**, çünkü mevcut geçmişi bozmaz.

```bash
# Geri alınacak commit'in hash'ini bulun (git log ile)
git log --oneline

# Belirtilen commit'in değişikliklerini geri alan yeni bir commit oluştur
git revert <geri_alinacak_commit_hash>
```

Bu komut, genellikle bir commit mesajı girmeniz için metin editörünü açar (varsayılan mesaj genellikle "Revert '[orijinal commit başlığı]'" şeklindedir). Mesajı onaylayıp kaydettiğinizde yeni revert commit'i oluşturulur.

Eğer `revert` işlemi çakışmaya (conflict) neden olursa, çakışmayı çözüp `git add <dosya>` ve ardından `git revert --continue` yapmanız gerekir. İptal etmek için `git revert --abort`.

#### 6.3.5 Geçmişteki Bir Duruma Dönme (`reset`)

`git reset`, branch'inizin işaret ettiği commit'i (HEAD) ve isteğe bağlı olarak hazırlık alanını ve çalışma dizinini belirli bir geçmiş commit'e "sıfırlamanızı" sağlar. Bu, **geçmişi yeniden yazan** güçlü ve potansiyel olarak tehlikeli bir komuttur.

**ÖNEMLİ UYARI:** `git reset`'i (özellikle `--hard` ile) **sadece yerel, paylaşılmamış commit'ler üzerinde kullanın.** Uzak depoya gönderilmiş commit'leri `reset`'lemek, takım arkadaşlarınızın depolarıyla ciddi uyumsuzluklara yol açar.

`git reset`'in üç ana modu vardır:

*   `--soft`: Sadece HEAD işaretçisini belirtilen commit'e taşır. Hazırlık alanı (staging area) ve çalışma dizini (working directory) dokunulmaz. Yani, `reset`'lenen commit'lerden sonraki tüm değişiklikler hala hazırlık alanında (staged) durur, sanki `git add` yapmışsınız gibi. Son birkaç commit'i birleştirmek (squash) için kullanılabilir (ama `rebase -i` genellikle daha pratiktir).

    ```bash
    # Son commit'i geri al, değişiklikler hazırlık alanında kalsın
    git reset --soft HEAD~1
    ```

*   `--mixed` (**Varsayılan mod**): HEAD işaretçisini ve hazırlık alanını (staging area) belirtilen commit'e sıfırlar. Çalışma dizinine (working directory) dokunmaz. Yani, `reset`'lenen commit'lerden sonraki tüm değişiklikler çalışma dizininde "unstaged" olarak kalır. Yanlışlıkla yapılan commit'leri geri alıp değişiklikleri yeniden düzenlemek için kullanışlıdır.

    ```bash
    # Son commit'i geri al, değişiklikler çalışma dizininde unstaged olarak kalsın
    git reset --mixed HEAD~1
    # veya sadece:
    git reset HEAD~1
    ```

*   `--hard`: HEAD işaretçisini, hazırlık alanını **VE** çalışma dizinini belirtilen commit'in durumuna sıfırlar. Yani, `reset`'lenen commit'lerden sonra yapılan tüm değişiklikler (hem staged hem unstaged) **kalıcı olarak silinir**. Çok dikkatli kullanılmalıdır! Yanlışlıkla yapılan ve tamamen kurtulmak istediğiniz commit'ler için kullanılır.

    ```bash
    # Son commit'i ve onun getirdiği tüm değişiklikleri (staged/unstaged) kalıcı olarak sil
    git reset --hard HEAD~1

    # Belirli bir commit hash'ine DİKKATLİCE dön (o commit'ten sonraki her şeyi siler)
    git reset --hard <commit_hash>
    ```

**`reset` sonrası kayıp commit'leri kurtarma:** Eğer yanlışlıkla `reset --hard` yaparsanız, `git reflog` komutu (Bölüm 10.5) genellikle silinen commit'lere geri dönmenizi sağlayabilir.

---

## 7. Paralel Evrenler: Dallanma ve Birleştirme

Dallanma (Branching), Git'in en önemli özelliklerinden biridir. Ana kod tabanını (genellikle `main` veya `master`) bozmadan yeni özellikler geliştirmek, hataları düzeltmek veya farklı fikirleri denemek için paralel çalışma alanları oluşturmanızı sağlar.

### 7.1 Branch (Dal) Nedir?

Bir branch, aslında belirli bir commit'e işaret eden **hareketli bir etikettir**. Varsayılan olarak, ilk commit yapıldığında `main` (veya eski sistemlerde `master`) adında bir branch oluşur. Yeni bir branch oluşturduğunuzda, aslında sadece mevcut commit'e işaret eden yeni bir etiket yaratmış olursunuz. Siz o branch'te yeni commit'ler yaptıkça, sadece o branch etiketi ileri doğru hareket eder, diğer branch'ler yerinde kalır. Bu sayede farklı geliştirme hatları birbirinden bağımsız ilerleyebilir.

### 7.2 Branch Oluşturma, Geçiş Yapma ve Listeleme (`branch`, `checkout`)

**Yeni Branch Oluşturma:**

```bash
# Mevcut bulunduğunuz commit'ten yeni bir branch oluşturur, ama o branch'e geçmez
git branch <yeni_branch_adi>
# Örnek:
git branch feature/kullanici-kayit
```

**Branch'ler Arası Geçiş Yapma (`checkout`):**
Farklı bir branch'e geçmek (çalışma dizininizi o branch'in son commit'indeki hale getirmek) için `checkout` kullanılır:

```bash
git checkout <gecis_yapilacak_branch_adi>
# Örnek:
git checkout feature/kullanici-kayit
```

*Not:* Geçiş yapmadan önce mevcut branch'teki değişikliklerinizi commit'lemeniz veya stash'lemeniz (Bölüm 10.1) genellikle iyi bir fikirdir, aksi takdirde Git çakışma uyarısı verebilir veya değişiklikler kaybolabilir.

**Branch Oluşturma ve Aynı Anda Geçiş Yapma (Yaygın Kullanım):**
Bu iki adımı tek komutta birleştirmek için `-b` seçeneği kullanılır:

```bash
git checkout -b <yeni_branch_adi>
# Örnek:
git checkout -b hotfix/login-bug
```

Bu komut, `git branch hotfix/login-bug` ve ardından `git checkout hotfix/login-bug` yapmanın kısayoludur.

**Branch'leri Listeleme:**

```bash
# Sadece yerel (local) branch'leri listeler. Aktif olan branch '*' ile işaretlenir.
git branch

# Yerel branch'leri son commit bilgisiyle birlikte listeler
git branch -v

# Hem yerel hem de uzak izleme (remote-tracking) branch'lerini listeler
git branch -a

# Belirli bir desene uyan branch'leri listele (örn: 'feature/' ile başlayanlar)
git branch --list 'feature/*'
```

**Branch Yeniden Adlandırma:**

```bash
# Mevcut (aktif) branch'i yeniden adlandır
git branch -m <yeni_ad>

# Başka bir branch'i yeniden adlandır (aktif olmayan)
git branch -m <eski_ad> <yeni_ad>
```

**Branch Silme:**
**UYARI:** Silinecek branch'teki commit'ler başka hiçbir branch tarafından referans alınmıyorsa ve henüz birleştirilmediyse, bu commit'lere erişimi kaybedebilirsiniz (`reflog` ile kurtarma şansı olsa da).

```bash
# Birleştirilmiş (merged) bir branch'i sil (güvenli)
git branch -d <silinecek_branch_adi>
# Örnek:
git branch -d feature/kullanici-kayit

# Birleştirilmemiş bir branch'i silmeye zorla (DİKKATLİ OLUN!)
# Commit kaybına neden olabilir.
git branch -D <silinecek_branch_adi>
```

### 7.3 Branch Birleştirme (`merge`)

Farklı bir branch'te tamamladığınız işleri (commit'leri) ana branch'inize (veya başka bir branch'e) entegre etmek için `git merge` kullanılır.

**Tipik Akış:**

1.  Hedef branch'e geçin (genellikle `main` veya `develop`).
2.  Hedef branch'in güncel olduğundan emin olun (`git pull` veya `fetch`+`merge`).
3.  Birleştirmek istediğiniz branch'i `merge` komutu ile çağırın.

```bash
# 1. Ana branch'e geç
git checkout main

# 2. Ana branch'i güncelle (uzak depodan son değişiklikleri al)
# Eğer uzak depo ile çalışıyorsanız bu adımı yapın
git pull origin main

# 3. Özellik branch'ini main'e birleştir
git merge feature/kullanici-kayit
```

**Merge Türleri:**

*   **Fast-Forward Merge:** Eğer hedef branch (`main`), birleştirilecek branch (`feature`) oluşturulduktan sonra hiç yeni commit almamışsa, Git sadece hedef branch'in etiketini birleştirilecek branch'in son commit'ine taşır. Geçmiş lineer (düz) kalır, yeni bir "merge commit" oluşmaz. Bu, en basit birleştirme türüdür.
*   **Three-Way Merge (Recursive Merge):** Eğer her iki branch de (hedef ve kaynak) kendi yollarında ilerlemişse (yani ortak atadan sonra ikisinde de yeni commit'ler varsa), Git iki branch'in son commit'lerini ve onların en yakın ortak atasını (common ancestor) kullanarak birleştirme yapar. Bu işlem sonucunda, iki farklı geçmişi birleştirdiğini gösteren yeni bir **"merge commit"** oluşur. Bu commit'in iki ebeveyni (parent) olur.

### 7.4 Merge Çakışmalarını (Conflict) Çözme

Eğer iki branch'te de **aynı dosyanın aynı satırları** farklı şekillerde değiştirilmişse, Git bu değişikliği otomatik olarak birleştiremez ve bir **"merge conflict"** (birleştirme çakışması) oluşur.

**Çakışmayı Fark Etme:** `git merge` komutu başarısız olur ve hangi dosyalarda çakışma olduğunu listeler. `git status` komutu da çakışan dosyaları "Unmerged paths" altında gösterir.

**Çakışan Dosyaları Açma:** Çakışan dosyaları bir metin editöründe açtığınızda, Git'in çakışan bölümleri aşağıdaki gibi işaretlediğini görürsünüz:

```diff
<<<<<<< HEAD
// Hedef branch'teki (örn: main) kodlarınız
System.out.println("Merhaba Dünya!");
=======
// Birleştirilen branch'teki (örn: feature) kodlar
System.out.println("Hello World!");
>>>>>>> feature/kullanici-kayit
```

**Çakışmayı Çözme Adımları:**

1.  Çakışan dosyayı açın.
2.  `<<<<<<< HEAD`, `=======`, `>>>>>>> branch_adi` işaretlerini bulun.
3.  Bu işaretler arasındaki kodları inceleyin.
4.  Dosyanın **son halinin nasıl olması gerektiğine karar verin.** İki taraftaki kodları birleştirebilir, birini seçebilir veya tamamen yeni bir kod yazabilirsiniz.
5.  Kararınızı verdikten sonra, **işaretçileri ve istemediğiniz kodları silin.** Dosyayı olması gereken doğru haline getirin.
6.  Dosyayı kaydedin.

**Çözülen Dosyayı Hazırlık Alanına Ekleme:**
Çakışmayı çözdükten sonra, dosyayı normal bir değişiklik gibi hazırlık alanına ekleyin:

```bash
git add <cakisma_cozulen_dosya.java>
```

**Merge İşlemini Tamamlama:**
Tüm çakışmaları çözüp ilgili dosyaları `add` ile ekledikten sonra, merge işlemini tamamlamak için bir commit oluşturun:

```bash
git commit
```

Git genellikle sizin için varsayılan bir merge commit mesajı hazırlar ("Merge branch '...' into ..."). Bu mesajı kullanabilir veya düzenleyebilirsiniz.

**Merge İşlemini İptal Etme:** Eğer çakışma çözümüyle başa çıkamayacağınıza karar verirseniz veya yanlış bir şey yaptıysanız, merge işlemini başlatmadan önceki duruma dönebilirsiniz:

```bash
git merge --abort
```

### 7.5 Geçmişi Yeniden Yazma (`rebase`)

`git rebase`, bir branch'teki commit'leri alıp başka bir branch'in **üzerine** yeniden uygulamak için kullanılan güçlü bir araçtır. Merge gibi iki branch'i birleştirmenin alternatif bir yoludur, ancak **geçmişi yeniden yazar**.

**Temel Kullanım (Feature Branch'i Güncelleme):**

Diyelim ki `main` branch'inden `feature/yeni-ozellik` adında bir branch oluşturdunuz. Siz `feature` üzerinde çalışırken, `main` branch'ine başka commit'ler eklendi. `feature` branch'inizi `main`'deki son değişikliklerle güncellemek ve geçmişinizi daha lineer (düz) tutmak için `rebase` kullanabilirsiniz:

```bash
# 1. Feature branch'inde olduğunuzdan emin olun
git checkout feature/yeni-ozellik

# 2. Main branch'indeki son değişiklikleri çekin (uzak depo varsa)
# Bu adım, yerel 'main' branch'inizi güncel tutmak içindir,
# rebase doğrudan 'origin/main' üzerine de yapılabilir.
git fetch origin
# Opsiyonel: Yerel main'i güncellemek isterseniz:
# git checkout main
# git pull origin main
# git checkout feature/yeni-ozellik

# 3. Feature branch'ini main'in üzerine rebase et
git rebase main
# veya doğrudan uzak branch üzerine:
# git rebase origin/main
```

**`rebase` Nasıl Çalışır?**

1.  `feature/yeni-ozellik` branch'i ile `main` branch'inin **ortak atasından** sonraki `feature` branch'indeki commit'leri bulur.
2.  `feature` branch'ini geçici olarak `main`'in son commit'ine taşır.
3.  Bulunan commit'leri **tek tek** `main`'in son commit'i üzerine sırayla uygulamaya çalışır.
4.  Sonuç olarak, `feature` branch'iniz sanki `main`'in en son halinden yeni oluşturulmuş gibi görünür ve commit geçmişi daha temiz, lineer bir hal alır. **Merge commit'i oluşmaz.**

**Rebase Çakışmalarını Çözme:**

`rebase` sırasında da çakışmalar olabilir (her commit tek tek uygulandığı için birden fazla çakışma çözmeniz gerekebilir).

1.  `rebase` durur ve çakışan dosyayı belirtir.
2.  Çakışmayı normal merge çakışması gibi çözün (işaretleri temizleyin, doğru kodu bırakın).
3.  Çözdüğünüz dosyayı hazırlık alanına ekleyin: `git add <cakisan_dosya>`
4.  Rebase işlemine devam etmesini söyleyin: `git rebase --continue`
5.  Eğer başka commit'lerde de çakışma varsa, 2-4 adımlarını tekrarlayın.

**Rebase İşlemini İptal Etme:**

```bash
git rebase --abort
```

**Rebase Uyarısı (The Golden Rule of Rebasing):**
`rebase`, commit'lerin hash'lerini değiştirdiği için **geçmişi yeniden yazar**. Bu nedenle, `merge`'ün aksine, **asla başkalarıyla paylaştığınız (uzak depoya push ettiğiniz) bir branch'i rebase etmeyin!** Eğer bunu yaparsanız ve `--force` ile push ederseniz (bkz. Bölüm 13.3), takım arkadaşlarınızın geçmişiyle sizinki uyumsuz hale gelir ve büyük sorunlar çıkar. Kendi yerel, henüz paylaşmadığınız `feature` branch'lerinizi temiz tutmak için `rebase` harikadır.

### 7.6 Merge vs. Rebase: Ne Zaman Hangisini Kullanmalı?

Bu, Git dünyasındaki yaygın tartışma konularından biridir ve kesin bir doğru cevabı yoktur, takım veya proje tercihlerine bağlıdır.

**Merge:**

*   **Avantajları:**
    *   Geçmişi olduğu gibi korur, **tahribatsızdır**.
    *   Hangi branch'in ne zaman birleştirildiği "merge commit"i sayesinde açıkça bellidir, **izlenebilirlik yüksektir**.
    *   Daha basittir ve geçmişi değiştirmediği için **paylaşılan branch'lerde daha güvenlidir**.
*   **Dezavantajları:**
    *   Özellikle çok sayıda branch ve sık birleştirme olan projelerde commit geçmişi çok dallı, budaklı ve takip etmesi zor hale gelebilir (`git log --graph` çıktısı karmaşıklaşır).
*   **Kullanım Senaryosu:**
    *   Paylaşılan branch'leri (örn: `develop`'u `main`'e, `release` branch'lerini `main`'e) birleştirirken.
    *   Bir özelliğin tam olarak ne zaman ve hangi noktada ana hatta dahil edildiğini kaydetmek istediğinizde.
    *   Takımınız `rebase` konusunda rahat değilse veya basitliği tercih ediyorsa.

**Rebase:**

*   **Avantajları:**
    *   Daha **temiz, lineer bir proje geçmişi** oluşturur. Sanki tüm işler sıralı bir şekilde yapılmış gibi görünür.
    *   Merge commit kalabalığını önler.
    *   Commit'leri birleştirme/düzenleme (`rebase -i`) için güçlü araçlar sunar (Bölüm 10.4).
*   **Dezavantajları:**
    *   **Geçmişi yeniden yazar** (commit hash'leri değişir).
    *   **Paylaşılan branch'lerde kullanılırsa çok tehlikeli olabilir ("Golden Rule").**
    *   Çakışma çözümü, `merge`'e göre daha sık ve commit başına yapıldığı için bazen daha zahmetli olabilir.
    *   Birleştirme noktası bilgisi (merge commit'i) kaybolur.
*   **Kullanım Senaryosu:**
    *   **Kendi yerel feature branch'inizi** ana branch (`main` veya `develop`) ile senkronize etmek ve Pull Request'e hazırlamak için.
    *   Pull Request'i birleştirmeden önce commit'leri düzenlemek/birleştirmek (`rebase -i`) için.

**Genel Tavsiye:**

*   **Yerel, kişisel branch'lerinizde:** `rebase` kullanarak ana daldaki (örn: `origin/main`) güncellemeleri alın ve geçmişinizi temiz tutun.
*   **Feature branch'inizi paylaşılan bir ana branch'e (`main`, `develop`) entegre ederken:** Genellikle `merge` (veya platformların sunduğu "Squash and Merge" gibi seçenekler) kullanın.
*   **En önemlisi:** Takımınızın belirlediği iş akışına ve kurallara uyun!

---

## 8. Takım Çalışması: Uzak Depolarla Etkileşim

Git'in dağıtık yapısı, takım çalışmasını ve kod paylaşımını kolaylaştırır. Bu, "remote" (uzak depo) kavramı üzerinden yapılır.

### 8.1 Yerel (Local) vs. Uzak (Remote) Depo

*   **Yerel Depo (Local Repository):** Sizin bilgisayarınızda bulunan `.git` klasörünü içeren tam depo kopyasıdır. Çalışma dizininiz, hazırlık alanınız ve tüm proje geçmişi buradadır. Yaptığınız `commit`, `branch`, `reset` gibi işlemler öncelikle burada gerçekleşir.
*   **Uzak Depo (Remote Repository):** Genellikle internet üzerinde (GitHub, GitLab, Bitbucket vb.) veya şirket ağı içindeki paylaşılan bir sunucuda barındırılan depo kopyasıdır. Takım üyelerinin kodlarını paylaştığı, senkronize ettiği ve işbirliği yaptığı merkezi bir nokta işlevi görür. Uzak depoda sizin çalışma dizininiz veya hazırlık alanınız bulunmaz; sadece commit geçmişi, branch'ler ve tag'ler bulunur.

### 8.2 Uzak Depo Yönetimi (`remote`)

Yerel deponuzun hangi uzak depolarla bağlantılı olduğunu yönetmek için `git remote` komutu kullanılır.

```bash
# Bağlı olunan uzak depoların kısa adlarını listele (genellikle 'origin')
git remote

# Uzak depoların adlarını ve URL'lerini listele
git remote -v

# Yeni bir uzak depo bağlantısı ekle
git remote add <kisa_ad> <url>
# Örnek: Orijinal projeyi 'upstream' olarak eklemek (forking workflow'da yaygın)
git remote add upstream https://github.com/orijinal-kullanici/orijinal-depo.git

# Belirli bir uzak depo hakkında detaylı bilgi göster (hangi branch'ler takip ediliyor vb.)
git remote show <uzak_depo_adi>
# Örnek:
git remote show origin

# Bir uzak deponun URL'sini değiştirme
git remote set-url <uzak_depo_adi> <yeni_url>

# Bir uzak depoyu yeniden adlandırma
git remote rename <eski_ad> <yeni_ad>

# Bir uzak depo bağlantısını kaldırma
git remote remove <uzak_depo_adi>
# veya
git remote rm <uzak_depo_adi>
```

`git clone` ile bir depo kopyaladığınızda, Git otomatik olarak orijinal URL'yi `origin` adıyla `remote` olarak ekler.

### 8.3 Uzak Depodaki Değişiklikleri Çekmeden Görme

Takım arkadaşlarınızın uzak depoya gönderdiği değişiklikleri kendi yerel çalışma kopyanıza **entegre etmeden** önce nelerin değiştiğini görmek isteyebilirsiniz. Bu, olası çakışmaları öngörmek veya projenin genel ilerleyişini takip etmek için çok faydalıdır.

**Adımlar:**

1.  **Uzak Depodaki Bilgiyi Güncelle (`fetch`):**
    Bu komut, belirtilen uzak depodan (genellikle `origin`) tüm branch ve tag bilgilerini indirir ve yerel deponuzdaki **"uzak izleme dallarını"** (remote-tracking branches, örn: `origin/main`) günceller. **Sizin aktif yerel branch'lerinize (`main`, `feature/x` gibi) dokunmaz.**

    ```bash
    git fetch <uzak_depo_adi>
    # Genellikle:
    git fetch origin
    ```

2.  **Farkları Görüntüle (`log` veya `diff`):**
    `fetch` işleminden sonra, yerel branch'iniz ile güncellenmiş uzak izleme branch'i arasındaki farkları görebilirsiniz:

    ```bash
    # Yerel 'main' branch'i ile 'origin/main' arasındaki commit farklarını listele
    # (origin/main'de olup main'de olmayan commitleri gösterir)
    git log main..origin/main --oneline

    # Yerel 'feature/x' branch'i ile 'origin/feature/x' arasındaki commit farkları
    git log feature/x..origin/feature/x --oneline

    # İki branch arasındaki dosya içerik farklarını göster
    git diff main origin/main

    # Belirli bir dosyada farkları göster
    git diff main origin/main -- <dosya_yolu>
    ```

    `git status` komutu da `fetch` sonrası yerel branch'inizin uzak izleme branch'ine göre kaç commit geride (`behind`) veya ileride (`ahead`) olduğunu gösterir.

### 8.4 Değişiklikleri Uzak Depodan Alma (`fetch`, `pull`)

Uzak depodaki yeni commit'leri yerel deponuza almak için iki ana komut vardır:

*   **`git fetch`:** (Yukarıda açıklandı) Sadece uzak depodaki verileri indirir ve uzak izleme dallarını (`origin/main` gibi) günceller. **Yerel branch'lerinizi değiştirmez.** Bu, değişiklikleri önce inceleyip sonra manuel olarak birleştirmek (merge veya rebase) istediğinizde kullanışlıdır.

    ```bash
    # 1. Uzak değişiklikleri fetch et
    git fetch origin

    # 2. Değişiklikleri incele (isteğe bağlı)
    git log main..origin/main --oneline

    # 3. Güncellenmiş uzak izleme branch'ini yerel branch'inize merge et
    git checkout main
    git merge origin/main
    ```

*   **`git pull`:** Aslında iki komutun birleşimidir: `git fetch` + `git merge`. Belirtilen uzak depodan ve branch'ten verileri çeker (`fetch`) ve ardından bu değişiklikleri **otomatik olarak mevcut yerel branch'inize birleştirir (`merge`)**. En yaygın kullanılan yöntemdir, ancak arka planda ne olduğunu anlamak önemlidir.

    ```bash
    # Aktif olan yerel branch'in takip ettiği uzak branch'ten (upstream)
    # değişiklikleri çek ve birleştir
    git pull

    # Belirli bir uzak depo ve branch'ten çek ve birleştir
    # (örn: origin'deki main branch'ini mevcut branch'e çek)
    git pull origin main
    ```

    **`pull` ile `rebase`:** `pull` işleminin `merge` yerine `rebase` yapmasını sağlayabilirsiniz. Bu, yerel commit'lerinizi çekilen uzak commit'lerin *üzerine* yerleştirir ve daha lineer bir geçmiş sağlar. **Dikkatli kullanılmalıdır**, özellikle paylaşılmış branch'lerde sorun yaratabilir.

    ```bash
    # Pull işlemini rebase ile yap (bir kerelik)
    git pull --rebase origin main

    # Varsayılan pull davranışını rebase olarak ayarla (global veya depo bazında)
    # git config --global pull.rebase true
    ```

### 8.5 Değişiklikleri Uzak Depoya Gönderme (`push`)

Yerel deponuzda yaptığınız commit'leri takım arkadaşlarınızla paylaşmak için uzak depoya göndermeniz gerekir. Bu işlem `git push` ile yapılır.

```bash
# Yerel 'main' branch'ini 'origin' uzak deposundaki 'main' branch'ine gönder
git push origin main

# Yerel 'feature/login' branch'ini 'origin' uzak deposuna aynı isimle gönder
git push origin feature/login
```

*   **İlk Push ve Upstream Ayarı (`-u`):** Bir yerel branch'i ilk kez uzak depoya gönderirken `-u` (veya `--set-upstream`) seçeneğini kullanmak yaygındır. Bu, yerel branch'inizin `origin`'deki hangi branch'i takip edeceğini ayarlar. Bu sayede sonraki `pull` ve `push` işlemlerinde branch isimlerini belirtmenize gerek kalmaz.

    ```bash
    # feature/yeni-ozellik branch'ini origin'e gönder ve upstream olarak ayarla
    git push -u origin feature/yeni-ozellik

    # Bu işlemden sonra, feature/yeni-ozellik branch'indeyken:
    git push # Otomatik olarak 'origin feature/yeni-ozellik' anlamına gelir
    git pull # Otomatik olarak 'origin feature/yeni-ozellik'ten çeker
    ```

*   **Force Push (`--force`, `--force-with-lease`):** Eğer yerel geçmişiniz uzak depodaki geçmişle uyumsuzsa (örn: yerel olarak `rebase` veya `reset` yaptıysanız), normal `push` işlemi reddedilir. Geçmişi zorla üzerine yazmak için `--force` kullanılabilir. **ANCAK BU ÇOK TEHLİKELİDİR!** Başkalarının commit'lerini silebilir.
    *   **Daha Güvenli Alternatif: `--force-with-lease`**: Bu seçenek, sadece uzak branch'teki son commit sizin beklediğiniz (fetch ettiğiniz zamanki) commit ise zorla push yapar. Eğer siz fetch ettikten sonra başka biri o branch'e push yapmışsa, `--force-with-lease` işlemi reddeder ve veri kaybını önler. **Genellikle `--force` yerine `--force-with-lease` tercih edilmelidir.** (Bkz. Bölüm 13.3)

    ```bash
    # DİKKAT! Tehlikeli! Sadece ne yaptığınızdan %100 eminseniz kullanın.
    # git push --force origin main

    # Daha güvenli zorla push
    git push --force-with-lease origin main
    ```

### 8.6 Uzak İzleme Dalları (Remote-Tracking Branches)

Yerel deponuz, uzak depodaki branch'lerin durumunu takip etmek için özel referanslar tutar. Bunlara "uzak izleme dalları" (remote-tracking branches) denir. Örneğin, `origin/main`, `origin/develop`, `upstream/main` gibi.

*   Bunlar, uzak depodaki ilgili branch'lerin **sizin son `fetch`, `pull` veya `push` yaptığınız andaki durumunu** gösterir.
*   Doğrudan bu branch'ler üzerinde çalışamazsınız (checkout ettiğinizde "detached HEAD" durumuna geçersiniz - Bkz. Bölüm 13.1).
*   Amacı, yerel çalışmalarınızı uzak depodaki durumla karşılaştırmak (`diff`, `log`) ve `merge`, `rebase` gibi işlemler için referans noktası olmaktır.
*   `git fetch` komutu bu dalları günceller.
*   `git branch -r` komutu sadece uzak izleme dallarını listeler.
*   `git branch -a` komutu hem yerel hem de uzak izleme dallarını listeler.

### 8.7 Uzak Branch'leri Yönetme

*   **Uzak Branch'i Silme:** Yerel olarak bir branch'i sildiğinizde, bu işlem otomatik olarak uzak depoya yansımaz. Uzak depodaki bir branch'i silmek için `push` komutunu özel bir syntax ile kullanırsınız:

    ```bash
    # origin uzak deposundaki 'old-feature' branch'ini sil
    git push origin --delete old-feature
    # veya eski syntax:
    # git push origin :old-feature
    ```

*   **Uzak Depoda Silinmiş Branch'leri Yerelden Temizleme (`prune`):** Takım arkadaşlarınız uzak depodan bazı branch'leri sildiyse, sizin yerel deponuzdaki `origin/silinmis-feature` gibi uzak izleme referansları hala kalabilir. Bunları temizlemek için `fetch` veya `remote` komutlarını `--prune` seçeneği ile kullanabilirsiniz.

    ```bash
    # Uzak depoda artık var olmayan uzak izleme dallarını yerelden temizle
    git fetch --prune origin
    # veya
    git remote prune origin
    ```

---

## 9. Pull Request / Merge Request Süreci

Çoğu modern Git barındırma platformu (GitHub, GitLab, Bitbucket), kod değişikliklerini ana branch'e entegre etmeden önce tartışmak, incelemek ve onaylamak için bir mekanizma sunar. Bu mekanizmaya genellikle **Pull Request (PR)** (GitHub, Bitbucket) veya **Merge Request (MR)** (GitLab) denir. İşlevleri temelde aynıdır.

### 9.1 PR/MR Nedir?

Bir Pull Request (veya Merge Request), bir geliştiricinin yaptığı değişiklikleri (genellikle bir feature branch'indeki commit'leri) başka bir branch'e (genellikle `main` veya `develop`) birleştirmeyi **teklif etmesi** işlemidir.

PR/MR süreci şunları sağlar:

*   **Kod İnceleme (Code Review):** Diğer takım üyeleri önerilen değişiklikleri satır satır inceleyebilir, yorum yapabilir, soru sorabilir ve iyileştirme talep edebilir.
*   **Tartışma:** Değişikliklerin amacı, yaklaşımı ve olası etkileri hakkında bir tartışma ortamı sunar.
*   **Otomatik Kontroller:** Sürekli Entegrasyon (CI) araçları (örn: GitHub Actions, Jenkins, GitLab CI) PR/MR üzerinde otomatik testler çalıştırabilir, kod stilini kontrol edebilir ve build alıp alamadığını doğrulayabilir.
*   **Kontrollü Entegrasyon:** Değişikliklerin ana kod tabanına sadece onaylandıktan ve kontroller geçtikten sonra birleştirilmesini sağlar, bu da kod kalitesini ve kararlılığını artırır.

### 9.2 PR/MR Oluşturma Adımları

Genel akış şu şekildedir (Platforma göre küçük farklılıklar olabilir):

1.  **Feature Branch Oluşturma:** Ana branch'ten (`main` veya `develop`) yeni bir branch oluşturun ve değişikliklerinizi bu branch üzerinde yapın.
    ```bash
    git checkout main
    git pull origin main
    git checkout -b feature/harika-yeni-ozellik
    # Kod yaz, değişiklik yap...
    git add .
    git commit -m "feat: Harika yeni özelliği ekle"
    # Gerekirse daha fazla commit...
    ```
2.  **Branch'i Uzak Depoya Push Etme:** Yerel branch'inizi uzak depoya (`origin`) gönderin.
    ```bash
    git push -u origin feature/harika-yeni-ozellik
    ```
3.  **PR/MR Oluşturma (Platform Arayüzü):**
    *   GitHub/GitLab/Bitbucket arayüzüne gidin.
    *   Genellikle `push` işleminden sonra size otomatik olarak bir PR/MR oluşturma butonu veya bildirimi gösterilir.
    *   Eğer gösterilmezse, projenin "Pull Requests" veya "Merge Requests" sekmesine gidin ve "New Pull Request" / "New Merge Request" butonuna tıklayın.
    *   **Kaynak Branch (Source/Compare):** Değişiklikleri yaptığınız branch (`feature/harika-yeni-ozellik`).
    *   **Hedef Branch (Target/Base):** Değişikliklerin birleştirilmesini istediğiniz branch (genellikle `main` veya `develop`).
    *   Platform, iki branch arasındaki commit'leri ve dosya farklarını gösterecektir.
    *   **Başlık ve Açıklama:** PR/MR için açıklayıcı bir başlık ve yapılan değişiklikleri, neden yapıldığını, nasıl test edilebileceğini anlatan detaylı bir açıklama yazın. İlgili issue'ları veya task'ları linkleyebilirsiniz (`Fixes #123` gibi).
    *   **Reviewer (İnceleyici) Ekleme:** Değişiklikleri incelemesini istediğiniz takım arkadaşlarınızı seçin.
    *   **Label/Tag Ekleme (Opsiyonel):** PR/MR'ı kategorize etmek için etiketler ekleyebilirsiniz (`bug`, `feature`, `ui`, `backend` gibi).
    *   **PR/MR'ı Oluştur:** Bilgileri doldurduktan sonra PR/MR'ı oluşturun.

4.  **İnceleme ve Tartışma:** Reviewer'lar kodu inceleyecek, yorumlar yapacak ve gerekirse değişiklik isteyecektir. Bildirimleri takip edin ve gelen geri bildirimlere göre kodunuzu güncelleyin. Güncellemeleri aynı feature branch'ine commit'leyip tekrar push edin; PR/MR otomatik olarak güncellenecektir.
    ```bash
    # Geri bildirime göre düzeltme yap
    git add .
    git commit -m "fix: İnceleme yorumlarına göre düzeltmeler yapıldı"
    git push origin feature/harika-yeni-ozellik
    ```
5.  **Onay ve Birleştirme (Merge):** Yeterli onay alındığında ve tüm kontroller geçtiğinde, yetkili bir kişi (veya siz) platform arayüzündeki "Merge" butonuna tıklayarak değişiklikleri hedef branch'e birleştirir. Platformlar genellikle farklı birleştirme stratejileri sunar:
    *   **Merge Commit:** Standart `git merge` işlemi yapar, feature branch geçmişini korur ve bir merge commit oluşturur.
    *   **Squash and Merge:** Feature branch'indeki tüm commit'leri tek bir commit haline getirir ve bunu hedef branch'e ekler. Daha temiz bir ana branch geçmişi sağlar ancak detaylı feature branch geçmişini kaybeder.
    *   **Rebase and Merge:** Feature branch'indeki commit'leri hedef branch'in üzerine rebase eder ve sonra fast-forward merge yapar. Lineer bir geçmiş sağlar ancak `rebase`'in risklerini taşır (eğer yanlış kullanılırsa).

6.  **Branch Silme (Opsiyonel):** Birleştirme işleminden sonra, artık ihtiyaç kalmayan feature branch'ini hem yerelden hem de uzaktan silebilirsiniz. Çoğu platform, merge sonrası branch'i silmek için bir buton sunar.
    ```bash
    # Yerel branch'e geç (main'e veya başka bir branch'e)
    git checkout main
    # Yerel feature branch'ini sil
    git branch -d feature/harika-yeni-ozellik
    # Uzak feature branch'ini sil (eğer platform otomatik silmediyse)
    git push origin --delete feature/harika-yeni-ozellik
    ```

### 9.3 Kod İnceleme (Code Review)

Kod inceleme, PR/MR sürecinin kalbidir ve yazılım kalitesini artırmanın en etkili yollarından biridir.

**İyi Bir Kod İncelemesinin Amaçları:**

*   **Hataları Bulma:** Mantıksal hatalar, bug'lar, olası güvenlik açıkları.
*   **Kod Kalitesini Artırma:** Okunabilirlik, sürdürülebilirlik, performans iyileştirmeleri.
*   **Tasarım ve Mimariyi Değerlendirme:** Kodun genel yapıya uygunluğu, alternatif çözümlerin değerlendirilmesi.
*   **Bilgi Paylaşımı:** Takım üyelerinin projenin farklı bölümleri hakkında bilgi sahibi olması.
*   **Standartlara Uyumu Sağlama:** Kodlama stilleri, isimlendirme kuralları, en iyi pratikler.
*   **Mentörlük:** Deneyimli geliştiricilerin daha az deneyimli olanlara yol göstermesi.

**İnceleme Yaparken Dikkat Edilmesi Gerekenler:**

*   **Amacı Anlayın:** Değişikliğin neyi çözmeye çalıştığını anlamadan incelemeye başlamayın. PR açıklamasını okuyun, gerekirse sorular sorun.
*   **Yapıcı Olun:** Eleştirileri kişisel algılamayın ve yapıcı bir dille ifade edin. "Bu kod kötü" yerine "Burada şu yaklaşımı kullanmak daha okunabilir olabilir mi?" gibi.
*   **Net ve Anlaşılır Olun:** Sorunları veya önerileri açıkça belirtin. Kod örnekleri verin.
*   **Önem Sırasına Göre Yorum Yapın:** Küçük stil önerileri ile ciddi mantık hatalarını ayırt edin.
*   **Övgüyü Unutmayın:** İyi yapılmış işleri takdir etmek motivasyonu artırır.
*   **Zamanında Geri Bildirim Verin:** PR/MR'ları çok uzun süre bekletmeyin.

**PR/MR Sahibi Olarak Dikkat Edilmesi Gerekenler:**

*   **Küçük ve Odaklı PR/MR'lar Açın:** İncelemesi kolay, tek bir amaca hizmet eden değişiklikler gönderin.
*   **Açıklayıcı Başlık ve Açıklama Yazın:** İnceleyicinin işini kolaylaştırın. Neyi, neden ve nasıl yaptığınızı anlatın.
*   **Kendi Kodunuzu İnceleyin:** PR/MR açmadan önce kendi kodunuzu gözden geçirin, olası hataları veya eksikleri düzeltin.
*   **Geri Bildirimlere Açık Olun:** Eleştirileri savunmacı bir tavırla karşılamayın. Amaç kodun daha iyi olmasıdır.
*   **Yorumlara Cevap Verin:** Anlaşılmayan noktaları açıklayın, yapılan değişiklikleri belirtin.

---

## 10. Git Ustalığı: İleri Düzey Konular ve Teknikler

Temel komutlara hakim olduktan sonra, Git'in daha ileri düzey özelliklerini öğrenerek verimliliğinizi artırabilir ve karmaşık durumlarla başa çıkabilirsiniz.

### 10.1 Değişiklikleri Geçici Saklama (`stash`)

Bazen bir branch üzerinde çalışırken, henüz commit'lemeye hazır olmayan değişiklikleriniz varken acilen başka bir branch'e geçmeniz veya `pull` yapmanız gerekebilir. Çalışma dizininizi ve hazırlık alanınızı (staging area) kirletmeden bu geçişi yapmak için `git stash` kullanılır.

`git stash`, takip edilen dosyalardaki (tracked files) değiştirilmiş veya hazırlık alanına eklenmiş (staged) değişiklikleri geçici bir yığına (stack) kaydeder ve çalışma dizininizi son commit'teki (HEAD) temiz haline geri döndürür.

```bash
# Çalışma dizini ve hazırlık alanındaki değişiklikleri stash'le
git stash
# veya bir mesajla stash'le (hatırlamak için faydalı)
git stash save "Kullanıcı arayüzü üzerinde çalışıyordum"

# Stash'lenen değişiklikleri listele
git stash list
# Çıktı:
# stash@{0}: WIP on main: a1b2c3d feat: İlk commit
# stash@{1}: On feature/login: Kullanıcı arayüzü üzerinde çalışıyordum

# Son stash'lenen değişikliği geri uygula VE stash listesinden kaldır
git stash pop
# Belirli bir stash'i geri uygula (örn: stash@{1}) VE listeden kaldır
git stash pop stash@{1}

# Son stash'lenen değişikliği geri uygula AMA stash listesinde TUT
git stash apply
# Belirli bir stash'i geri uygula AMA listede TUT
git stash apply stash@{1}

# Stash'teki değişiklikleri göster (son stash)
git stash show
# Stash'teki değişiklikleri diff olarak göster (son stash)
git stash show -p
# Belirli bir stash'in diff'ini göster
git stash show -p stash@{1}

# Belirli bir stash'i listeden sil
git stash drop stash@{1}

# Tüm stash listesini temizle (DİKKATLİ OLUN!)
git stash clear

# Stash'i yeni bir branch olarak oluşturma (kullanışlı!)
git stash branch <yeni_branch_adi> stash@{0}
```

*Not:* Varsayılan olarak `git stash`, `untracked` (izlenmeyen) veya `.gitignore` ile yoksayılan dosyaları kaydetmez. İzlenmeyen dosyaları da stash'lemek için `git stash -u` veya `git stash --include-untracked` kullanılır. Tüm dosyaları (yoksayılanlar dahil) stash'lemek için `git stash -a` veya `git stash --all`.

### 10.2 Sürümleri İşaretleme (`tag`)

Proje geçmişindeki belirli önemli noktaları (genellikle sürüm yayınları) işaretlemek için `tag` (etiket) kullanılır. Commit hash'leri gibi hatırlanması zor karakter dizileri yerine, `v1.0`, `v2.1-beta` gibi anlamlı isimlerle o noktaya kolayca erişim sağlar.

İki tür tag vardır:

1.  **Lightweight Tag (Hafif Etiket):** Sadece belirli bir commit'e işaret eden bir etikettir, başka bilgi içermez. Geçici veya sadece kişisel kullanım için olan etiketler için uygundur.
    ```bash
    # Mevcut HEAD commit'ine hafif bir etiket ekle
    git tag v1.0-lw

    # Geçmişteki bir commit'e hafif etiket ekle
    git tag v0.9-lw <commit_hash>
    ```

2.  **Annotated Tag (Açıklamalı Etiket):** Git veritabanında tam bir obje olarak saklanır. Etiketleyen kişinin adını, e-postasını, tarihini ve bir etiketleme mesajını içerir. Genellikle GPG ile imzalanabilir. **Resmi sürüm yayınları için önerilen türdür.**
    ```bash
    # Mevcut HEAD commit'ine açıklamalı bir etiket ekle (editör açılır)
    git tag -a v1.0 -m "Sürüm 1.0 yayınlandı"

    # Geçmişteki bir commit'e açıklamalı etiket ekle
    git tag -a v0.9 -m "Sürüm 0.9 stabil sürüm" <commit_hash>

    # İmzalı bir etiket oluştur (GPG anahtarınızın ayarlı olması gerekir)
    git tag -s v1.0-signed -m "İmzalı Sürüm 1.0"
    ```

**Tag Yönetimi:**

```bash
# Tüm etiketleri listele
git tag

# Belirli bir desene uyan etiketleri listele
git tag -l "v1.*"

# Belirli bir etiketin detaylarını göster (açıklamalı etiketler için)
git show v1.0

# Etiketleri Uzak Depoya Gönderme (`push`):
# `git push` varsayılan olarak etiketleri göndermez.
# Belirli bir etiketi gönder
git push origin v1.0

# TÜM yerel etiketleri uzak depoya gönder (dikkatli kullanın)
git push origin --tags

# Etiket Silme:
# Yerel etiketi sil
git tag -d v1.0-lw

# Uzak depodaki etiketi sil (branch silme ile aynı syntax)
git push origin --delete tag v1.0
# veya eski syntax:
# git push origin :refs/tags/v1.0
```

### 10.3 Commit Ayıklama (`cherry-pick`)

Farklı bir branch'teki **tek bir commit'in** yaptığı değişiklikleri alıp mevcut branch'inize **yeni bir commit olarak** uygulamak için `git cherry-pick` kullanılır.

Bu, bir hata düzeltmesini (`hotfix`) birden fazla release branch'ine uygulamak veya bir feature branch'indeki sadece belirli bir commit'i ana branch'e erkenden dahil etmek gibi durumlarda kullanışlıdır.

```bash
# 1. Hedef branch'e geçin
git checkout main

# 2. Diğer branch'teki istediğiniz commit'in hash'ini bulun (git log ile)
# Örneğin, 'develop' branch'indeki 'a1b2c3d' hash'li commit'i alacağız
git log develop --oneline

# 3. Commit'i mevcut branch'e (main) uygula
git cherry-pick a1b2c3d
```

*   `cherry-pick` işlemi de çakışmalara neden olabilir. Çakışma olursa, normal `merge`/`rebase` çakışması gibi çözülür (`dosyayı düzenle`, `git add <dosya>`, `git cherry-pick --continue`). İptal etmek için `git cherry-pick --abort`.
*   `cherry-pick` yeni bir commit oluşturur (orijinal commit ile aynı mesajla başlar ama farklı hash'e sahip olur).

### 10.4 İnteraktif Rebase (`rebase -i`) ile Geçmişi Düzenleme

`git rebase -i` (interactive), commit geçmişinizi yeniden yazmak için çok güçlü bir araçtır. Henüz uzak depoya göndermediğiniz bir dizi commit üzerinde çeşitli işlemler yapmanızı sağlar:

*   **Commit'leri Yeniden Sıralama:** Commit'lerin uygulama sırasını değiştirme.
*   **Commit Mesajlarını Düzenleme:** `reword`
*   **Commit'leri Birleştirme:** `squash` (önceki commit ile birleştirir, mesajları birleştirme imkanı sunar), `fixup` (önceki commit ile birleştirir, sadece önceki commit'in mesajını kullanır).
*   **Commit'leri Silme:** `drop`
*   **Commit'i Düzenleme:** `edit` (Commit'i uygular ama durur, böylece değişiklik yapabilir, yeni commit ekleyebilir veya `--amend` yapabilirsiniz. Sonra `git rebase --continue` ile devam edersiniz).
*   **Yeni Komutlar Çalıştırma:** `exec` (Rebase sırasında belirli bir noktada shell komutu çalıştırma, örn: testleri çalıştırma).

**Kullanım:**

```bash
# Son 3 commit üzerinde interaktif rebase başlat
git rebase -i HEAD~3

# Belirli bir commit'e KADAR olan commit'ler üzerinde interaktif rebase başlat
# (Dikkat: Belirtilen commit dahil edilmez, ondan SONRAKİLER düzenlenir)
git rebase -i <commit_hash_parent>
```

Bu komutlardan birini çalıştırdığınızda, metin editörünüz açılır ve düzenlenecek commit'lerin bir listesi gösterilir. Her satırın başında `pick` yazar. Yapmak istediğiniz işleme göre bu `pick` kelimesini değiştirmeniz gerekir.

**Örnek Editör Ekranı:**

```
pick a1b2c3d feat: İlk bölüm eklendi
pick e4f5g6h fix: Yazım hatası düzeltildi
pick 7i8j9k0 feat: İkinci bölüm eklendi

# Rebase 1234567..7i8j9k0 onto 1234567 (3 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to re-edit the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
```

**Örnek Kullanım Senaryosu:** İkinci commit'in (`e4f5g6h`) mesajını düzeltmek ve üçüncü commit'i (`7i8j9k0`) birinciyle (`a1b2c3d`) birleştirmek (mesajlarını birleştirerek).

**Düzenlenmiş Editör Ekranı:**

```
pick a1b2c3d feat: İlk bölüm eklendi
reword e4f5g6h fix: Yazım hatası düzeltildi # 'pick' yerine 'reword' yazdık
squash 7i8j9k0 feat: İkinci bölüm eklendi # 'pick' yerine 'squash' yazdık
```

Dosyayı kaydedip kapattığınızda:

1.  Git önce `a1b2c3d` commit'ini uygular.
2.  Sonra `e4f5g6h` commit'i için editörü tekrar açar, mesajı düzenlemenizi ister. Kaydedip kapatırsınız.
3.  Sonra `7i8j9k0` commit'ini bir öncekiyle (`a1b2c3d`) birleştirmeye çalışır ve birleştirilmiş commit için yeni bir mesaj yazmanız (veya mevcutları düzenlemeniz) için editörü açar. Kaydedip kapatırsınız.

**UYARI:** İnteraktif rebase de **geçmişi yeniden yazar**. Bu nedenle **"The Golden Rule of Rebasing"** burada da geçerlidir: Asla paylaşılan branch'lerdeki commit'ler üzerinde kullanmayın. Pull Request açmadan önce yerel feature branch'inizi temizlemek için harikadır.

### 10.5 Kayıp İşleri Bulma (`reflog`)

Git, HEAD işaretçisinin ve branch referanslarının **sadece yerel deponuzdaki** hareketlerini kaydeden bir referans günlüğü tutar. Bu günlüğe `git reflog` ile erişilebilir.

`reflog`, yanlışlıkla yaptığınız `reset --hard`, `rebase`, `branch -D` gibi **geçmişi değiştiren veya commit kaybına neden olabilecek** işlemlerden sonra kaybolduğunu düşündüğünüz commit'leri bulmak ve kurtarmak için can simididir.

```bash
git reflog
# Çıktı örneği:
# a1b2c3d HEAD@{0}: reset: moving to HEAD~1
# e4f5g6h HEAD@{1}: commit: Yeni özellik eklendi
# 1234567 HEAD@{2}: checkout: moving from feature/x to main
# 7i8j9k0 HEAD@{3}: commit (amend): Başlık düzeltildi
# ...
```

Çıktıdaki her satır, HEAD'in geçmişteki bir konumunu gösterir. En üstteki en yenisidir. Soldaki hash (`a1b2c3d`, `e4f5g6h` gibi), o andaki commit'in hash'idir. `HEAD@{n}` syntax'ı, o duruma referans vermek için kullanılabilir.

**Kayıp Commit'i Kurtarma:**

Diyelim ki `git reset --hard HEAD~1` ile son commit'inizi sildiniz.

1.  `git reflog` çalıştırın.
2.  Silinen commit'i bulun (örn: `e4f5g6h HEAD@{1}: commit: Yeni özellik eklendi`).
3.  O commit'e geri dönmek için `reset` kullanabilirsiniz:
    ```bash
    # O commit'e geri dön (en güvenli yol genellikle yeni bir branch oluşturmaktır)
    git checkout -b kurtarilan-commit e4f5g6h
    # veya eğer mevcut branch'i o duruma getirmek isterseniz (dikkatli olun):
    # git reset --hard e4f5g6h
    ```

`reflog` kayıtları sonsuza kadar tutulmaz, belirli aralıklarla temizlenir (genellikle 90 gün), ancak yakın zamanda yapılan işlemler için çok değerlidir. `reflog` sadece yereldir, uzak depoya gönderilmez.

### 10.6 Hatanın Kaynağını Bulma (`bisect`)

Projenizde bir hata (bug) olduğunu fark ettiniz, ancak bu hatanın hangi commit ile geldiğini bilmiyorsunuz. Yüzlerce commit arasında elle aramak yerine `git bisect` komutunu kullanarak bu süreci otomatikleştirebilirsiniz.

`git bisect`, ikili arama (binary search) algoritmasını kullanarak hataya neden olan commit'i verimli bir şekilde bulmanızı sağlar.

**Kullanım Adımları:**

1.  **Bisect Modunu Başlat:**
    ```bash
    git bisect start
    ```
2.  **"Kötü" (Hatalı) Commit'i İşaretle:** Hatanın var olduğunu bildiğiniz mevcut veya yakın zamandaki bir commit'i işaretleyin. Genellikle bu mevcut HEAD'dir.
    ```bash
    git bisect bad
    # veya belirli bir commit ise:
    # git bisect bad <hatali_commit_hash>
    ```
3.  **"İyi" (Hatasız) Commit'i İşaretle:** Hatanın **olmadığını** bildiğiniz geçmişteki bir commit'i işaretleyin. Bu genellikle eski bir tag veya bilinen stabil bir commit olur.
    ```bash
    git bisect good v1.0
    # veya belirli bir commit hash'i:
    # git bisect good <hatasiz_commit_hash>
    ```
4.  **Test Etme Döngüsü:** Git şimdi `bad` ve `good` commit'leri arasındaki commit geçmişinin tam ortasındaki bir commit'e otomatik olarak `checkout` yapacaktır. Bu noktada:
    *   Projenizi derleyin/çalıştırın.
    *   Hatanın bu commit'te **olup olmadığını** test edin.
    *   Sonuca göre Git'e bildirin:
        *   Eğer hata **varsa**: `git bisect bad`
        *   Eğer hata **yoksa**: `git bisect good`
5.  **Tekrarlama:** Git, arama aralığını daraltarak (kalan commit'lerin ortasına giderek) 4. adımı tekrarlamanızı isteyecektir. Siz `bad`/`good` dedikçe Git aralığı küçültür.
6.  **Sonuç:** Birkaç adımdan sonra Git, hatayı ilk getiren commit'i bulacak ve size bildirecektir: `"<commit_hash> is the first bad commit"`
7.  **Bisect Modundan Çık:** Hatalı commit'i bulduktan sonra, `bisect` modundan çıkıp başlangıçtaki branch'inize dönmek için:
    ```bash
    git bisect reset
    ```

**Otomatikleştirme (`git bisect run`):** Eğer hatayı kontrol eden bir test script'iniz varsa (script hata varsa sıfır dışında bir exit kodu, hata yoksa sıfır exit kodu döndürmeli), `bisect` işlemini tamamen otomatikleştirebilirsiniz:

```bash
git bisect start HEAD v1.0 # Başlangıç ve bitiş noktaları
git bisect run ./test_script.sh # Hata kontrol script'ini çalıştır
# Git script'i her adımda çalıştırıp bad/good kararını otomatik verir.
git bisect reset
```

### 10.7 Alt Modüller (`submodule`)

Bir Git deposu içinde başka bir Git deposunu (genellikle harici bir kütüphane veya paylaşılan bir bileşen) barındırmanız ve yönetmeniz gerektiğinde `git submodule` kullanılır. Alt modül, ana projenizin belirli bir commit'ine bağlı kalır.

**Alt Modül Ekleme:**

```bash
# Belirtilen URL'deki depoyu, belirtilen yola bir alt modül olarak ekle
git submodule add <repository_url> <path>
# Örnek: 'lib/tema' klasörüne bir tema deposunu ekle
git submodule add https://github.com/kullanici/tema.git lib/tema
```

Bu işlem şunları yapar:

*   Belirtilen yolda (`lib/tema`) alt modül deposunu klonlar.
*   `.gitmodules` adında bir dosya oluşturur veya günceller. Bu dosya, alt modüllerin URL'lerini ve yollarını içerir.
*   Ana projede, alt modülün eklendiği yolda (`lib/tema`) özel bir "commit" girdisi oluşturur. Bu girdi, alt modülün hangi commit'ine işaret ettiğini belirtir.
*   `.gitmodules` dosyasını ve alt modül girdisini hazırlık alanına ekler. Bunları commit'lemeniz gerekir.

```bash
git add .gitmodules lib/tema
git commit -m "feat: Tema alt modülünü ekle"
```

**Alt Modül İçeren Projeyi Klonlama:**
Normal `git clone` işlemi, alt modüllerin içeriğini otomatik olarak indirmez.

```bash
# 1. Ana projeyi klonla
git clone <ana_proje_url>
cd <ana_proje_klasoru>

# 2. Alt modülleri başlat ve güncelle (içeriklerini indir)
git submodule init
git submodule update

# VEYA klonlarken hepsini tek seferde yap:
git clone --recurse-submodules <ana_proje_url>
```

**Alt Modülleri Güncelleme:**
Ana projenizdeki alt modülün daha yeni bir commit'e işaret etmesini sağlamak için:

```bash
# 1. Alt modül klasörüne gir
cd lib/tema

# 2. Alt modülün kendi deposunda son değişiklikleri çek
git checkout main # veya ilgili branch
git pull

# 3. Ana projeye geri dön
cd ../..

# 4. Ana projede alt modülün yeni commit'ini kaydet
git add lib/tema
git commit -m "chore: Tema alt modülünü güncelle"
```

**Başkalarının Yaptığı Alt Modül Güncellemelerini Alma:**
Eğer başka biri alt modülün işaret ettiği commit'i güncelleyip ana projeye push ettiyse, siz `pull` yaptıktan sonra kendi yerel alt modül kopyanızı güncellemeniz gerekir:

```bash
# 1. Ana projede değişiklikleri çek
git pull origin main

# 2. Yerel alt modül kopyalarını güncellenmiş commit'lere getir
git submodule update --init --recursive
```

Alt modüller güçlüdür ancak yönetimi bazen karmaşık olabilir. Alternatif olarak, projenizin diline özgü paket yöneticileri (npm, composer, pip, Maven vb.) veya Git LFS (Bölüm 10.8) gibi araçlar düşünülebilir.

### 10.8 Büyük Dosyaları Yönetme (Git LFS)

Git, kaynak kodu gibi metin tabanlı dosyaların sürümlenmesi için optimize edilmiştir. Büyük ikili dosyaları (resimler, videolar, ses dosyaları, veri setleri, derlenmiş kütüphaneler vb.) doğrudan Git deposuna eklemek, deponun boyutunu hızla şişirir, klonlama ve fetch işlemlerini yavaşlatır.

**Git Large File Storage (LFS)**, bu sorunu çözmek için geliştirilmiş bir Git eklentisidir. Büyük dosyaları doğrudan Git deposunda saklamak yerine, bu dosyaları ayrı bir LFS sunucusunda saklar ve Git deposunda sadece bu dosyalara işaret eden **küçük metin işaretçilerini (pointer)** tutar.

**Kurulum (Bir kerelik):**

1.  Git LFS'i indirip kurun: [https://git-lfs.github.com/](https://git-lfs.github.com/) (Homebrew: `brew install git-lfs`, Linux: paket yöneticisiyle `git-lfs`)
2.  Git LFS'i kullanıcı hesabınız için kurun (tüm depolarınız için):
    ```bash
    git lfs install
    ```
3.  (Opsiyonel) Mevcut bir depo için kurmak isterseniz:
    ```bash
    cd /path/to/repo
    git lfs install
    ```

**Kullanım:**

1.  **Hangi Dosyaların LFS ile İzleneceğini Belirle (`track`):** Projenizin kök dizininde `git lfs track` komutu ile hangi dosya türlerinin veya belirli dosyaların LFS tarafından yönetileceğini belirtin. Bu komut, `.gitattributes` adında bir dosya oluşturur veya günceller.
    ```bash
    # Tüm .psd dosyalarını LFS ile izle
    git lfs track "*.psd"

    # assets/videos klasöründeki tüm .mp4 dosyalarını izle
    git lfs track "assets/videos/*.mp4"

    # Belirli bir büyük dosyayı izle
    git lfs track "data/large_dataset.bin"
    ```
2.  **`.gitattributes` Dosyasını Commit'le:** `.gitattributes` dosyası, Git'e hangi dosyaların LFS ile yönetileceğini söyler, bu yüzden mutlaka commit'lenmelidir.
    ```bash
    git add .gitattributes
    git commit -m "chore: Git LFS izleme kurallarını yapılandır"
    ```
3.  **Büyük Dosyaları Ekle ve Commit'le:** Artık LFS tarafından izlenen büyük dosyaları normal şekilde `git add` ve `git commit` ile ekleyebilirsiniz.
    ```bash
    git add assets/videos/intro.mp4
    git add design.psd
    git commit -m "feat: Tanıtım videosu ve tasarım dosyası eklendi"
    ```
    `commit` işlemi sırasında Git LFS, büyük dosyaların içeriğini LFS sunucusuna yükler ve Git deposuna sadece işaretçi dosyalarını kaydeder.
4.  **Değişiklikleri Push Et:** Normal `git push` komutu, hem Git commit'lerini hem de LFS dosyalarını (işaretçiler ve gerekirse gerçek dosyalar) uzak sunucuya gönderir.
    ```bash
    git push origin main
    ```

**LFS ile Çalışırken:**

*   **Klonlama (`clone`):** Normal `git clone` işlemi, LFS işaretçilerini alır ancak büyük dosyaların gerçek içeriklerini indirmez. İçerikleri indirmek için klonlama sonrası `git lfs pull` gerekir veya klonlarken otomatik indirmeyi sağlamak için `git clone` yeterlidir (modern Git/LFS sürümlerinde genellikle varsayılan davranış budur).
*   **Çekme (`pull`):** `git pull` komutu hem Git değişikliklerini hem de ilgili LFS dosyalarının güncel sürümlerini otomatik olarak indirir.
*   **Geçmişteki Dosyaları LFS'e Taşıma:** Eğer depoya yanlışlıkla büyük dosyalar commit'lediyseniz, `git lfs migrate` komutu ile geçmişi yeniden yazarak bu dosyaları LFS'e taşıyabilirsiniz (bu işlem **geçmişi değiştirir**, dikkatli olun!).

GitHub, GitLab, Bitbucket gibi platformlar genellikle ücretsiz veya belirli limitler dahilinde Git LFS desteği sunar.

### 10.9 Git Kancaları (`hooks`)

Git kancaları (`hooks`), Git iş akışındaki belirli olaylar (örn: commit öncesi, push öncesi, commit sonrası) gerçekleştiğinde otomatik olarak çalışan script'lerdir.

*   **Amaç:** Kod stilini kontrol etmek, commit mesajlarını doğrulamak, testleri çalıştırmak, dağıtım script'lerini tetiklemek gibi işlemleri otomatikleştirmek.
*   **Konum:** Her Git deposunun `.git/hooks` klasöründe bulunurlar. Varsayılan olarak `.sample` uzantılı örnek script'ler bulunur. Bir kancayı aktif etmek için `.sample` uzantısını kaldırmanız yeterlidir.
*   **Türleri:**
    *   **Client-Side Hooks (İstemci Taraflı):** Sizin yerel deponuzda çalışır. Örnekler:
        *   `pre-commit`: `git commit` komutu çalıştırıldığında, mesaj yazılmadan *önce* çalışır. Kod linting, stil kontrolü veya basit testler için idealdir. Eğer script sıfır dışında bir exit koduyla biterse, commit işlemi iptal edilir.
        *   `prepare-commit-msg`: Commit mesajı editörü açılmadan önce çalışır. Commit mesajını otomatik olarak düzenlemek veya şablon eklemek için kullanılır.
        *   `commit-msg`: Commit mesajı yazılıp kapatıldıktan *sonra* çalışır. Mesajın formatını (örn: Conventional Commits) veya içeriğini doğrulamak için kullanılır. Eğer script sıfır dışında biterse, commit iptal edilir.
        *   `post-commit`: Commit işlemi başarıyla tamamlandıktan *sonra* çalışır. Bildirim göndermek vb. için kullanılabilir.
        *   `pre-push`: `git push` komutu çalıştırıldığında, uzak depoya gönderilmeden *önce* çalışır. Daha kapsamlı testlerin çalıştırılması veya push işleminin belirli koşullara göre engellenmesi için kullanılır. Sıfır dışında biterse push iptal edilir.
        *   Diğerleri: `applypatch-msg`, `pre-applypatch`, `post-applypatch`, `pre-rebase`, `post-rewrite`, `post-checkout`, `post-merge`, `pre-auto-gc`.
    *   **Server-Side Hooks (Sunucu Taraflı):** Git sunucusunda çalışır. Genellikle Git barındırma hizmetleri (GitHub Enterprise, GitLab self-hosted, Gerrit vb.) tarafından yönetilir veya özel Git sunucularında kullanılır. Proje politikalarını uygulamak, erişim kontrolü yapmak, bildirim sistemlerini entegre etmek için kullanılır. Örnekler: `pre-receive`, `update`, `post-receive`.

**Kanca Yazma:** Kancalar herhangi bir çalıştırılabilir script olabilir (shell, Python, Ruby, Perl vb.). Script'in başına shebang (`#!/bin/sh` veya `#!/usr/bin/env python`) eklemek yaygındır.

**Örnek `pre-commit` (Shell):** Basit bir Python lint kontrolü

```bash
#!/bin/sh

# Sadece .py uzantılı ve hazırlık alanındaki (staged) dosyaları kontrol et
STAGED_PY_FILES=$(git diff --cached --name-only --diff-filter=ACM | grep '\.py$')

if [ -z "$STAGED_PY_FILES" ]; then
  exit 0 # Python dosyası yoksa başarılı çık
fi

echo "Running flake8 linter..."

# flake8 kurulu olmalı (pip install flake8)
flake8 $STAGED_PY_FILES

# flake8'in exit kodunu kontrol et
if [ $? -ne 0 ]; then
  echo "Linting failed. Please fix the errors before committing."
  exit 1 # Hata varsa commit'i engelle
fi

exit 0 # Başarılı
```

**Dikkat:** `.git/hooks` klasörü Git tarafından takip edilmez ve klonlanmaz/push edilmez. Takım içinde ortak kancalar kullanmak için genellikle bu script'leri projenin normal bir klasöründe tutup, geliştiricilerin bunları `.git/hooks` altına manuel olarak kopyalamasını veya sembolik link oluşturmasını sağlamak ya da [Husky](https://typicode.github.io/husky/), [pre-commit](https://pre-commit.com/) gibi araçlar kullanmak gerekir.

---

## 11. `.gitignore` Dosyası ve İncelikleri

Projenizde Git tarafından **izlenmemesi** gereken dosyalar veya klasörler bulunur. Bunlar genellikle derlenmiş kodlar, bağımlılık klasörleri (örn: `node_modules`), log dosyaları, işletim sistemi veya IDE'ye özgü geçici dosyalar, hassas bilgiler içeren yapılandırma dosyaları vb. olabilir.

`git add .` gibi komutlarla bu dosyaları yanlışlıkla hazırlık alanına eklememek ve `git status` çıktısını temiz tutmak için `.gitignore` dosyası kullanılır.

### 11.1 `.gitignore` Nasıl Çalışır?

*   Projenizin kök dizinine (veya alt dizinlerine) `.gitignore` adında bir metin dosyası oluşturursunuz.
*   Bu dosyaya, Git'in yoksaymasını istediğiniz dosya veya klasör desenlerini (pattern) her satıra bir tane olacak şekilde yazarsınız.
*   Git, bir dosyanın takip edilip edilmeyeceğine karar verirken `.gitignore` dosyalarındaki desenleri kontrol eder. Eşleşen dosyalar genellikle `git status`'te "untracked" olarak bile görünmez ve `git add .` ile eklenmez.
*   `.gitignore` dosyası da projenizin bir parçası olduğu için **commit edilmelidir**, böylece projenin diğer klonlarında da aynı dosyalar yoksayılır.

### 11.2 Yaygın Kullanım Desenleri

`.gitignore` dosyası standart glob desenlerini kullanır:

```gitignore
# Yorumlar '#' ile başlar

# Belirli bir dosyayı yoksay
config.local.yaml
secret_key.pem

# Belirli bir klasördeki tüm dosyaları yoksay
logs/
build/
dist/

# Belirli bir uzantıya sahip tüm dosyaları yoksay
*.log
*.tmp
*.swp # Vim swap dosyaları

# Belirli bir klasördeki belirli uzantılı dosyaları yoksay
/node_modules/
/vendor/

# Klasörleri yoksay ama içindeki belirli dosyaları yoksayma
# Önce klasörü yoksay
temp/
# Sonra yoksayılmayacak dosyayı belirt (başına ! koyarak)
!temp/important.txt

# Belirli bir dosyayı yoksay ama alt dizinlerde değilse
# (Sadece kök dizindeki .env dosyası)
/.env

# Tüm 'debug.log' dosyalarını yoksay, ama 'src/debug.log' hariç
debug.log
!src/debug.log

# İşletim Sistemi ve IDE dosyaları
.DS_Store
Thumbs.db
.vscode/
.idea/
*.suo
*.user
```

*   **gitignore.io (veya topal.com/gitignore):** Projenizde kullandığınız teknolojilere (Node, Python, Java, VSCode, macOS vb.) göre otomatik olarak `.gitignore` dosyası oluşturmanıza yardımcı olan harika bir araçtır.

### 11.3 Zaten Takip Edilen Dosyaları Yoksayma

Eğer yanlışlıkla yoksaymanız gereken bir dosyayı (`config.local.yaml` gibi) daha önce commit'lediyseniz, bu dosyayı `.gitignore`'a eklemek tek başına yeterli olmaz. Git zaten o dosyayı takip ettiği için yoksaymaz.

Bu dosyayı Git takibinden çıkarmak (ancak yerel diskinizden silmeden) ve ardından `.gitignore`'a eklemek gerekir:

```bash
# 1. Dosyayı Git takibinden çıkar (staging area'dan kaldırır)
git rm --cached config.local.yaml
# Eğer bir klasörse:
# git rm -r --cached logs/

# 2. .gitignore dosyasını düzenle veya oluştur ve dosya/klasör adını ekle
echo "config.local.yaml" >> .gitignore
# veya
echo "logs/" >> .gitignore

# 3. Değişiklikleri commit'le
git add .gitignore
git commit -m "chore: config.local.yaml ve logs/ yoksayma listesine eklendi ve takipten çıkarıldı"
```

Artık `config.local.yaml` ve `logs/` klasörü yerel diskinizde durmaya devam eder, ancak Git tarafından takip edilmez ve sonraki commit'lere dahil edilmez.

### 11.4 Global `.gitignore`

Bazen belirli dosya türlerini (örn: işletim sistemine özgü `.DS_Store` veya editör yedek dosyaları `*~`) **tüm** Git depolarınızda yoksaymak isteyebilirsiniz. Her projeye tek tek eklemek yerine global bir `.gitignore` dosyası tanımlayabilirsiniz.

```bash
# 1. Global .gitignore dosyasını oluştur (genellikle kullanıcı ana dizininde)
touch ~/.gitignore_global

# 2. Git'e bu dosyayı kullanmasını söyle
git config --global core.excludesfile ~/.gitignore_global

# 3. Global yoksayma dosyasını düzenle
# nano ~/.gitignore_global veya tercih ettiğiniz editörle açıp desenleri ekleyin
# Örnek içerik:
# .DS_Store
# Thumbs.db
# *~
# .vscode/
```

Bu global dosya sadece sizin yerel makinenizdeki tüm depoları etkiler, projenin kendisiyle birlikte commit edilmez.

---

## 12. Verimli Çalışma: Popüler Git İş Akışları (Workflows)

Git'in esnekliği, takımların farklı ihtiyaçlarına uygun çeşitli iş akışları (workflows) geliştirmesine olanak tanımıştır. Doğru iş akışını seçmek ve tutarlı bir şekilde uygulamak, takım çalışmasını organize etmek, kod kalitesini korumak ve sürüm yönetimini kolaylaştırmak için önemlidir.

### 12.1 Feature Branch Workflow

*   **Temel Fikir:** Tüm yeni geliştirmeler (yeni özellikler, hata düzeltmeleri) ana branch'ten (`main`) ayrılan kısa ömürlü **feature branch**'lerinde yapılır. İş tamamlandığında, feature branch ana branch'e **Pull Request (PR) / Merge Request (MR)** aracılığıyla birleştirilir.
*   **Ana Branch (`main`):** Her zaman **üretim (production) ortamına dağıtılabilecek**, stabil ve test edilmiş kodu temsil eder. Doğrudan `main` branch'ine commit yapılmaz.
*   **Feature Branch'ler:**
    *   Genellikle `feature/`, `fix/`, `hotfix/`, `chore/` gibi öneklerle isimlendirilir (örn: `feature/user-authentication`, `fix/login-button-bug`).
    *   Geliştirici, işe başlamadan önce `main`'den yeni bir branch oluşturur.
    *   Değişikliklerini bu branch'e commit'ler.
    *   İşi bitince branch'i uzak depoya push eder ve `main`'e birleştirmek için PR/MR açar.
    *   Kod incelemesi ve onay sonrası PR/MR birleştirilir.
    *   Feature branch silinir.
*   **Avantajları:**
    *   Basit ve anlaşılması kolaydır.
    *   `main` branch'i her zaman temiz ve dağıtıma hazır kalır.
    *   Kod incelemesi PR/MR süreciyle kolayca entegre edilir.
    *   Geliştiriciler izole bir şekilde çalışabilir.
*   **Dezavantajları:**
    *   Karmaşık sürüm yönetimi veya birden fazla ortam (staging, production) için ek kurallar gerekebilir.
*   **Kullanım Alanı:** Küçük ve orta ölçekli takımlar, sürekli teslimat (Continuous Delivery) yapan projeler için çok uygundur. GitHub Flow ve GitLab Flow bu temel iş akışının varyasyonlarıdır.

### 12.2 Gitflow Workflow

*   **Temel Fikir:** Feature Branch Workflow'dan daha katı kurallara sahip, daha yapılandırılmış bir modeldir. Farklı türde işler için özel amaçlı, uzun ömürlü branch'ler kullanır. Vincent Driessen tarafından popüler hale getirilmiştir.
*   **Ana Branch'ler (Uzun Ömürlü):**
    *   `main` (veya `master`): Sadece **üretim (production) sürümlerini** içerir. Her commit bir sürüm numarası ile etiketlenir (`tag`). Doğrudan commit yapılmaz, sadece `release` veya `hotfix` branch'lerinden merge edilir.
    *   `develop`: Ana geliştirme branch'idir. Tamamlanmış özellikler ve bir sonraki sürüm için hazırlanan kodlar buraya entegre edilir. Gecelik build'ler veya staging ortamı genellikle bu branch'ten yapılır. `main` kadar stabil olması beklenmez ama derlenebilir/çalışabilir durumda olmalıdır.
*   **Destekleyici Branch'ler (Kısa Ömürlü):**
    *   **Feature Branch'ler (`feature/*`):** Yeni özellikler geliştirmek için `develop` branch'inden ayrılır. İş bitince tekrar `develop`'a merge edilir (PR/MR ile). `main`'e doğrudan dokunmazlar.
    *   **Release Branch'ler (`release/*`):** Yeni bir üretim sürümü hazırlamak için `develop`'tan ayrılır. Bu branch üzerinde sadece küçük hata düzeltmeleri, dokümantasyon güncellemeleri ve sürüme özgü son hazırlıklar yapılır. Yeni özellik eklenmez. Hazır olduğunda hem `main`'e (sürüm olarak etiketlenir) hem de `develop`'a (yapılan son düzeltmeleri geri almak için) merge edilir. Sonra silinir.
    *   **Hotfix Branch'ler (`hotfix/*`):** Üretimdeki (`main`) kritik bir hatayı acilen düzeltmek için **doğrudan `main`'den** ayrılır. Düzeltme yapıldıktan sonra hem `main`'e (yeni bir patch sürümü olarak etiketlenir) hem de `develop`'a (düzeltmenin geliştirme ortamına da yansıması için) merge edilir. Sonra silinir.
*   **Avantajları:**
    *   Çok yapılandırılmış ve öngörülebilirdir.
    *   Paralel geliştirmeyi, sürüm hazırlığını ve acil durum düzeltmelerini net bir şekilde ayırır.
    *   Birden fazla sürümün aynı anda desteklenmesi gereken projeler için uygundur.
*   **Dezavantajları:**
    *   Feature Branch Workflow'a göre daha karmaşıktır.
    *   Daha fazla branch yönetimi gerektirir.
    *   Sürekli Teslimat (CD) yapan takımlar için bazen hantal olabilir (özellikle `release` branch süreci).
*   **Kullanım Alanı:** Belirli sürüm döngüleri olan, birden fazla sürümü destekleyen, daha büyük veya daha geleneksel projeler.

### 12.3 GitHub Flow / GitLab Flow

*   **GitHub Flow:** Feature Branch Workflow'un çok basit bir versiyonudur.
    *   `main` branch'i her zaman dağıtıma hazırdır.
    *   Yeni işler `main`'den ayrılan feature branch'lerinde yapılır.
    *   İş bitince PR açılır.
    *   PR onaylanınca ve testler geçince **doğrudan `main`'e merge edilir**.
    *   Merge edilen `main` branch'i **hemen dağıtıma gönderilir** (Continuous Deployment).
    *   `release` veya `develop` gibi ek branch'ler yoktur. Hotfix'ler de normal feature branch gibi ele alınır.
    *   **Avantajı:** Çok basit, hızlı, Sürekli Teslimat/Dağıtım (CI/CD) için ideal.
    *   **Dezavantajı:** Belirli sürümleri yönetmek veya birden fazla ortamı (staging) desteklemek için ek pratikler gerekebilir.
*   **GitLab Flow:** GitHub Flow'a benzer ancak ortam veya sürüm bazlı branch'ler ekleyerek daha fazla esneklik sunar.
    *   `main` branch'i yine ana geliştirme hattıdır ve genellikle üretim ortamını temsil eder.
    *   Feature branch'ler `main`'den ayrılır ve iş bitince MR ile `main`'e merge edilir.
    *   **Ortam Branch'leri (Opsiyonel):** `pre-production`, `staging`, `production` gibi uzun ömürlü branch'ler tanımlanabilir. `main`'den bu branch'lere merge işlemi, ilgili ortama dağıtımı tetikler (`main` -> `staging` -> `production` gibi).
    *   **Release Branch'leri (Opsiyonel):** Belirli sürümleri yönetmek için `main`'den release branch'leri oluşturulabilir (Gitflow'daki gibi ama genellikle sadece `main`'e merge edilir).
    *   **Avantajı:** GitHub Flow'dan daha esnektir, farklı dağıtım ve sürüm senaryolarına uyarlanabilir.
    *   **Dezavantajı:** GitHub Flow kadar basit değildir, ek branch yönetimi gerektirebilir.

### 12.4 Forking Workflow

*   **Temel Fikir:** Katkıda bulunan herkesin ana depo üzerinde doğrudan yazma izni olmadığı durumlarda (özellikle açık kaynak projelerde) kullanılır. Her katkıda bulunan, ana projenin **kendi kişisel kopyasını (fork)** oluşturur.
*   **Akış:**
    1.  **Fork:** Katkıda bulunmak istediğiniz orijinal (genellikle `upstream` olarak adlandırılır) depoyu GitHub/GitLab gibi platformlarda kendi hesabınıza "fork"larsınız. Bu, sunucu tarafında projenin tam bir kopyasını oluşturur (`origin`).
    2.  **Clone:** Kendi fork'ladığınız depoyu (`origin`) yerel makinenize klonlarsınız.
        ```bash
        git clone git@github.com:sizin-kullanici-adiniz/proje.git
        cd proje
        ```
    3.  **Upstream Remote Ekleme:** Orijinal depoyu takip etmek için yerel deponuza `upstream` adında bir remote eklersiniz. Bu, orijinal projeden güncellemeleri almanızı sağlar.
        ```bash
        git remote add upstream https://github.com/orijinal-kullanici/proje.git
        ```
    4.  **Branch Oluşturma:** Değişiklik yapmak için yerel deponuzda yeni bir feature branch oluşturursunuz (genellikle `upstream/main`'in güncel halinden).
        ```bash
        git fetch upstream
        git checkout -b feature/yeni-katki upstream/main
        ```
    5.  **Geliştirme ve Commit:** Değişikliklerinizi yapar ve yerel feature branch'inize commit'lersiniz.
    6.  **Push to Origin:** Feature branch'inizi kendi fork'unuza (`origin`) push edersiniz.
        ```bash
        git push -u origin feature/yeni-katki
        ```
    7.  **Pull Request (Upstream'e):** GitHub/GitLab arayüzünden, kendi fork'unuzdaki (`sizin-kullanici-adiniz/proje`) `feature/yeni-katki` branch'inden, orijinal depodaki (`orijinal-kullanici/proje`) `main` branch'ine bir Pull Request açarsınız.
    8.  **İnceleme ve Merge:** Proje sahipleri (maintainer) PR'ınızı inceler, geri bildirimde bulunur ve uygun görürlerse orijinal depoya merge ederler.
    9.  **Güncel Kalma:** Zamanla orijinal depo (`upstream`) güncellendikçe, kendi fork'unuzu ve yerel kopyanızı güncellemeniz gerekir:
        ```bash
        git checkout main
        git fetch upstream
        git merge upstream/main # Yerel main'i güncelle
        git push origin main    # Fork'unuzdaki main'i güncelle (isteğe bağlı)
        ```
*   **Avantajları:**
    *   Ana depoya doğrudan yazma izni olmayan çok sayıda katkıcı için idealdir.
    *   Proje sahiplerine tam kontrol sağlar.
    *   Her katkıcının kendi izole çalışma alanı olur.
*   **Dezavantajları:**
    *   Diğer iş akışlarına göre biraz daha fazla adım içerir (fork, upstream remote yönetimi).
*   **Kullanım Alanı:** Açık kaynak projeler, büyük organizasyonlarda farklı takımlar arası işbirliği.

**Hangi İş Akışını Seçmeli?**
Doğru iş akışı projenizin boyutuna, takım yapınıza, sürüm sıklığınıza ve dağıtım süreçlerinize bağlıdır. Genellikle basit başlayıp (Feature Branch veya GitHub Flow) ihtiyaçlar arttıkça daha yapılandırılmış modellere (GitLab Flow, Gitflow) geçmek veya uyarlamak iyi bir yaklaşımdır. En önemlisi, takım olarak bir iş akışı üzerinde anlaşmak ve bunu tutarlı bir şekilde uygulamaktır.

---

## 13. Sorun Giderme ve İpuçları

Git kullanırken kaçınılmaz olarak bazı kafa karıştırıcı durumlar veya hatalarla karşılaşabilirsiniz. Bu bölümde sık karşılaşılan sorunlara ve bazı kullanışlı ipuçlarına değineceğiz.

### 13.1 "Detached HEAD" Durumu

`git checkout` komutunu bir branch ismi yerine doğrudan bir commit hash'i, tag veya uzak izleme dalı (`origin/main` gibi) ile kullandığınızda "Detached HEAD" durumuna geçersiniz.

*   **Anlamı:** HEAD işaretçisi artık belirli bir yerel branch'e değil, doğrudan belirli bir commit'e işaret etmektedir. Sanki geçmişteki bir noktaya zaman yolculuğu yapmış gibisinizdir.
*   **Ne Yapılabilir:** Bu durumda geçmişi inceleyebilir, dosyaları görebilir, hatta test amaçlı geçici commit'ler bile yapabilirsiniz.
*   **Tehlikesi:** Eğer bu durumda yeni commit'ler yaparsanız ve sonra başka bir branch'e `checkout` yaparsanız, bu yeni (geçici) commit'ler hiçbir branch tarafından takip edilmediği için kaybolabilir (çöp toplayıcı tarafından silinebilir).
*   **Çözüm:**
    *   **Eğer sadece inceleme yapıyorsanız:** İşiniz bitince normal bir branch'e geri dönün: `git checkout main`
    *   **Eğer bu noktadan yeni bir geliştirme hattı başlatmak istiyorsanız:** Hemen yeni bir branch oluşturun. Bu, detached HEAD durumundayken yaptığınız (varsa) yeni commit'leri de bu yeni branch'e bağlar:
        ```bash
        # Detached HEAD durumundayken:
        git checkout -b yeni-feature-bu-noktadan
        ```
    *   **Eğer yanlışlıkla olduysa ve değişiklik yapmadıysanız:** Sadece normal bir branch'e geri dönün: `git checkout <branch_adi>`

`git status` komutu detached HEAD durumunda olduğunuzu size söyler.

### 13.2 Yanlış Commit/Rebase Sonrası Eski Duruma Dönme (`reflog` ve `reset`)

Yanlışlıkla `reset --hard` yaptınız, `rebase` işlemini karıştırdınız veya bir commit'i `amend` edip pişman oldunuz. Kısacası, kaybolduğunu düşündüğünüz commit'ler var. Panik yapmayın! `reflog` genellikle kurtarıcınızdır.

1.  **Referans Günlüğünü İncele (`reflog`):** Yerel deponuzdaki HEAD ve branch hareketlerinin günlüğünü görün. Geri dönmek istediğiniz durumun (commit'in) hash'ini bulun.
    ```bash
    git reflog
    # Örnek Çıktı:
    # c1a2b3d HEAD@{0}: rebase finished: returning to refs/heads/main
    # f4e5d6c HEAD@{1}: rebase: GHI commit'ini düzenle
    # a7b8c9d HEAD@{2}: rebase: DEF commit'ini uygula
    # 1234567 HEAD@{3}: rebase: starting rebase...
    # 8h9i0j1 HEAD@{4}: reset: moving to HEAD~2
    # k2l3m4n HEAD@{5}: commit: Yanlış commit
    # ...
    ```
2.  **İstediğiniz Duruma Dön (`reset` veya `checkout -b`):**
    *   Diyelim ki `reset --hard HEAD~2` (yani `8h9i0j1 HEAD@{4}`) işlemi yanlıştı ve `k2l3m4n HEAD@{5}` durumuna geri dönmek istiyorsunuz.
    *   **En Güvenli Yol:** O commit'ten yeni bir branch oluşturup durumu incelemek:
        ```bash
        git checkout -b kurtarma-branchi k2l3m4n
        ```
        Eğer her şey yolundaysa, bu branch'i kullanmaya devam edebilir veya mevcut branch'inizi bu duruma getirebilirsiniz.
    *   **Mevcut Branch'i Sıfırlama (Dikkatli):** Eğer mevcut branch'in doğrudan o eski duruma dönmesini istiyorsanız `reset --hard` kullanabilirsiniz (mevcut kaydedilmemiş değişiklikler kaybolur):
        ```bash
        git reset --hard k2l3m4n
        ```

Unutmayın, `reflog` sadece yereldir ve kayıtlar zamanla silinir.

### 13.3 PR Öncesi Branch'i Güncelleme (`rebase`/`merge`, `--force-with-lease`)

Feature branch'iniz üzerinde çalışırken, ana branch (`main` veya `develop`) ilerlemiş olabilir. Pull Request (PR) açmadan önce feature branch'inizi ana branch'teki son değişikliklerle güncellemek iyi bir pratiktir. Bu, olası çakışmaları erkenden yakalamanızı ve PR'ınızın temiz bir şekilde birleştirilmesini kolaylaştırır.

İki ana yöntem vardır:

1.  **Rebase (Tercih Edilen - Temiz Geçmiş İçin):** Feature branch'inizdeki commit'leri ana branch'in son commit'inin üzerine taşır. Lineer bir geçmiş oluşturur.
    ```bash
    # 1. Feature branch'indeyken ana branch'teki son değişiklikleri fetch et
    git fetch origin

    # 2. Feature branch'ini origin/main (veya origin/develop) üzerine rebase et
    git rebase origin/main
    # (Çakışma olursa çöz, git add ., git rebase --continue)

    # 3. Güncellenmiş feature branch'ini uzak depoya push et
    # Rebase geçmişi değiştirdiği için normal push reddedilir.
    # Force push gerekir, ANCAK --force-with-lease kullanın!
    git push --force-with-lease origin feature/benim-ozellik
    ```
    `--force-with-lease`, siz `fetch` yaptıktan sonra başka biri `feature/benim-ozellik` branch'ine push yapmışsa işlemi durdurarak veri kaybını önler. `--force`'dan çok daha güvenlidir.

2.  **Merge:** Ana branch'i feature branch'inize merge eder. Bir merge commit'i oluşturur, geçmiş dallı kalır.
    ```bash
    # 1. Feature branch'indeyken ana branch'teki son değişiklikleri fetch et
    git fetch origin

    # 2. origin/main'i mevcut feature branch'ine merge et
    git merge origin/main
    # (Çakışma olursa çöz, git add ., git commit)

    # 3. Güncellenmiş feature branch'ini uzak depoya push et (normal push yeterli)
    git push origin feature/benim-ozellik
    ```

Genellikle PR öncesi temiz bir geçmiş için `rebase` tercih edilir, ancak takımınızın iş akışına uymalısınız. Rebase yapıyorsanız, **mutlaka `--force-with-lease`** kullanın.

### 13.4 Git Kısayolları (`alias`)

Sık kullandığınız uzun Git komutları için kısayollar (alias) tanımlayarak zamandan kazanabilirsiniz. Alias'lar `git config` ile tanımlanır.

```bash
# Global olarak (tüm depolar için) alias tanımla

# git status -> git st
git config --global alias.st status

# git checkout -> git co
git config --global alias.co checkout

# git branch -> git br
git config --global alias.br branch

# git commit -> git ci
git config --global alias.ci commit

# git log --oneline --graph --decorate -> git logg
git config --global alias.logg "log --oneline --graph --decorate"

# git log (daha süslü format) -> git lol
git config --global alias.lol "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"

# Son commit'i geri al (değişiklikler unstaged) -> git undo
git config --global alias.undo "reset HEAD~1"

# Hazırlık alanındaki her şeyi geri al -> git unstage
git config --global alias.unstage "reset HEAD --"

# Tüm tanımlı alias'ları listele
git config --global --get-regexp alias

# Bir alias'ı kaldır
# git config --global --unset alias.st
```

Alias'ları tanımladıktan sonra `git st`, `git co feature/x`, `git lol` gibi kullanabilirsiniz.

---

## 14. Git'in İç Yapısı: Temel Objeler (İsteğe Bağlı)

Git'in nasıl çalıştığını daha derinden anlamak istiyorsanız, temel veri yapılarını bilmek faydalı olabilir. Bu bölüm zorunlu değildir ancak Git'in neden hızlı ve güçlü olduğunu anlamanıza yardımcı olur.

Git temel olarak bir **içerik adreslemeli dosya sistemidir (content-addressable filesystem)**. Yani, veriyi dosya adı veya konumuyla değil, içeriğinin **SHA-1 hash**'i ile adresler. `.git/objects` klasöründe dört temel obje türü bulunur:

### 14.1 Blob, Tree, Commit Objeleri

1.  **Blob (Binary Large Object):** Bir dosyanın içeriğini temsil eder. Başka hiçbir meta veri (dosya adı, tarih vb.) içermez, sadece dosyanın ham verisi. Aynı içeriğe sahip farklı dosya isimleri olsa bile, Git sadece bir tane blob objesi saklar. Obje adı, içeriğin SHA-1 hash'idir.
    ```bash
    # Bir dosyanın içeriğini hash'leyip blob olarak sakla ve hash'ini göster
    echo 'merhaba dünya' | git hash-object -w --stdin
    # Örnek Çıktı: 3b18e512dba79e4c8300dd08aeb37f8e728b8dad

    # Bir blob objesinin içeriğini göster
    git cat-file -p 3b18e512db # Hash'in ilk birkaç karakteri yeterli
    # Çıktı: merhaba dünya
    ```
2.  **Tree (Ağaç):** Bir klasörün içeriğini temsil eder. Diğer `tree` objelerine (alt klasörler) ve `blob` objelerine (dosyalar) işaret eden bir liste içerir. Her girdi dosya/klasör modunu (izinler), tipini (blob/tree), SHA-1 hash'ini ve dosya/klasör adını içerir. Bir projenin belirli bir andaki anlık görüntüsünü (snapshot) oluşturur. Tree objesinin hash'i de kendi içeriğine göre hesaplanır.
    ```bash
    # Mevcut hazırlık alanının (index) tree objesini oluştur ve hash'ini göster
    git write-tree
    # Örnek Çıktı: d8329fc1cc938780ffdd9f9410d34488208cbb05

    # Bir tree objesinin içeriğini listele
    git cat-file -p d8329fc1cc
    # Örnek Çıktı:
    # 100644 blob a906cb2a4a904a152e80877d4088654daad0c859      README.md
    # 040000 tree 1a2b3c4d5e6f7890...                         src
    ```
3.  **Commit:** Proje geçmişindeki bir noktayı temsil eder. Şunları içerir:
    *   Bu commit'in anlık görüntüsünü temsil eden **kök tree objesinin SHA-1 hash'i**.
    *   Varsa, **bir önceki commit(ler)in (parent) SHA-1 hash(ler)i**. (Merge commit'lerinin birden fazla parent'ı vardır).
    *   **Yazar (Author):** Kodu ilk yazan kişi ve zamanı.
    *   **Commit Yapan (Committer):** Commit'i oluşturan kişi ve zamanı (Author ve Committer farklı olabilir, örn: rebase veya başkasının patch'ini uygularken).
    *   **Commit Mesajı**.
    Commit objesinin hash'i de tüm bu bilgilerin içeriğine göre hesaplanır. `git log` komutu aslında bu commit objelerini takip ederek geçmişi gösterir.
    ```bash
    # Son commit objesinin içeriğini göster
    git cat-file -p HEAD
    # Örnek Çıktı:
    # tree d8329fc1cc938780ffdd9f9410d34488208cbb05
    # parent a1b2c3d4e5f6...
    # author Cihan Atas <atascihan115@gmail.com> 1678886400 +0300
    # committer Cihan Atas <atascihan115@gmail.com> 1678886400 +0300
    #
    # feat: İlk commit
    ```
4.  **Tag (Etiket - Annotated):** (Bölüm 10.2'de bahsedildi) Açıklamalı etiketler de kendi objelerine sahiptir. Belirli bir commit'e işaret eder ve etiketleyen, tarih, mesaj ve GPG imzası gibi ek bilgiler içerir.

Bu obje yapısı sayesinde Git:

*   **Verimli Depolama:** Aynı dosya içeriği (blob) sadece bir kez saklanır.
*   **Veri Bütünlüğü:** Her objenin hash'i içeriğine bağlıdır. İçerik değişirse hash de değişir. Bu, geçmişin değiştirilemez (immutable) olmasını sağlar (rebase gibi işlemler aslında yeni objeler yaratır).
*   **Hız:** Çoğu işlem (commit, branch, merge) yerel objeler üzerinde yapılır ve çok hızlıdır.

### 14.2 `.git` Klasörüne Kısa Bir Bakış

Bir Git deposunu `init` veya `clone` ile oluşturduğunuzda projenizin kök dizininde gizli bir `.git` klasörü oluşur. Bu klasör, Git'in tüm "beynini" içerir:

*   **`objects/`:** Tüm Git objelerinin (blob, tree, commit, tag) saklandığı yerdir. Hash'in ilk iki karakteri klasör adı, geri kalanı dosya adı olacak şekilde organize edilir. Verimlilik için zamanla "packfile" denen sıkıştırılmış dosyalarda birleştirilirler (`pack/` alt klasörü).
*   **`refs/`:** Referansların (işaretçilerin) tutulduğu yerdir.
    *   **`refs/heads/`:** Yerel branch'lerinizin en son commit'lerine işaret eden dosyalar (örn: `refs/heads/main` dosyası, `main` branch'inin son commit hash'ini içerir).
    *   **`refs/tags/`:** Etiketlerinizin işaret ettiği commit'lere ait referanslar.
    *   **`refs/remotes/`:** Uzak izleme dallarının (`origin/main` gibi) referansları.
*   **`HEAD`:** Şu anda üzerinde bulunduğunuz (aktif olan) branch'e veya commit'e işaret eden sembolik bir referanstır. Genellikle `ref: refs/heads/main` gibi bir içerik taşır (yani `main` branch'ine işaret eder). Detached HEAD durumunda ise doğrudan bir commit hash'i içerir.
*   **`index`:** Hazırlık alanını (Staging Area) temsil eden ikili bir dosyadır. Bir sonraki commit'e dahil edilecek dosyaların anlık görüntüsünü (dosya adı, hash, metadata) tutar. `git add` komutu bu dosyayı günceller.
*   **`config`:** Depoya özgü yapılandırma ayarlarını içerir (uzak depo URL'leri, branch takipleri vb.). Global ayarlar (`~/.gitconfig`) ve sistem ayarları ile birleşir.
*   **`hooks/`:** İstemci taraflı kancaların (hooks) bulunduğu yerdir (Bölüm 10.9).
*   **`logs/`:** `reflog` verilerinin saklandığı yerdir. Özellikle `logs/refs/heads/` ve `logs/HEAD`.
*   **`COMMIT_EDITMSG`:** Son commit mesajının geçici olarak tutulduğu dosya.
*   **`FETCH_HEAD`:** En son `git fetch` ile getirilen uzak referans bilgilerini tutan geçici dosya.
*   **`MERGE_HEAD`, `CHERRY_PICK_HEAD`, `REVERT_HEAD`:** Merge, cherry-pick veya revert işlemi sırasında diğer branch'in/commit'in referansını tutan dosyalar.

Bu klasörün içeriğini manuel olarak düzenlemek genellikle önerilmez (config hariç), ancak yapısını anlamak Git'in çalışma mantığını kavramanıza yardımcı olur.

---

## 15. Ek Kaynaklar ve Sonraki Adımlar

Bu rehber, Git ve GitHub'ın temellerini ve sık kullanılan ileri düzey konularını kapsamayı amaçlamıştır. Ancak Git çok derin ve geniş bir araçtır. Öğrenmeye devam etmek için aşağıdaki kaynaklardan faydalanabilirsiniz:

*   **Resmi Git Dokümantasyonu:** [https://git-scm.com/doc](https://git-scm.com/doc) - En kapsamlı ve doğru kaynaktır. Özellikle [Pro Git kitabı](https://git-scm.com/book/tr/v2) (Türkçe çevirisi de mevcut) harika bir başlangıç noktasıdır.
*   **GitHub Dokümantasyonu:** [https://docs.github.com/](https://docs.github.com/) - GitHub'a özgü özellikler (Actions, Packages, Pages, PR süreçleri vb.) hakkında detaylı bilgi.
*   **GitLab Dokümantasyonu:** [https://docs.gitlab.com/](https://docs.gitlab.com/) - GitLab'a özgü özellikler için.
*   **Atlassian Git Tutorials:** [https://www.atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials) - Kavramları ve iş akışlarını açıklayan iyi yazılmış rehberler (Bitbucket'in geliştiricisi).
*   **Learn Git Branching:** [https://learngitbranching.js.org/](https://learngitbranching.js.org/) - Dallanma, rebase, cherry-pick gibi konuları interaktif olarak görselleştiren harika bir site.
*   **Conventional Commits:** [https://www.conventionalcommits.org/](https://www.conventionalcommits.org/) - Anlamlı commit mesajları yazma standardı.
*   **Oh Shit, Git!?!:** [https://ohshitgit.com/](https://ohshitgit.com/) - Git'te işler ters gittiğinde ne yapacağınıza dair pratik çözümler sunan eğlenceli bir kaynak.

**Sonraki Adımlar:**

*   **Pratik Yapın:** Öğrendiklerinizi kendi projelerinizde veya deneme depolarında bol bol uygulayın. Farklı komutları deneyin, hata yapmaktan çekinmeyin.
*   **Takımınızın İş Akışını Öğrenin:** Eğer bir takımda çalışıyorsanız, takımınızın benimsediği Git iş akışını, branch isimlendirme kurallarını ve PR/MR süreçlerini öğrenin ve uygulayın.
*   **Katkıda Bulunun:** Açık kaynak projelere katkıda bulunarak Forking Workflow gibi süreçleri deneyimleyin ve farklı geliştiricilerle etkileşim kurun.
*   **Git GUI Araçlarını Keşfedin:** Komut satırı güçlü olsa da, bazen görsel araçlar (SourceTree, GitKraken, VS Code Git entegrasyonu, GitHub Desktop vb.) geçmişi görselleştirmek veya çakışmaları çözmek için yardımcı olabilir. Ancak temel komutları bilmek her zaman önemlidir.
*   **Sürekli Öğrenin:** Git sürekli gelişen bir araçtır. Yeni özellikleri ve en iyi pratikleri takip etmeye çalışın.

Umarım bu rehber Git ve GitHub yolculuğunuzda size faydalı olur! Başarılar!
```

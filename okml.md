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

4.2 Temel Yapılandırma (Zorunlu)

Git, yaptığınız her commit'e kimlik (ad ve e-posta) bilgilerinizi ekler. Bu, değişikliklerin kim tarafından yapıldığını takip etmek için kritiktir. Bu ayarları yapmadan commit atamazsınız veya atmamalısınız.

# Global ayar: Bu bilgisayardaki tüm Git depolarınız için geçerli olur
git config --global user.name "Adınız Soyadınız"
git config --global user.email "eposta@adresiniz.com"
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Ayarlarınızı kontrol etmek için:

# Tüm ayarları gösterir (yerel, global, sistem)
git config --list          
# Sadece global ayarları gösterir
git config --global --list
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
4.3 Metin Editörü Ayarları

Git, commit mesajı yazmak veya merge çakışmalarını çözmek gibi durumlarda bir metin editörüne ihtiyaç duyar. Varsayılan editörü değiştirebilirsiniz:

# VS Code için (komut satırından 'code' ile başlatılabiliyorsa ve kapanana kadar beklemesi için --wait)
git config --global core.editor "code --wait"

# Nano için
git config --global core.editor "nano"

# Vim için (genellikle varsayılan)
git config --global core.editor "vim"

# Sublime Text için (örnek - yolunuza göre değişebilir)
# git config --global core.editor "'C:/Program Files/Sublime Text 3/subl.exe' -w"
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
4.4 SSH Anahtarı Oluşturma ve Platformlara Ekleme

GitHub, GitLab, Bitbucket gibi platformlarla HTTPS yerine SSH üzerinden (daha güvenli ve pratik) iletişim kurmak için SSH anahtar çifti kullanılır.

Anahtar Oluşturma:

# Ed25519 (Modern ve önerilen)
ssh-keygen -t ed25519 -C "eposta@adresiniz.com"

# RSA (Eski ama hala yaygın)
# ssh-keygen -t rsa -b 4096 -C "eposta@adresiniz.com"
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Komut size anahtarın kaydedileceği yeri (genellikle ~/.ssh/id_ed25519 veya ~/.ssh/id_rsa) ve bir parola (passphrase - önerilir!) soracaktır. Enter'a basarak varsayılan konumu kabul edebilirsiniz. Parola, özel anahtarınızı ek koruma altına alır.

SSH Agent'a Ekleme (Oturum boyunca parolayı tekrar sormaması için):

# Agent'ı başlat (farklı shell'lerde farklı olabilir)
eval "$(ssh-agent -s)"
# Anahtarı agent'a ekle (dosya adını doğru yazdığınızdan emin olun)
ssh-add ~/.ssh/id_ed25519 # Eğer farklı bir isim veya RSA kullandıysanız onu yazın
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Eğer anahtarı parola ile oluşturduysanız, burada parolayı girmeniz istenecektir.

Public Key'i Kopyalama:
Public anahtar (.pub uzantılı dosya), platformlara ekleyeceğiniz anahtardır. Private anahtarı (.pub olmayan) ASLA paylaşmayın!

# macOS:
pbcopy < ~/.ssh/id_ed25519.pub

# Linux (xclip kuruluysa):
xclip -selection clipboard < ~/.ssh/id_ed25519.pub

# Windows (Git Bash):
cat ~/.ssh/id_ed25519.pub | clip

# Manuel: Dosyayı bir metin editörüyle açıp içeriğini kopyalayın
# cat ~/.ssh/id_ed25519.pub
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Platforma Ekleme:

GitHub: Settings -> SSH and GPG keys -> New SSH key

GitLab: User Settings (sağ üst profil ikonu) -> Preferences -> SSH Keys

Bitbucket: Personal settings (sol alt avatar) -> SSH keys
Kopyaladığınız public anahtarın tamamını (ssh-ed25519 AAAAC3... eposta@adresiniz.com gibi) ilgili alana yapıştırın ve bir isim verin (örn: "İş Laptopu", "Ev Bilgisayarı").

5. Git’in Temel Taşları: Depo ve Temel Komutlar
5.1 Depo (Repository) Kavramı

Bir Git deposu (repository veya kısaca "repo"), projenizin tüm dosyalarını, bu dosyaların geçmişini (commit'ler), dallarını (branch) ve diğer tüm Git meta verilerini içeren bir klasördür. Bu bilgilerin çoğu projenizin kök dizinindeki gizli .git klasöründe saklanır.

5.2 Yeni Depo Başlatma ve Klonlama (init, clone)

Yeni Bir Proje İçin Git'i Başlatma (init):
Mevcut bir proje klasörünü Git deposuna dönüştürmek için:

cd /path/to/your/project
git init
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Bu komut, bulunduğunuz dizinde .git adında gizli bir alt klasör oluşturur ve projenizi Git kontrolüne alır.

Mevcut Bir Depoyu Klonlama (clone):
Uzak bir sunucudaki (örn: GitHub) bir depoyu kendi bilgisayarınıza kopyalamak için:

# SSH URL'si (önerilen, SSH ayarı yapıldıysa):
git clone git@github.com:kullaniciadi/depoadi.git

# HTTPS URL'si:
git clone https://github.com/kullaniciadi/depoadi.git

# Belirli bir klasör adı altında klonlamak için:
git clone <url> <yeni_klasor_adi>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Bu komut, depoadi (veya belirttiğiniz yeni_klasor_adi) adında bir klasör oluşturur, içine .git klasörünü ve projenin varsayılan branch'inin en son halini indirir. Ayrıca origin adında bir remote (uzak depo) bağlantısını otomatik olarak kurar.

5.3 Değişiklikleri İzleme (The Three States & status)

Git'te dosyalarınız temel olarak üç ana durumda bulunur:

Working Directory (Çalışma Dizini): Proje dosyalarınızın diskteki hali. Burada değişiklik yapar, dosya ekler veya silersiniz.

Staging Area (Hazırlık Alanı / Index): Bir sonraki commit'e dahil etmek istediğiniz değişikliklerin "hazırlandığı" bir ara alandır. git add ile dosyaları buraya eklersiniz. Bu, commit'e sadece istediğiniz değişiklikleri dahil etmenizi sağlar.

Repository (.git directory): Commit'lediğiniz (yani kalıcı olarak kaydettiğiniz) proje anlık görüntülerinin (snapshot) ve tüm geçmişin saklandığı yerdir. git commit ile hazırlık alanındaki değişiklikler buraya kaydedilir.

Dosyaların bu üç alandaki durumunu görmek için en sık kullanacağınız komut:

git status
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

git status çıktısı size şunları söyler:

Hangi branch'te olduğunuzu.

Yerel branch'inizin uzak branch'e göre durumunu (ileride mi, geride mi, güncel mi).

Changes to be committed: Hazırlık alanındaki (staging) dosyalar.

Changes not staged for commit: Çalışma dizininde değiştirilmiş ama hazırlık alanına eklenmemiş dosyalar.

Untracked files: Git tarafından henüz hiç izlenmeyen yeni dosyalar.

5.4 Değişiklikleri Hazırlık Alanına Ekleme (Staging & add)

Çalışma dizinindeki değişiklikleri bir sonraki commit'e hazırlamak için git add kullanılır:

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
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
5.5 Commit Oluşturma (Değişiklikleri Kaydetme & commit)

Hazırlık alanındaki değişiklikleri (snapshot) projenin geçmişine kalıcı olarak kaydetmek için git commit kullanılır. Her commit, projenin o anki durumunun bir kaydıdır, bir SHA-1 kimliği (hash), yazar bilgisi, tarih ve bir mesaj içerir.

# Kısa ve açıklayıcı bir mesajla commit oluşturma (en yaygın kullanım)
git commit -m "feat: Kullanıcı profili sayfasını ekle"

# `-m` kullanmazsanız, Git'in ayarladığı metin editörü açılır.
# İlk satıra kısa başlık (max 50 karakter), bir boş satır, sonra detaylı açıklama yazılır.
git commit
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
5.6 İyi Commit Mesajları Yazma

Commit mesajları, projenin geçmişini anlamak, hata ayıklamak ve takım iletişimini sağlamak için hayati öneme sahiptir.

Anlamlı Başlık: İlk satır (konu satırı) kısa (genellikle <50 karakter) olmalı, emir kipinde yazılmalı ("Ekle", "Düzelt", "Güncelle" gibi) ve değişikliğin ne yaptığını açıkça özetlemelidir.

Detaylı Açıklama (Gerekiyorsa): Başlıktan sonra bir boş satır bırakılmalı. Ardından, değişikliğin neden yapıldığını, hangi sorunu çözdüğünü veya önemli bağlamları açıklayan daha uzun bir metin yazılabilir. Satırları okunabilirlik için ~72 karaktere sığdırmaya çalışın.

Conventional Commits Standardı: Takım içinde tutarlılık sağlamak ve otomatik sürüm notu oluşturma gibi araçları kullanmak için popüler bir standarttır. Mesajlar şu formatta yazılır: tip(kapsam): açıklama

Tipler: feat (yeni özellik), fix (hata düzeltme), docs (dokümantasyon), style (formatlama), refactor (kod iyileştirme), perf (performans), test (test ekleme/düzeltme), build (yapı sistemi), ci (sürekli entegrasyon), chore (diğer bakım işleri).

Kapsam (Opsiyonel): Değişikliğin etki ettiği alan (örn: auth, ui, api).

Açıklama: Başlık kısmındaki gibi emir kipinde kısa açıklama.

Örnekler:

feat(auth): Google ile giriş yapma özelliği eklendi

fix: Kullanıcı silindiğinde ilişkili verilerin temizlenmemesi sorunu düzeltildi

docs(readme): Kurulum adımları güncellendi

refactor(api): Servis katmanındaki kod tekrarları azaltıldı

chore: Bağımlılıklar son sürümlere güncellendi

Breaking Change: Eğer değişiklik geriye dönük uyumluluğu bozuyorsa, açıklamanın sonuna BREAKING CHANGE: ile başlayan bir not eklenir veya tipin sonuna ! konur (örn: feat!: ...).

5.7 Değişiklikleri Görüntüleme (Farklar & diff)

Yapılan veya yapılacak olan değişiklikleri satır satır görmek için git diff kullanılır:

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
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
6. Zaman Makinesi: Geçmişi Yönetme ve Geri Alma

Git'in en güçlü yanlarından biri, proje geçmişini yönetme ve hataları geri alma yeteneğidir.

6.1 Commit Geçmişini Görüntüleme (git log)

Projenin commit geçmişini görmek için git log kullanılır. Birçok kullanışlı seçeneği vardır:

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
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=short
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
6.2 Belirli Bir Commit'i İnceleme (git show)

Tek bir commit'in tüm detaylarını (yazar, tarih, tam mesaj ve yaptığı tüm değişiklikler) görmek için:

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
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
6.3 Geri Alma İşlemleri

Hatalar olur! Git, hataları düzeltmek veya değişiklikleri geri almak için çeşitli mekanizmalar sunar:

6.3.1 Son Commit'i Düzenleme (--amend)

Son commit'e dosya eklemeyi unuttuysanız, bir hatayı düzelttiyseniz veya sadece commit mesajını değiştirmek istiyorsanız, yeni bir commit oluşturmak yerine son commit'i düzenleyebilirsiniz.

ÖNEMLİ UYARI: Bu işlem son commit'in hash'ini değiştirir, yani geçmişi yeniden yazar. Sadece henüz uzak depoya göndermediğiniz (push etmediğiniz) commit'ler için kullanın. Başkalarıyla paylaşılan bir branch'teki commit'i amend ederseniz, ciddi sorunlara yol açabilirsiniz (onların geçmişiyle sizinki uyumsuz hale gelir).

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
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
6.3.2 Hazırlık Alanından Dosya Çıkarma (reset HEAD/restore --staged)

git add ile yanlışlıkla hazırlık alanına (staging area) eklediğiniz bir değişikliği veya dosyayı commit'lemeden önce geri almak için:

# Yeni ve önerilen yöntem:
git restore --staged <dosya_adi>

# Tüm hazırlık alanını temizle (tüm eklenenleri geri al)
git restore --staged .

# Eski yöntem (hala çalışır):
# git reset HEAD <dosya_adi>
# git reset HEAD .
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Bu komutlar çalışma dizininizdeki (working directory) değişikliklere dokunmaz, sadece hazırlık alanını (staging area) temizler veya belirtilen dosyayı çıkarır.

6.3.3 Çalışma Dizinindeki Değişiklikleri Geri Alma (checkout --/restore)

Çalışma dizininde (working directory) yaptığınız ama henüz commit'lemediğiniz (hatta belki add bile yapmadığınız) değişiklikleri iptal etmek ve dosyanın son commit'teki haline dönmesini sağlamak için:

UYARI: Bu işlem, çalışma dizinindeki o dosyaya ait kaydedilmemiş tüm değişiklikleri kalıcı olarak siler. Geri alınamaz. Çok dikkatli olun!

# Yeni ve önerilen yöntem:
git restore <dosya_adi>

# Çalışma dizinindeki TÜM değişiklikleri geri al (çok tehlikeli!)
# git restore .

# Eski yöntem (daha kafa karıştırıcı olabilir):
# git checkout -- <dosya_adi>
# git checkout -- . # Çok tehlikeli!
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
6.3.4 Bir Commit'in Değişikliklerini Geri Alan Yeni Commit Oluşturma (revert)

Geçmişteki belirli bir commit'in yaptığı değişiklikleri tersine çeviren yeni bir commit oluşturur. Proje geçmişini değiştirmez (yani eski commit'i silmez), sadece o commit'in etkilerini ortadan kaldıran zıt bir değişiklik ekler.

Bu yöntem, uzak depoya gönderilmiş (push edilmiş) veya başkalarıyla paylaşılan branch'lerdeki hataları düzeltmek için en güvenli yoldur, çünkü mevcut geçmişi bozmaz.

# Geri alınacak commit'in hash'ini bulun (git log ile)
git log --oneline

# Belirtilen commit'in değişikliklerini geri alan yeni bir commit oluştur
git revert <geri_alinacak_commit_hash>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Bu komut, genellikle bir commit mesajı girmeniz için metin editörünü açar (varsayılan mesaj genellikle "Revert '[orijinal commit başlığı]'" şeklindedir). Mesajı onaylayıp kaydettiğinizde yeni revert commit'i oluşturulur.

Eğer revert işlemi çakışmaya (conflict) neden olursa, çakışmayı çözüp git add <dosya> ve ardından git revert --continue yapmanız gerekir. İptal etmek için git revert --abort.

6.3.5 Geçmişteki Bir Duruma Dönme (reset)

git reset, branch'inizin işaret ettiği commit'i (HEAD) ve isteğe bağlı olarak hazırlık alanını ve çalışma dizinini belirli bir geçmiş commit'e "sıfırlamanızı" sağlar. Bu, geçmişi yeniden yazan güçlü ve potansiyel olarak tehlikeli bir komuttur.

ÖNEMLİ UYARI: git reset'i (özellikle --hard ile) sadece yerel, paylaşılmamış commit'ler üzerinde kullanın. Uzak depoya gönderilmiş commit'leri reset'lemek, takım arkadaşlarınızın depolarıyla ciddi uyumsuzluklara yol açar.

git reset'in üç ana modu vardır:

--soft: Sadece HEAD işaretçisini belirtilen commit'e taşır. Hazırlık alanı (staging area) ve çalışma dizini (working directory) dokunulmaz. Yani, reset'lenen commit'lerden sonraki tüm değişiklikler hala hazırlık alanında (staged) durur, sanki git add yapmışsınız gibi. Son birkaç commit'i birleştirmek (squash) için kullanılabilir (ama rebase -i genellikle daha pratiktir).

# Son commit'i geri al, değişiklikler hazırlık alanında kalsın
git reset --soft HEAD~1
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

--mixed (Varsayılan mod): HEAD işaretçisini ve hazırlık alanını (staging area) belirtilen commit'e sıfırlar. Çalışma dizinine (working directory) dokunmaz. Yani, reset'lenen commit'lerden sonraki tüm değişiklikler çalışma dizininde "unstaged" olarak kalır. Yanlışlıkla yapılan commit'leri geri alıp değişiklikleri yeniden düzenlemek için kullanışlıdır.

# Son commit'i geri al, değişiklikler çalışma dizininde unstaged olarak kalsın
git reset --mixed HEAD~1 
# veya sadece:
git reset HEAD~1
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

--hard: HEAD işaretçisini, hazırlık alanını VE çalışma dizinini belirtilen commit'in durumuna sıfırlar. Yani, reset'lenen commit'lerden sonra yapılan tüm değişiklikler (hem staged hem unstaged) kalıcı olarak silinir. Çok dikkatli kullanılmalıdır! Yanlışlıkla yapılan ve tamamen kurtulmak istediğiniz commit'ler için kullanılır.

# Son commit'i ve onun getirdiği tüm değişiklikleri (staged/unstaged) kalıcı olarak sil
git reset --hard HEAD~1 

# Belirli bir commit hash'ine DİKKATLİCE dön (o commit'ten sonraki her şeyi siler)
git reset --hard <commit_hash>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

reset sonrası kayıp commit'leri kurtarma: Eğer yanlışlıkla reset --hard yaparsanız, git reflog komutu (Bölüm 10.5) genellikle silinen commit'lere geri dönmenizi sağlayabilir.

7. Paralel Evrenler: Dallanma ve Birleştirme

Dallanma (Branching), Git'in en önemli özelliklerinden biridir. Ana kod tabanını (genellikle main veya master) bozmadan yeni özellikler geliştirmek, hataları düzeltmek veya farklı fikirleri denemek için paralel çalışma alanları oluşturmanızı sağlar.

7.1 Branch (Dal) Nedir?

Bir branch, aslında belirli bir commit'e işaret eden hareketli bir etikettir. Varsayılan olarak, ilk commit yapıldığında main (veya eski sistemlerde master) adında bir branch oluşur. Yeni bir branch oluşturduğunuzda, aslında sadece mevcut commit'e işaret eden yeni bir etiket yaratmış olursunuz. Siz o branch'te yeni commit'ler yaptıkça, sadece o branch etiketi ileri doğru hareket eder, diğer branch'ler yerinde kalır. Bu sayede farklı geliştirme hatları birbirinden bağımsız ilerleyebilir.

7.2 Branch Oluşturma, Geçiş Yapma ve Listeleme (branch, checkout)

Yeni Branch Oluşturma:

# Mevcut bulunduğunuz commit'ten yeni bir branch oluşturur, ama o branch'e geçmez
git branch <yeni_branch_adi>
# Örnek:
git branch feature/kullanici-kayit
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Branch'ler Arası Geçiş Yapma:
Farklı bir branch'e geçmek (çalışma dizininizi o branch'in son commit'indeki hale getirmek) için checkout kullanılır:

git checkout <gecis_yapilacak_branch_adi>
# Örnek:
git checkout feature/kullanici-kayit
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Not: Geçiş yapmadan önce mevcut branch'teki değişikliklerinizi commit'lemeniz veya stash'lemeniz (Bölüm 10.1) genellikle iyi bir fikirdir, aksi takdirde Git çakışma uyarısı verebilir veya değişiklikler kaybolabilir.

Branch Oluşturma ve Aynı Anda Geçiş Yapma (Yaygın Kullanım):
Bu iki adımı tek komutta birleştirmek için:

git checkout -b <yeni_branch_adi>
# Örnek:
git checkout -b hotfix/login-bug
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Bu komut, git branch hotfix/login-bug ve ardından git checkout hotfix/login-bug yapmanın kısayoludur.

Branch'leri Listeleme:

# Sadece yerel (local) branch'leri listeler. Aktif olan branch '*' ile işaretlenir.
git branch

# Yerel branch'leri son commit bilgisiyle birlikte listeler
git branch -v

# Hem yerel hem de uzak izleme (remote-tracking) branch'lerini listeler
git branch -a 

# Belirli bir desene uyan branch'leri listele
git branch --list 'feature/*'
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Branch Yeniden Adlandırma:

# Mevcut branch'i yeniden adlandır
git branch -m <yeni_ad>

# Başka bir branch'i yeniden adlandır
git branch -m <eski_ad> <yeni_ad>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Branch Silme:
UYARI: Silinecek branch'teki commit'ler başka hiçbir branch tarafından referans alınmıyorsa ve henüz birleştirilmediyse, bu commit'lere erişimi kaybedebilirsiniz (reflog ile kurtarma şansı olsa da).

# Birleştirilmiş (merged) bir branch'i sil (güvenli)
git branch -d <silinecek_branch_adi>
# Örnek:
git branch -d feature/kullanici-kayit

# Birleştirilmemiş bir branch'i silmeye zorla (DİKKATLİ OLUN!)
git branch -D <silinecek_branch_adi>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
7.3 Branch Birleştirme (merge)

Farklı bir branch'te tamamladığınız işleri (commit'leri) ana branch'inize (veya başka bir branch'e) entegre etmek için git merge kullanılır.

Tipik Akış:

Hedef branch'e geçin (genellikle main veya develop).

Hedef branch'in güncel olduğundan emin olun (git pull veya fetch+merge).

Birleştirmek istediğiniz branch'i merge komutu ile çağırın.

# 1. Ana branch'e geç
git checkout main

# 2. Ana branch'i güncelle (uzak depodan son değişiklikleri al)
git pull origin main 

# 3. Özellik branch'ini main'e birleştir
git merge feature/kullanici-kayit
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Merge Türleri:

Fast-Forward Merge: Eğer hedef branch (main), birleştirilecek branch (feature) oluşturulduktan sonra hiç yeni commit almamışsa, Git sadece hedef branch'in etiketini birleştirilecek branch'in son commit'ine taşır. Geçmiş lineer (düz) kalır, yeni bir "merge commit" oluşmaz. Bu, en basit birleştirme türüdür.

Three-Way Merge (Recursive Merge): Eğer her iki branch de (hedef ve kaynak) kendi yollarında ilerlemişse (yani ortak atadan sonra ikisinde de yeni commit'ler varsa), Git iki branch'in son commit'lerini ve onların en yakın ortak atasını (common ancestor) kullanarak birleştirme yapar. Bu işlem sonucunda, iki farklı geçmişi birleştirdiğini gösteren yeni bir "merge commit" oluşur. Bu commit'in iki ebeveyni (parent) olur.

7.4 Merge Çakışmalarını (Conflict) Çözme

Eğer iki branch'te de aynı dosyanın aynı satırları farklı şekillerde değiştirilmişse, Git bu değişikliği otomatik olarak birleştiremez ve bir "merge conflict" (birleştirme çakışması) oluşur.

Çakışmayı Fark Etme: git merge komutu başarısız olur ve hangi dosyalarda çakışma olduğunu listeler. git status komutu da çakışan dosyaları "Unmerged paths" altında gösterir.

Çakışan Dosyaları Açma: Çakışan dosyaları bir metin editöründe açtığınızda, Git'in çakışan bölümleri işaretlediğini görürsünüz:

<<<<<<< HEAD
// Hedef branch'teki (örn: main) kodlarınız
System.out.println("Merhaba Dünya!");
=======
// Birleştirilen branch'teki (örn: feature) kodlar
System.out.println("Hello World!");
>>>>>>> feature/kullanici-kayit
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Diff
IGNORE_WHEN_COPYING_END

Çakışmayı Çözme:

Bu işaretleri (<<<<<<<, =======, >>>>>>>) ve istemediğiniz kodları silin.

Her iki değişikliği de tutmak istiyorsanız, kodları uygun şekilde birleştirin.

Sonuç olarak dosyanın olması gereken doğru haline getirin.

Çözülen Dosyayı Hazırlık Alanına Ekleme:
Çakışmayı çözdükten sonra, dosyayı normal bir değişiklik gibi hazırlık alanına ekleyin:

git add <cakisma_cozulen_dosya.java>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Merge İşlemini Tamamlama:
Tüm çakışmaları çözüp ilgili dosyaları add ile ekledikten sonra, merge işlemini tamamlamak için bir commit oluşturun:

git commit
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Git genellikle sizin için varsayılan bir merge commit mesajı hazırlar ("Merge branch '...' into ..."). Bu mesajı kullanabilir veya düzenleyebilirsiniz.

Merge İşlemini İptal Etme: Eğer çakışma çözümüyle başa çıkamayacağınıza karar verirseniz, merge işlemini başlatmadan önceki duruma dönebilirsiniz:

git merge --abort
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
7.5 Geçmişi Yeniden Yazma (rebase)

git rebase, bir branch'teki commit'leri alıp başka bir branch'in üzerine yeniden uygulamak için kullanılan güçlü bir araçtır. Merge gibi iki branch'i birleştirmenin alternatif bir yoludur, ancak geçmişi yeniden yazar.

Temel Kullanım (Feature Branch'i Güncelleme):

Diyelim ki main branch'inden feature/yeni-ozellik adında bir branch oluşturdunuz. Siz feature üzerinde çalışırken, main branch'ine başka commit'ler eklendi. feature branch'inizi main'deki son değişikliklerle güncellemek ve geçmişinizi daha lineer (düz) tutmak için rebase kullanabilirsiniz:

# 1. Feature branch'inde olduğunuzdan emin olun
git checkout feature/yeni-ozellik

# 2. Main branch'indeki son değişiklikleri çekin (uzak depo varsa)
# Bu adım, yerel 'main' branch'inizi güncel tutmak içindir, rebase doğrudan 'origin/main' üzerine de yapılabilir.
git fetch origin 
git checkout main
git pull origin main
git checkout feature/yeni-ozellik

# 3. Feature branch'ini main'in üzerine rebase et
git rebase main 
# veya doğrudan uzak branch üzerine:
# git rebase origin/main
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

rebase Nasıl Çalışır?

feature/yeni-ozellik branch'i ile main branch'inin ortak atasından sonraki feature branch'indeki commit'leri bulur.

feature branch'ini geçici olarak main'in son commit'ine taşır.

Bulunan commit'leri tek tek main'in son commit'i üzerine sırayla uygulamaya çalışır.

Sonuç olarak, feature branch'iniz sanki main'in en son halinden yeni oluşturulmuş gibi görünür ve commit geçmişi daha temiz, lineer bir hal alır. Merge commit'i oluşmaz.

Rebase Çakışmalarını Çözme:

rebase sırasında da çakışmalar olabilir (her commit tek tek uygulandığı için birden fazla çakışma çözmeniz gerekebilir).

rebase durur ve çakışan dosyayı belirtir.

Çakışmayı normal merge çakışması gibi çözün (işaretleri temizleyin, doğru kodu bırakın).

Çözdüğünüz dosyayı hazırlık alanına ekleyin: git add <cakisan_dosya>

Rebase işlemine devam etmesini söyleyin: git rebase --continue

Eğer başka commit'lerde de çakışma varsa, 2-4 adımlarını tekrarlayın.

Rebase İşlemini İptal Etme:

git rebase --abort
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Rebase Uyarısı:
rebase, commit'lerin hash'lerini değiştirdiği için geçmişi yeniden yazar. Bu nedenle, merge'ün aksine, asla başkalarıyla paylaştığınız (uzak depoya push ettiğiniz) bir branch'i rebase etmeyin! Eğer bunu yaparsanız ve --force ile push ederseniz, takım arkadaşlarınızın geçmişiyle sizinki uyumsuz hale gelir ve büyük sorunlar çıkar. Kendi yerel, henüz paylaşmadığınız feature branch'lerinizi temiz tutmak için rebase harikadır.

7.6 Merge vs. Rebase: Ne Zaman Hangisini Kullanmalı?

Bu, Git dünyasındaki yaygın tartışma konularından biridir ve kesin bir doğru cevabı yoktur, takım veya proje tercihlerine bağlıdır.

Merge:

Avantajları: Geçmişi olduğu gibi korur. Hangi branch'in ne zaman birleştirildiği "merge commit"i sayesinde açıkça bellidir. Daha basittir ve geçmişi değiştirmediği için paylaşılan branch'lerde daha güvenlidir.

Dezavantajları: Özellikle çok sayıda branch ve sık birleştirme olan projelerde commit geçmişi çok dallı, budaklı ve takip etmesi zor hale gelebilir (git log --graph çıktısı karmaşıklaşır).

Kullanım Senaryosu: Paylaşılan branch'leri (örn: develop'u main'e, release branch'lerini main'e) birleştirirken, bir özelliğin tam olarak ne zaman ve hangi noktada ana hatta dahil edildiğini kaydetmek istediğinizde tercih edilir.

Rebase:

Avantajları: Daha temiz, lineer bir proje geçmişi oluşturur. Sanki tüm işler sıralı bir şekilde yapılmış gibi görünür. Commit'leri birleştirme/düzenleme (rebase -i) için güçlü araçlar sunar.

Dezavantajları: Geçmişi yeniden yazar (commit hash'leri değişir). Paylaşılan branch'lerde kullanılırsa çok tehlikeli olabilir. Çakışma çözümü, merge'e göre daha sık ve commit başına yapıldığı için bazen daha zahmetli olabilir. Birleştirme noktası bilgisi kaybolur (merge commit'i olmaz).

Kullanım Senaryosu: Kendi yerel feature branch'inizi ana branch (main veya develop) ile senkronize etmek ve temiz bir şekilde Pull Request'e hazırlamak için kullanılır. Pull Request'i birleştirmeden önce commit'leri düzenlemek/birleştirmek (rebase -i) için idealdir.

Genel Tavsiye: Kendi yerel feature branch'lerinizde rebase kullanarak ana daldaki güncellemeleri alın ve geçmişinizi temiz tutun. Feature branch'inizi paylaşılan bir ana branch'e (main, develop) entegre ederken ise genellikle merge (veya platformların sunduğu "Squash and Merge" gibi seçenekler) kullanın. Takımınızın belirlediği iş akışına uyun.

8. Takım Çalışması: Uzak Depolarla Etkileşim

Git'in dağıtık yapısı, takım çalışmasını ve kod paylaşımını kolaylaştırır. Bu, "remote" (uzak depo) kavramı üzerinden yapılır.

8.1 Yerel (Local) vs. Uzak (Remote) Depo

Yerel Depo (Local Repository): Sizin bilgisayarınızda bulunan .git klasörünü içeren tam depo kopyasıdır. Çalışma dizininiz, hazırlık alanınız ve tüm proje geçmişi buradadır. Yaptığınız commit, branch, reset gibi işlemler öncelikle burada gerçekleşir.

Uzak Depo (Remote Repository): Genellikle internet üzerinde (GitHub, GitLab, Bitbucket vb.) veya şirket ağı içindeki paylaşılan bir sunucuda barındırılan depo kopyasıdır. Takım üyelerinin kodlarını paylaştığı, senkronize ettiği ve işbirliği yaptığı merkezi bir nokta işlevi görür. Uzak depoda sizin çalışma dizininiz veya hazırlık alanınız bulunmaz; sadece commit geçmişi, branch'ler ve tag'ler bulunur.

8.2 Uzak Depo Yönetimi (remote)

Yerel deponuzun hangi uzak depolarla bağlantılı olduğunu yönetmek için git remote komutu kullanılır.

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
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

git clone ile bir depo kopyaladığınızda, Git otomatik olarak orijinal URL'yi origin adıyla remote olarak ekler.

8.3 Uzak Depodaki Değişiklikleri Çekmeden Görme

Takım arkadaşlarınızın uzak depoya gönderdiği değişiklikleri kendi yerel çalışma kopyanıza entegre etmeden önce nelerin değiştiğini görmek isteyebilirsiniz. Bu, olası çakışmaları öngörmek veya projenin genel ilerleyişini takip etmek için çok faydalıdır.

Adımlar:

Uzak Depodaki Bilgiyi Güncelle (fetch):
Bu komut, belirtilen uzak depodan (genellikle origin) tüm branch ve tag bilgilerini indirir ve yerel deponuzdaki "uzak izleme dallarını" (remote-tracking branches, örn: origin/main) günceller. Sizin aktif yerel branch'lerinize (main, feature/x gibi) dokunmaz.

git fetch origin
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Artık `origin/

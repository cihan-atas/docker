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
    *   [5.2 Yeni Depo Başlatma ve Klonlama](#52-yeni-depo-başlatma-ve-klonlama)
    *   [5.3 Değişiklikleri İzleme (The Three States)](#53-değişiklikleri-izleme-the-three-states)
    *   [5.4 Değişiklikleri Hazırlık Alanına Ekleme (Staging)](#54-değişiklikleri-hazırlık-alanına-ekleme-staging)
    *   [5.5 Commit Oluşturma (Değişiklikleri Kaydetme)](#55-commit-oluşturma-değişiklikleri-kaydetme)
    *   [5.6 İyi Commit Mesajları Yazma](#56-iyi-commit-mesajları-yazma)
    *   [5.7 Değişiklikleri Görüntüleme (Farklar)](#57-değişiklikleri-görüntüleme-farklar)
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
    *   [7.2 Branch Oluşturma, Geçiş Yapma ve Listeleme](#72-branch-oluşturma-geçiş-yapma-ve-listeleme)
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

Kurulumu doğrulamak için terminal veya komut istemcisinde `git --version` komutunu çalıştırın.

```bash
git --version



4.2 Temel Yapılandırma (Zorunlu)

Git, yaptığınız her commit'e kimlik (ad ve e-posta) bilgilerinizi ekler. Bu, değişikliklerin kim tarafından yapıldığını takip etmek için kritiktir. Bu ayarları yapmadan commit atamazsınız veya atmamalısınız.

      
# Global ayar: Bu bilgisayardaki tüm Git depolarınız için geçerli olur
git config --global user.name "Adınız Soyadınız"
git config --global user.email "eposta@adresiniz.com"

    

IGNORE_WHEN_COPYING_START
Use code with caution.Bash
IGNORE_WHEN_COPYING_END

Ayarlarınızı kontrol etmek için:

      
git config --list          # Tüm ayarları gösterir (yerel, global, sistem)
git config --global --list # Sadece global ayarları gösterir

    

IGNORE_WHEN_COPYING_START
Use code with caution.Bash
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
Use code with caution.Bash
IGNORE_WHEN_COPYING_END
4.4 SSH Anahtarı Oluşturma ve Platformlara Ekleme

GitHub, GitLab, Bitbucket gibi platformlarla HTTPS yerine SSH üzerinden (daha güvenli ve pratik) iletişim kurmak için SSH anahtar çifti kullanılır.

    Anahtar Oluşturma:

          
    # Ed25519 (Modern ve önerilen)
    ssh-keygen -t ed25519 -C "eposta@adresiniz.com"

    # RSA (Eski ama hala yaygın)
    # ssh-keygen -t rsa -b 4096 -C "eposta@adresiniz.com"

        

    IGNORE_WHEN_COPYING_START

Use code with caution.Bash
IGNORE_WHEN_COPYING_END

Komut size anahtarın kaydedileceği yeri (genellikle ~/.ssh/id_ed25519 veya ~/.ssh/id_rsa) ve bir parola (passphrase - önerilir!) soracaktır. Enter'a basarak varsayılan konumu kabul edebilirsiniz. Parola, özel anahtarınızı ek koruma altına alır.

SSH Agent'a Ekleme (Oturum boyunca parolayı tekrar sormaması için):

      
# Agent'ı başlat (farklı shell'lerde farklı olabilir)
eval "$(ssh-agent -s)"
# Anahtarı agent'a ekle (dosya adını doğru yazdığınızdan emin olun)
ssh-add ~/.ssh/id_ed25519 # Eğer farklı bir isim veya RSA kullandıysanız onu yazın

    

IGNORE_WHEN_COPYING_START
Use code with caution.Bash
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

    Use code with caution.Bash
    IGNORE_WHEN_COPYING_END

    Platforma Ekleme:

        GitHub: Settings -> SSH and GPG keys -> New SSH key

        GitLab: User Settings (sağ üst profil ikonu) -> Preferences -> SSH Keys

        Bitbucket: Personal settings (sol alt avatar) -> SSH keys
        Kopyaladığınız public anahtarın tamamını (ssh-ed25519 AAAAC3... eposta@adresiniz.com gibi) ilgili alana yapıştırın ve bir isim verin (örn: "İş Laptopu", "Ev Bilgisayarı").

5. Git’in Temel Taşları: Depo ve Temel Komutlar
5.1 Depo (Repository) Kavramı

Bir Git deposu (repository veya kısaca "repo"), projenizin tüm dosyalarını, bu dosyaların geçmişini (commit'ler), dallarını (branch) ve diğer tüm Git meta verilerini içeren bir klasördür. Bu bilgilerin çoğu projenizin kök dizinindeki gizli .git klasöründe saklanır.
5.2 Yeni Depo Başlatma ve Klonlama

    Yeni Bir Proje İçin Git'i Başlatma (init):
    Mevcut bir proje klasörünü Git deposuna dönüştürmek için:

          
    cd /path/to/your/project
    git init

        

    IGNORE_WHEN_COPYING_START

Use code with caution.Bash
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

    Use code with caution.Bash
    IGNORE_WHEN_COPYING_END

    Bu komut, depoadi (veya belirttiğiniz yeni_klasor_adi) adında bir klasör oluşturur, içine .git klasörünü ve projenin varsayılan branch'inin en son halini indirir. Ayrıca origin adında bir remote (uzak depo) bağlantısını otomatik olarak kurar.

5.3 Değişiklikleri İzleme (The Three States)

Git'te dosyalarınız temel olarak üç ana durumda bulunur:

    Working Directory (Çalışma Dizini): Proje dosyalarınızın diskteki hali. Burada değişiklik yapar, dosya ekler veya silersiniz.

    Staging Area (Hazırlık Alanı / Index): Bir sonraki commit'e dahil etmek istediğiniz değişikliklerin "hazırlandığı" bir ara alandır. git add ile dosyaları buraya eklersiniz. Bu, commit'e sadece istediğiniz değişiklikleri dahil etmenizi sağlar.

    Repository (.git directory): Commit'lediğiniz (yani kalıcı olarak kaydettiğiniz) proje anlık görüntülerinin (snapshot) ve tüm geçmişin saklandığı yerdir. git commit ile hazırlık alanındaki değişiklikler buraya kaydedilir.

Dosyaların bu üç alandaki durumunu görmek için en sık kullanacağınız komut:

      
git status

    

IGNORE_WHEN_COPYING_START
Use code with caution.Bash
IGNORE_WHEN_COPYING_END

git status çıktısı size şunları söyler:

    Hangi branch'te olduğunuzu.

    Yerel branch'inizin uzak branch'e göre durumunu (ileride mi, geride mi, güncel mi).

    Changes to be committed: Hazırlık alanındaki (staging) dosyalar.

    Changes not staged for commit: Çalışma dizininde değiştirilmiş ama hazırlık alanına eklenmemiş dosyalar.

    Untracked files: Git tarafından henüz hiç izlenmeyen yeni dosyalar.

5.4 Değişiklikleri Hazırlık Alanına Ekleme (Staging)

Çalışma dizinindeki değişiklikleri bir sonraki commit'e hazırlamak için git add kullanılır:

      

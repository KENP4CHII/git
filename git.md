# Git Temelleri: 

## Git'in çalışma prensiplerini açıklayın.

- Versiyon Kontrolü 
- Dağıtık Sistem 0
- Depo 
- Branch 
- Commit 
- Birleştirme 
- İzleme

## Bir Git deposu nasıl oluşturulur ve yapılandırılır?

Depoyu oluşturmak için bir klasör oluşturun ve ardından bu klasöre terminal veya komut istemcisini kullanarak gittikten sonra 
```bash
git init
```
 komutunu çalıştırarak depo oluşturabilriz.  


## Yerel bir depoda değişikliklerinizi nasıl takip edersiniz ve nasıl taahhüt edersiniz? 

Yaptığınız commitlerin geçmişini gözden geçirebilmek için 

```bash
git log
```

 komutunu çalıştırabilriz.

## Bir uzak depo (remote repository) nasıl eklenir ve senkronize edilir?

- Bir uzak depoyu eklemek için git remote add komutunu kullanabiliriz Genellikle, "origin" adı altında uzak depoyu eklemek yaygın bir uygulamadır. "origin" yerine başka isimde kullanabiliriz.  

- Yerel depodaki değişiklikleri uzak depoya göndermek ve uzak depodaki değişiklikleri yerel depoya çekmek için "git push" ve "git pull" komutlarını kullanabiliriz.

## Git'in farklı dalları (branches) nasıl kullanılır ve yönetilir?

- Branch oluşturma 
  ``` bash
  git branch yeni_dal_adı
  ```
- Dala geçiş yapma 
  ```bash
  git checkout yeni_dal_adı
  ```
- Dallar arasında geçiş yapma 
  ```bash  
  git checkout yeni_dal_adı
  ```
- Dalları listeleme 
  ```bash
  git branch
  ```
- Dalları silme 
  ```bash
  git branch -d yeni_dal_adı
  ```
#	Dal Yönetimi ve Birleştirme: 

## Git dal (branch) kavramını açıklayın ve neden önemli olduğunu tartışın. 

## Bir yeni dal oluşturun, değişiklikler yapın ve ana dala (master/main) nasıl birleştirirsiniz? 

Yeni bir dal oluşturmak için 
```bash
git branch
```
 komutunu kullanacağız. Yeni dal üzerinde istediğiniz değişiklikleri yapalım.
Yaptığınız değişiklikleri stage'e ekleyelim ve bir commit ile kayıt edelim. 
```bash
git commit -m "Yeni dal üzerinde yapılan değişiklikler"
```
 Yeni dal üzerindeki değişiklikleri ana dala birleştirmek için 
 ```bash
 git merge
 ```
  komutunu kullanabiliriz.

## Çakışan (conflicting) değişikliklerle başa çıkmak için Git'in birleştirme (merge) ve çözme (resolve) yeteneklerini gösterin. 

"dal_A" ve "dal_B" adında iki farklı dal oluşturduk ve her birinde aynı dosyayı değiştirdik. 
```bash
git checkout dal_A

git merge dal_B
```
   Bu komutlar "dal_B"'yi "dal_A" ile birleştirir. Ancak dosyada çakışan değişiklikler olduğu için bu işlem çakışmaya neden olacaktır. Çakışma durumunu görmek için bir metin düzenleyici kullanarak "dosya.txt" dosyasını açın. Dosyanın içinde çakışan değişikliklerin belirtileri olacaktır

## Rebase işlemi nedir ve ne zaman kullanılır?

 - Farklı dallarda yapılan değişiklikleri birleştirmek için kullanılan bir işlemdir. 
 - Daha temiz ve düzenli geçmiş oluşturmak
 - Entegrasyon dalını güncelleme
 - Commit geçmişini düzenleme

## Birleştirme (merge) stratejileri hakkında bilgi verin ve nasıl seçileceğini açıklayın.


# İş Akışları ve İş Akışı Yönetimi: 

## Git akış modelleri (GitFlow, GitHub Flow vb.) hakkında bilgi verin ve nasıl uygulanacağını açıklayın. 

## İş akışı (workflow) sırasında tipik bir geliştirme döngüsünü (commit, dal oluşturma, birleştirme) gösterin. 

## Özellik dalları (feature branches) oluşturmak ve yönetmek için Git'in pratiklerini tartışın. 

## Sürüm (release) dallarını nasıl oluşturursunuz ve yönetirsiniz? 

Sürüm dalı oluşturmak için 
```bash
git checkout -b release-1.1
``` 

Sürüm dalında, sürüm için hazırlık yapmak üzere gerekli değişiklikleri yapın. Bu, hata düzeltmeleri, belgelendirme güncellemeleri, sürüm notları hazırlığı gibi işleri içerebilir.

Sürüm hazırlık sürecinin bir parçası olarak, sürüm dalındaki değişiklikleri test edin ve sürümün stabil olduğundan emin olun. Bu, kod incelemeleri, birim testleri ve entegrasyon testleri yapmayı içerebilir.

Sürüm dalı test edildikten ve hazır olduğunda, bu noktaya bir sürüm etiketi oluşturun
```bash
git tag v1.0
```

Sürüm hazır olduğunda ve sürüm paketi oluşturulduğunda, sürüm dalını ana dala birleştirin 
```bash
git checkout main
git merge release-1.1
```

## Bir hata düzeltme (hotfix) iş akışını nasıl uygularsınız?

# İleri Düzey Git Yetenekleri: 

## Git'in yeniden yazım (rebase) ve değiştirme (cherry-pick) yeteneklerini kullanarak nasıl değişiklikler alıp vereceğinizi açıklayın. 

Mevcut dalınızı başka bir dalın son değişikliklerine temel alarak yeniden yapılandırır. Bu, geçmişi daha temiz ve düzenli tutmanın bir yoludur.Bir dalda başka bir dala yapılmış değişiklikler varsa, bu değişiklikleri almak ve kendi değişikliklerimizin üzerine uygulamak için rebase işlemini kullanabiliriz.
```bash
git checkout feature
git rebase main
```
Değiştirme belirli bir commit in değişikliklerini almak için kullanılır. Bu, belirli bir değişikliği alıp başka bir dala veya dalda uygulamanın bir yoludur. Feature daldaki belirli bir commit'i main dala uygulamak için
```bash
git checkout main
git cherry-pick <commit-hash>
```
Bu komutlar, belirli commit'in değişikliklerini main dalına uygular.


## Git içi arama ve sıralama yeteneklerini kullanarak belirli bir değişikliği tespit edin ve geri alın. 

Değişikliği tespit etmek için 
```bash
git log
```
 komutunu kullanarak değişiklik geçmişini gözden geçirebiliriz. Belirli bir değişikliği geri almak için 
 ```bash
 git revert
 ```
  veya 
  ```bash
  git reset
  ```
   komutlarını kullanabiliriz

## Git'in alt yapı (submodule) ve alt depo (subtree) yeteneklerini açıklayın ve nasıl kullanılacağını tartışın. 

Bir alt projenin bağımlılık olarak eklenmesi gerektiğinde.Farklı bir ekip tarafından geliştirilen bir kütüphaneyi kullanmak.
Alt projeyi ana projeye eklemek için 
```bash
git submodule add <repository_url>
``` 
Alt yapıyı güncellemek için 
```bash
git submodule update --remote
```
 Alt projedeki değişiklikleri taahhüt etmek için alt proje dizininde değişiklikleri taahhüt edin ve ardından ana projenin dizininde değişiklikleri taahhüt edin

Projelerinizin belirli bir bölümüne farklı bir projenin kodunu dahil etmek istediğinizde.Bir alt projenin özel bir versiyonunu projenize dahil etmek istediğinizde. Alt depoyu ana projeye eklemek için 
```bash
git subtree add --prefix=<destination_folder> <repository_url> <branch>
```
 Alt depodaki değişiklikleri almak için 
 ```bash
 git subtree pull --prefix=<destination_folder> <repository_url> <branch>
```
## Git'in dosya ve dizinlerdeki değişiklikleri nasıl izleyebileceğini ve inceleyebileceğinizi gösterin. 

Tüm değiştirilmiş dosyaların değişikliklerini görmek için 
```bash
git diff
```
 komutunu kullanabiliriz.
Dosya ve Dizin Değişikliklerini İncelemek için
```bash 
git log
```
 komutunu kullanabiliriz.

## Git'in işaretçileri (tags) ve sürüm etiketleri (release tags) nasıl kullanılır ve yönetilir?

- Bir sürüm etiketi oluşturmak için 
  ```bash
  git tag 
  ```
  komutunu kullanabiliriz.

# Belirli Bir Taahhüd Üzerine Etiket Oluşturma:
- Belirli bir taahhüd üzerine bir sürüm etiketi oluşturmak için
```bash
git tag <version> <commit_hash>
```

- Mevcut sürüm etiketlerini görmek için
```bash
git tag
```
- Belirli bir sürüm etiketinin ayrıntılarını görmek için
```bash
git show <version>
```
- Bir sürüm etiketini silmek için
```bash
git tag -d <version>
```

- Yerel olarak oluşturulan bir sürüm etiketini uzak sunucuya göndermek için
```bash
git push origin <version>
```
- Tüm sürüm etiketlerini uzak sunucuya göndermek için
```bash
git push origin --tags
```
- Bir sürüm etiketini uzak sunucudan silmek için
```bash
git push origin :refs/tags/<version>
```

# Git İşbirliği ve Uygulama: 

## Git üzerinde işbirliği yapmanın faydalarını açıklayın ve nasıl yapılacağını tartışın. 

### Dal Paylaşımı:
 Geliştiriciler projenin farklı özelliklerini veya düzeltmelerini içeren dallar oluşturabilir ve bu dalları diğer ekip üyeleriyle paylaşabilir.

### Kod İncelemeleri:
 Geliştiriciler birbirlerinin kodunu inceleyerek geri bildirim sağlayabilir ve projeye katkıda bulunabilir.

### Birleştirme İşlemleri:
 Geliştiriciler kendi dallarındaki değişiklikleri ana dala birleştirerek projeye katkıda bulunabilir.

### Ekip İletişimi:
 İletişim herhangi bir işbirliği sürecinin önemli bir parçasıdır. Geliştiriciler projenin ilerlemesi gereksinimler ve sorunlar hakkında düzenli olarak iletişim halinde olmalıdır.

## Bir Git depo üzerinde takım üyeleriyle nasıl işbirliği yapılır? 

Ortak bir depo oluşturma, dallar oluşturma, kod inceleme, ana dala birleştirme, uzak depoya yükleme.

## Git'in çeşitli işbirliği özelliklerini (dal paylaşma, dal birleştirme istekleri, pull requests vb.) nasıl kullanacağınızı gösterin. 

Projenizin ana kopyasından türetilmiş bir dal oluşturun ve üzerinde çalışmaya başlayalım 
```bash
git checkout -b my-feature
```
Yerel dalınızdaki değişiklikleri uzak depoya yükleyerek diğer takım üyeleriyle paylaşın 
```bash
git push origin my-feature
```
Uzak depoya yükledikten sonra birleştirme isteği (pull request) oluşturarak değişikliklerinizi ana dala eklemek için istek gönderin. Bunun için GitHub GitLab veya Bitbucket gibi platformlar üzerinde birleştirme isteği oluşturabilirsiniz.

## Git konuşlandırma (Git forking) nedir ve ne zaman kullanılır? 



## Git'in proje yönetim araçları (GitHub, GitLab, Bitbucket vb.) ile entegrasyonunu nasıl gerçekleştirirsiniz?

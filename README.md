# 📱 Kami Apps Geliştirme Standartları ve İsimlendirme Rehberi

Bu doküman, **Kami Apps** şirketi tarafından geliştirilen mobil uygulamalar için kapsamlı isimlendirme kurallarını, proje yapılandırma standartlarını ve geliştirme süreç rehberini içermektedir. Bu standartların amacı, projelerimizin sürdürülebilir, ölçeklenebilir, profesyonel ve ekip içinde tutarlı olmasını sağlamaktır.

## 🎯 Bu Rehberin Amacı

Bu rehber aşağıdaki konularda standartlaşma sağlar:
- Proje isimlendirme kuralları
- Dosya ve klasör organizasyonu
- Versiyon yönetimi ve sürüm adlandırma
- Git iş akışı standartları
- Platform-specific konfigürasyonlar
- Test süreçleri ve aşamaları

## 📋 İçindekiler

- [Proje Adlandırma Standartları](#-proje-adlandırma-standartları)
- [Platform Konfigürasyonları](#-platform-konfigürasyonları)
- [Dosya ve Klasör Organizasyonu](#-dosya-ve-klasör-organizasyonu)
- [Sürüm Yönetimi](#-sürüm-yönetimi)
- [Git İş Akışı](#git-iş-akışı)
- [Test Süreçleri](#-test-süreçleri)
- [Abonelik Sistemleri](#-abonelik-sistemleri)
- [İsimlendirme Stili Referansı](#-i̇simlendirme-stili-referansı)

---

## 📂 Proje Adlandırma Standartları

### Proje Repository İsimleri
Projeler platform bazında **kebab-case** formatında isimlendirilir:

| Platform | Format Kuralı | Örnek Repository |
|----------|---------------|------------------|
| Android  | `{proje-adı}-android` | `sample-android` |
| iOS      | `{proje-adı}-ios` | `sample-ios` |
| Paylaşılan SDK | `{proje-adı}-sdk` | `sample-sdk` |
| Backend API | `{proje-adı}-api` | `sample-api` |

**Örnek Proje Seti:**
```
github.com/KamiApps/sample-android
github.com/KamiApps/sample-ios
github.com/KamiApps/sample-sdk
github.com/KamiApps/sample-api
```

### Proje Adı Seçim Kuralları
- Kısa ve anlamlı olmalı (maksimum 15 karakter)
- İngilizce kelimeler kullanılmalı
- Özel karakterler ve sayılar mümkün olduğunca kaçınılmalı
- Kelimeler arası `-` karakteri kullanılmalı

---

## 🔧 Platform Konfigürasyonları

### Android Konfigürasyonu

**Package Name Format:** `lowercase` stili
```
com.kamiapps.{projeadi}
```

**Örnek:**
```
com.kamiapps.sample
```

**Application ID Yapısı:**
- **Development:** `com.kamiapps.sample.dev`
- **Staging:** `com.kamiapps.sample.staging`
- **Production:** `com.kamiapps.sample`

### iOS Konfigürasyonu

**Bundle Identifier Format:** `PascalCase` stili
```
com.kamiapps.{ProjeAdi}
```

**Örnek:**
```
com.kamiapps.Sample
```

**Bundle ID Yapısı:**
- **Development:** `com.kamiapps.Sample.dev`
- **Staging:** `com.kamiapps.Sample.staging`
- **Production:** `com.kamiapps.Sample`

---

## 📁 Dosya ve Klasör Organizasyonu

### Android Klasör Yapısı
Android projelerinde **lowercase** stili kullanılır:

```
app/
├── src/
│   ├── main/
│   │   ├── java/com/kamiapps/sample/
│   │   │   ├── ui/
│   │   │   │   ├── login/          # lowercase
│   │   │   │   │   ├── LoginScreen.kt      # PascalCase
│   │   │   │   │   └── LoginViewModel.kt   # PascalCase
│   │   │   │   ├── tasklist/      # lowercase
│   │   │   │   │   ├── TaskListScreen.kt
│   │   │   │   │   └── TaskListViewModel.kt
│   │   │   ├── data/
│   │   │   │   ├── model/          # lowercase
│   │   │   │   │   └── TaskModel.kt        # PascalCase
│   │   │   │   └── repository/     # lowercase
│   │   │   │       └── TaskRepository.kt   # PascalCase
│   │   │   └── utils/              # lowercase
│   │   │       └── DateHelper.kt           # PascalCase
```

### iOS Klasör Yapısı
iOS projelerinde **PascalCase** stili kullanılır:

```
Sample/
├── Views/                          # PascalCase
│   ├── Login/                      # PascalCase
│   │   ├── LoginView.swift         # PascalCase
│   │   └── LoginViewModel.swift    # PascalCase
│   └── TaskList/                   # PascalCase
│       ├── TaskListView.swift
│       └── TaskListViewModel.swift
├── Models/                         # PascalCase
│   └── TaskModel.swift            # PascalCase
├── Services/                       # PascalCase
│   └── APIService.swift           # PascalCase
└── Utils/                          # PascalCase
    └── DateHelper.swift           # PascalCase
```

---

## 📊 Sürüm Yönetimi

### Sürüm Numarası Formatı
**Semantic Versioning (SemVer)** standardı kullanılır:

```
MAJOR.MINOR.PATCH
```

**Örnek:** `1.2.3`

- **MAJOR:** Geriye uyumsuz değişiklikler
- **MINOR:** Geriye uyumlu yeni özellikler
- **PATCH:** Geriye uyumlu hata düzeltmeleri

### Sürüm Kodları

**Android Version Code:**
```
MAJOR * 10000 + MINOR * 100 + PATCH
```
**Örnek:** v1.2.3 → Version Code: 10203

**iOS Build Number:**
```
MAJOR.MINOR.PATCH.BUILD
```
**Örnek:** 1.2.3.47

### Pre-release Sürümleri
**Format:** `{sürüm}-{aşama}.{numara}`

**Örnekler:**
- `1.0.0-alpha.1` - İlk alpha sürümü
- `1.0.0-beta.3` - Üçüncü beta sürümü
- `1.0.0-rc.1` - İlk release candidate

---

## 🌿 Git İş Akışı

### Branch İsimlendirmesi
**kebab-case** formatı kullanılır:

```
{tip}/{kısa-açıklama}
```

**Branch Tipleri:**
- `feature/` - Yeni özellik geliştirme
- `bugfix/` - Hata düzeltme
- `hotfix/` - Acil üretim düzeltmesi
- `release/` - Sürüm hazırlama
- `chore/` - Proje bakımı

**Örnekler:**
```
feature/user-authentication
feature/task-management
bugfix/login-validation-error
hotfix/crash-on-startup
release/v1.2.0
chore/update-dependencies
```

### Commit Mesajları
**Conventional Commits** standardı kullanılır:

```
{tip}: {açıklama}

[isteğe bağlı gövde]

[isteğe bağlı footer]
```

**Commit Tipleri:**
- `feat:` - Yeni özellik
- `fix:` - Hata düzeltme
- `docs:` - Dokümantasyon
- `style:` - Kod formatı
- `refactor:` - Kod yeniden yapılandırma
- `test:` - Test ekleme/düzeltme
- `chore:` - Proje bakımı

**Örnekler:**
```
feat: kullanıcı giriş ekranı eklendi
fix: görev listesi boş durumda crash sorunu düzeltildi
docs: API dokümantasyonu güncellendi
refactor: authentication servisleri sadeleştirildi
```

---

## 🧪 Test Süreçleri

### Test Aşamaları

#### Android Test Aşamaları

**1. Development (DEV)**
- **App ID:** `com.kamiapps.sample.dev`
- **Version:** `1.0.0-dev.{build-number}`
- **Ortam:** Yerel geliştirme
- **Test Türü:** Unit testler, instrumented testler

**2. Alpha Testing**
- **App ID:** `com.kamiapps.sample.alpha`
- **Version:** `1.0.0-alpha.{iteration}`
- **Dağıtım:** Firebase App Distribution
- **Hedef:** İç ekip testi

**3. Beta Testing**
- **App ID:** `com.kamiapps.sample.beta`
- **Version:** `1.0.0-beta.{iteration}`
- **Dağıtım:** Google Play Internal Testing
- **Hedef:** Beta kullanıcıları

**4. Release Candidate**
- **App ID:** `com.kamiapps.sample`
- **Version:** `1.0.0-rc.{iteration}`
- **Dağıtım:** Google Play Closed Testing
- **Hedef:** Son kabul testleri

**5. Production**
- **App ID:** `com.kamiapps.sample`
- **Version:** `1.0.0`
- **Dağıtım:** Google Play Store
- **Hedef:** Genel kullanıcılar

#### iOS Test Aşamaları

**1. Development (DEV)**
- **Bundle ID:** `com.kamiapps.Sample.dev`
- **Version:** `1.0.0-dev.{build-number}`
- **Ortam:** Xcode Simulator/Device
- **Test Türü:** Unit testler, UI testler

**2. Alpha Testing**
- **Bundle ID:** `com.kamiapps.Sample.alpha`
- **Version:** `1.0.0-alpha.{iteration}`
- **Dağıtım:** Xcode/TestFlight Internal
- **Hedef:** İç ekip testi

**3. Beta Testing**
- **Bundle ID:** `com.kamiapps.Sample.beta`
- **Version:** `1.0.0-beta.{iteration}`
- **Dağıtım:** TestFlight External Testing
- **Hedef:** Beta kullanıcıları

**4. Release Candidate**
- **Bundle ID:** `com.kamiapps.Sample`
- **Version:** `1.0.0-rc.{iteration}`
- **Dağıtım:** TestFlight
- **Hedef:** Son kabul testleri

**5. Production**
- **Bundle ID:** `com.kamiapps.Sample`
- **Version:** `1.0.0`
- **Dağıtım:** App Store
- **Hedef:** Genel kullanıcılar

---

## 💳 Abonelik Sistemleri

### Abonelik Ürün İsimlendirmesi
**snake_case** formatı kullanılır:

#### iOS Ürün Kimlikleri (App Store Connect)
```
{app_name}_{plan}_{period}
```

**Örnekler:**
- `sample_premium_weekly`
- `sample_premium_monthly`
- `sample_premium_yearly`
- `sample_pro_lifetime`

#### Android Ürün Kimlikleri (Google Play Console)
```
{namespace}:{product-name}
```

**Örnekler:**
- `sample_premium:sample-premium-weekly`
- `sample_premium:sample-premium-monthly`
- `sample_premium:sample-premium-yearly`
- `sample_premium:sample-pro-lifetime`

### RevenueCat Entitlements
**snake_case** formatı kullanılır:

**Örnekler:**
- `premium` - Temel premium özellikler
- `pro_access` - Pro seviye erişim
- `unlimited_usage` - Sınırsız kullanım

---

## 📖 İsimlendirme Stili Referansı

Bu tabloda hangi durumda hangi isimlendirme stilinin kullanıldığı belirtilmiştir:

| Stil | Format | Kullanım Alanı | Örnek |
|------|--------|----------------|-------|
| **kebab-case** | `kelime-kelime` | • GitHub repository isimleri<br>• Git branch isimleri<br>• URL-friendly kimlikler<br>• Android Play Store product names | `sample-android`<br>`feature/user-auth`<br>`sample-premium-weekly` |
| **snake_case** | `kelime_kelime` | • Database field isimleri<br>• Environment variables<br>• iOS/Android product IDs<br>• RevenueCat entitlements<br>• Configuration keys | `user_profile`<br>`sample_premium_weekly`<br>`pro_access` |
| **PascalCase** | `KelimeKelime` | • iOS Bundle Identifier<br>• Kotlin class isimleri<br>• Swift class isimleri<br>• iOS klasör isimleri<br>• Component isimleri | `com.kamiapps.Sample`<br>`LoginViewModel.kt`<br>`TaskListView.swift`<br>`Views/Login/` |
| **camelCase** | `kelimeKelime` | • Değişken isimleri<br>• Fonksiyon isimleri<br>• Property isimleri<br>• JSON field isimleri | `userName`<br>`fetchUserData()`<br>`isLoginValid` |
| **lowercase** | `kelimekelime` | • Android package names<br>• Domain isimleri<br>• Tekil klasör isimleri | `com.kamiapps.sample`<br>• `data/`<br>• `utils/` |
| **UPPERCASE** | `KELIME_KELIME` | • Sabitler (Constants)<br>• Environment variable isimleri<br>• Build configuration | `API_BASE_URL`<br>`DATABASE_NAME`<br>`DEBUG_MODE` |

---

## ✅ Hızlı Kontrol Listesi

Yeni bir proje başlatırken aşağıdaki kontrol listesini kullanın:

### Proje Kurulumu
- [ ] Repository ismi `kebab-case` formatında
- [ ] Android package name `lowercase` formatında
- [ ] iOS Bundle ID `PascalCase` formatında
- [ ] Başlangıç sürümü `1.0.0-dev.1` olarak ayarlandı
- [ ] Git flow branch yapısı kuruldu

### Test Ortamları
- [ ] Development konfigürasyonu oluşturuldu
- [ ] Alpha test ortamı hazırlandı
- [ ] Beta test ortamı yapılandırıldı
- [ ] Production konfigürasyonu tamamlandı

### Abonelik Sistemi (Eğer varsa)
- [ ] iOS product IDs tanımlandı
- [ ] Android product IDs oluşturuldu
- [ ] RevenueCat entitlements belirlendi

---

## Destek ve İletişim

Bu rehberle ilgili sorularınız için:
- **Teknik Sorular:** Geliştirme ekibine başvurun
- **Süreç Soruları:** Proje yöneticisine danışın
- **Güncelleme Önerileri:** GitHub issue açın

---

**Son Güncelleme:** 1 Ağustos 2025  
**Versiyon:** 1.0.0  
**Hazırlayan:** Kami Apps Geliştirme Ekibi

> 💡 **Not:** Bu rehber canlı bir dokümandır ve geliştirme süreçlerimizle birlikte güncellenecektir. Lütfen düzenli olarak kontrol edin.

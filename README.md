# Mahami — Legal & Support Pages

صفحات Privacy / Terms / Support لتطبيق **مهامي اليومية** (Mahami).
مُعدَّة للنشر على GitHub Pages مع custom domain `mahami.app`.

## البنية

```
legal-pages/
├── index.html          → mahami.app/
├── privacy/index.html  → mahami.app/privacy
├── terms/index.html    → mahami.app/terms
├── support/index.html  → mahami.app/support
├── 404.html            → fallback لأي مسار غير موجود
├── CNAME               → custom domain
└── .nojekyll           → يعطّل معالجة Jekyll الافتراضيّة
```

## خطوات النشر على GitHub Pages

### 1. أنشئ Repository جديد على GitHub
- اسم مقترح: `mahami-pages` أو `mahami.app`
- Public (لازم لـ Pages المجاني)
- بدون README مبدئي

### 2. ارفع الملفات
من Terminal على Windows:

```powershell
cd D:\claude\claude-mhami\legal-pages
git init
git add .
git commit -m "Initial: Privacy + Terms + Support pages"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mahami-pages.git
git push -u origin main
```

### 3. فعّل GitHub Pages
- اذهب إلى **Repository Settings → Pages**.
- **Source:** اختر `Deploy from a branch`.
- **Branch:** `main`، **Folder:** `/ (root)`.
- اضغط **Save**.

بعد ١-٢ دقيقة، الصفحات ستكون متاحة على:
```
https://YOUR_USERNAME.github.io/mahami-pages/
https://YOUR_USERNAME.github.io/mahami-pages/privacy
https://YOUR_USERNAME.github.io/mahami-pages/terms
https://YOUR_USERNAME.github.io/mahami-pages/support
```

### 4. اربط Custom Domain (`mahami.app`)

#### خيار أ — ملك النطاق (إذا كنت تملك mahami.app)
في إعدادات DNS لمزوّد النطاق (Namecheap/GoDaddy/Cloudflare):

أضف **A Records** لـ root domain (apex):
```
@   A   185.199.108.153
@   A   185.199.109.153
@   A   185.199.110.153
@   A   185.199.111.153
```

أو **CNAME** لـ www subdomain:
```
www   CNAME   YOUR_USERNAME.github.io
```

ثم في GitHub Repository Settings → Pages:
- **Custom domain:** `mahami.app` → Save.
- ✅ Enforce HTTPS (بعد ١٠-٣٠ دقيقة).

ملف `CNAME` في الـ repo مكتوب فيه `mahami.app` تلقائيًا.

#### خيار ب — لا تملك mahami.app
احذف ملف `CNAME` من الـ repo، واستخدم الرابط الافتراضي:
```
https://YOUR_USERNAME.github.io/mahami-pages/privacy
```

⚠️ **مهم:** إن استخدمت الرابط الافتراضي، يجب تحديث:
- `Packages/FeaturePaywall/Sources/FeaturePaywall/PaywallView.swift` (legalLink URLs)
- `App/Self/SettingsView.swift` (legalRow URLs)
- App Store Connect → Privacy Policy URL + App Description

### 5. تأكد من العمل قبل App Store Review
افتح في المتصفّح:
- ✅ `https://mahami.app/privacy` يفتح صفحة الخصوصيّة
- ✅ `https://mahami.app/terms` يفتح شروط الاستخدام
- ✅ `https://mahami.app/support` يفتح الدعم
- ✅ HTTPS يعمل (المتصفّح يُظهر قفل)
- ✅ الصفحات تُعرض بـ RTL سليم على mobile

## التحديث المستقبلي
تعديل المحتوى:
1. عدّل `privacy/index.html` (أو `terms/index.html` أو `support/index.html`).
2. حدّث تاريخ "آخر تحديث" في أعلى الصفحة.
3. `git add .` → `git commit -m "Update privacy"` → `git push`.
4. GitHub Pages يُعيد النشر خلال دقيقة.

## ملاحظات

- **support email:** الصفحات تستخدم `twq983@gmail.com`.
- **الخصوصيّة:** المحتوى يطابق فلسفة Mahami (محلّي بالكامل، بلا تتبّع). راجعه قانونيًا إن أردت ضمانًا إضافيًا.
- **الشروط:** EULA الافتراضيّة من Apple مرجع رئيسيّ. للتطبيقات البسيطة هذا كافٍ.
- **التصميم:** الصفحات RTL أولًا مع نسخة إنجليزيّة في أسفل كل صفحة، Light + Dark mode تلقائيًا.
- **CDN/HTTPS:** GitHub Pages يوفّرهما مجانًا.

## App Store Connect

بعد نشر الصفحات وتأكّد عملها، أضف في **App Store Connect**:

| الحقل | القيمة |
|---|---|
| Privacy Policy URL | `https://mahami.app/privacy` |
| Marketing URL (optional) | `https://mahami.app/` |
| Support URL (required) | `https://mahami.app/support` |
| EULA / Terms (Custom) | الصق محتوى `terms/index.html` أو ضع رابط `https://mahami.app/terms` |

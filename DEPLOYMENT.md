# 🚀 Conx Deployment Guide | دليل نشر Conx

Complete guide for deploying Conx app to production with Pi Network integration.

دليل كامل لنشر تطبيق Conx على الإنترنت مع التكامل مع شبكة Pi.

---

## 📋 Prerequisites | المتطلبات الأساسية

### English:
- **Vercel Account** (free): https://vercel.com/signup
- **GitHub Account** (free): https://github.com/join
- **Pi Developer Account**: https://developers.minepi.com
- **Domain** (optional): Your custom domain or use Vercel's free subdomain

### العربية:
- **حساب Vercel** (مجاني): https://vercel.com/signup
- **حساب GitHub** (مجاني): https://github.com/join
- **حساب Pi للمطورين**: https://developers.minepi.com
- **نطاق** (اختياري): نطاقك الخاص أو استخدم النطاق المجاني من Vercel

---

## 🎯 Method 1: Deploy via v0 (Easiest) | الطريقة 1: النشر عبر v0 (الأسهل)

### English:

1. **Click "Publish" Button**
   - In v0 interface, click the "Publish" button at the top right
   - Sign in with your Vercel account if prompted

2. **Configure Deployment**
   - Project Name: `conx-app` (or your preferred name)
   - Framework: Next.js (auto-detected)
   - Root Directory: `./`

3. **Deploy**
   - Click "Deploy"
   - Wait 2-3 minutes for deployment
   - You'll get a URL like: `https://conx-app.vercel.app`

### العربية:

1. **انقر على زر "Publish"**
   - في واجهة v0، انقر على زر "Publish" في الأعلى
   - سجل دخول بحساب Vercel إذا طُلب منك

2. **تكوين النشر**
   - اسم المشروع: `conx-app` (أو اسم تختاره)
   - الإطار: Next.js (يتم اكتشافه تلقائياً)
   - المجلد الرئيسي: `./`

3. **انشر**
   - انقر "Deploy"
   - انتظر 2-3 دقائق للنشر
   - ستحصل على رابط مثل: `https://conx-app.vercel.app`

---

## 🔧 Method 2: Deploy via GitHub + Vercel | الطريقة 2: النشر عبر GitHub + Vercel

### English:

1. **Download Project**
   - Click three dots (⋮) in v0
   - Select "Download ZIP"
   - Extract the ZIP file

2. **Create GitHub Repository**
   - Go to https://github.com/new
   - Repository name: `conx-app`
   - Make it Public or Private
   - Click "Create repository"

3. **Upload Code to GitHub**
   ```bash
   cd conx-app
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/conx-app.git
   git push -u origin main
   ```

4. **Deploy to Vercel**
   - Go to https://vercel.com/new
   - Click "Import Project"
   - Select your `conx-app` repository
   - Click "Deploy"
   - Wait 2-3 minutes

### العربية:

1. **تنزيل المشروع**
   - انقر على النقاط الثلاث (⋮) في v0
   - اختر "Download ZIP"
   - فك ضغط ملف ZIP

2. **إنشاء مستودع GitHub**
   - اذهب إلى https://github.com/new
   - اسم المستودع: `conx-app`
   - اجعله عام أو خاص
   - انقر "Create repository"

3. **رفع الكود إلى GitHub**
   ```bash
   cd conx-app
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/conx-app.git
   git push -u origin main
   ```

4. **النشر على Vercel**
   - اذهب إلى https://vercel.com/new
   - انقر "Import Project"
   - اختر مستودع `conx-app`
   - انقر "Deploy"
   - انتظر 2-3 دقائق

---

## 🔐 Pi Network Verification | التحقق من شبكة Pi

### English:

1. **Access Validation File**
   - After deployment, your validation key is automatically available at:
   - `https://your-domain.vercel.app/validation-key.txt`

2. **Verify on Pi Developer Portal**
   - Go to https://developers.minepi.com
   - Navigate to your app settings
   - Under "Domain Verification", enter: `https://your-domain.vercel.app/validation-key.txt`
   - Click "Verify"
   - Wait 1-2 minutes for confirmation

3. **Configure App Wallet**
   - In Pi Developer Portal, go to "Payment Settings"
   - Your App Wallet Address: `GDBGP63GWW35YTK3SRNI2AUS6JKL3OEO2VM5RKJIT6MGU36RSFGQLKPI`
   - This wallet will receive 0.1% transaction fees

### العربية:

1. **الوصول لملف التحقق**
   - بعد النشر، مفتاح التحقق متاح تلقائياً على:
   - `https://your-domain.vercel.app/validation-key.txt`

2. **التحقق على Pi Developer Portal**
   - اذهب إلى https://developers.minepi.com
   - انتقل إلى إعدادات التطبيق
   - تحت "Domain Verification"، أدخل: `https://your-domain.vercel.app/validation-key.txt`
   - انقر "Verify"
   - انتظر 1-2 دقيقة للتأكيد

3. **تكوين محفظة التطبيق**
   - في Pi Developer Portal، اذهب إلى "Payment Settings"
   - عنوان محفظة التطبيق: `GDBGP63GWW35YTK3SRNI2AUS6JKL3OEO2VM5RKJIT6MGU36RSFGQLKPI`
   - ستستقبل هذه المحفظة رسوم 0.1% من المعاملات

---

## 🌐 Custom Domain Setup (Optional) | إعداد نطاق مخصص (اختياري)

### English:

1. **Add Domain to Vercel**
   - In Vercel dashboard, go to your project
   - Click "Settings" → "Domains"
   - Add your domain: `conx6801.pinet.com`

2. **Configure DNS**
   - Go to your domain provider (Pi Network domain management)
   - Add these records:
     ```
     Type: CNAME
     Name: @
     Value: cname.vercel-dns.com
     ```

3. **Wait for DNS Propagation**
   - Takes 10 minutes to 48 hours
   - Check status in Vercel dashboard

### العربية:

1. **إضافة نطاق إلى Vercel**
   - في لوحة Vercel، اذهب لمشروعك
   - انقر "Settings" → "Domains"
   - أضف نطاقك: `conx6801.pinet.com`

2. **تكوين DNS**
   - اذهب إلى مزود النطاق (إدارة نطاقات Pi Network)
   - أضف هذه السجلات:
     ```
     Type: CNAME
     Name: @
     Value: cname.vercel-dns.com
     ```

3. **انتظر نشر DNS**
   - يستغرق من 10 دقائق إلى 48 ساعة
   - تحقق من الحالة في لوحة Vercel

---

## ⚙️ Environment Variables | متغيرات البيئة

### English:

**Not Required for Basic Deployment**
- The app uses App Wallet address hardcoded in `lib/app-config.ts`
- Pi SDK loads automatically from CDN
- No API keys needed for basic features

**Optional (for future features):**
- `NEXT_PUBLIC_PI_API_KEY` - If you need Pi API access
- `DATABASE_URL` - If you add database integration

### العربية:

**غير مطلوب للنشر الأساسي**
- التطبيق يستخدم عنوان محفظة التطبيق المدمج في `lib/app-config.ts`
- Pi SDK يتم تحميله تلقائياً من CDN
- لا حاجة لمفاتيح API للميزات الأساسية

**اختياري (للميزات المستقبلية):**
- `NEXT_PUBLIC_PI_API_KEY` - إذا كنت بحاجة للوصول لـ Pi API
- `DATABASE_URL` - إذا أضفت تكامل قاعدة بيانات

---

## 🧪 Testing After Deployment | الاختبار بعد النشر

### English:

1. **Test in Pi Browser**
   - Open your deployed URL in Pi Browser on mobile
   - Example: `https://conx-app.vercel.app`
   - Click "Connect Pi Wallet"
   - Verify authentication works

2. **Test Features**
   - ✅ Language switcher (English ↔ Arabic)
   - ✅ Navigation to all pages
   - ✅ Pi SDK detection
   - ✅ Premium subscription display
   - ✅ Transfer page functionality

3. **Check Validation File**
   - Visit: `https://your-domain.vercel.app/validation-key.txt`
   - Should display the validation key

### العربية:

1. **الاختبار في متصفح Pi**
   - افتح رابط التطبيق المنشور في متصفح Pi على الهاتف
   - مثال: `https://conx-app.vercel.app`
   - انقر "ربط محفظة Pi"
   - تحقق من عمل المصادقة

2. **اختبار الميزات**
   - ✅ مبدل اللغة (إنجليزي ↔ عربي)
   - ✅ التنقل لجميع الصفحات
   - ✅ اكتشاف Pi SDK
   - ✅ عرض اشتراكات Premium
   - ✅ وظيفة صفحة التحويل

3. **التحقق من ملف التحقق**
   - زر: `https://your-domain.vercel.app/validation-key.txt`
   - يجب أن يعرض مفتاح التحقق

---

## 🔄 Future Updates | التحديثات المستقبلية

### English:

**Automatic Updates (If deployed via v0 Publish)**
- Updates deploy automatically when you make changes in v0

**Manual Updates (If deployed via GitHub)**
```bash
# Make your changes, then:
git add .
git commit -m "Update: description of changes"
git push origin main
# Vercel will auto-deploy in 2-3 minutes
```

### العربية:

**تحديثات تلقائية (إذا نشرت عبر v0 Publish)**
- التحديثات تُنشر تلقائياً عند إجراء تغييرات في v0

**تحديثات يدوية (إذا نشرت عبر GitHub)**
```bash
# قم بإجراء التغييرات، ثم:
git add .
git commit -m "Update: وصف التغييرات"
git push origin main
# Vercel سينشر تلقائياً في 2-3 دقائق
```

---

## 🆘 Troubleshooting | حل المشاكل

### Pi SDK Not Available | Pi SDK غير متاح

**English:**
- Make sure you're opening the app in **Pi Browser only**
- Clear browser cache and try again
- Check that your domain is verified in Pi Developer Portal

**Arabic:**
- تأكد من فتح التطبيق في **متصفح Pi فقط**
- امسح ذاكرة التخزين المؤقت وحاول مجدداً
- تحقق من أن نطاقك مُتحقق منه في Pi Developer Portal

### Deployment Failed | فشل النشر

**English:**
- Check Vercel deployment logs
- Make sure all files are included
- Verify `package.json` has all dependencies

**Arabic:**
- تحقق من سجلات النشر في Vercel
- تأكد من تضمين جميع الملفات
- تحقق من أن `package.json` يحتوي على جميع التبعيات

---

## 📞 Support | الدعم

**English:**
- Pi Developer Forum: https://developers.minepi.com/forum
- Vercel Support: https://vercel.com/help
- GitHub Issues: Create issue in your repository

**Arabic:**
- منتدى Pi للمطورين: https://developers.minepi.com/forum
- دعم Vercel: https://vercel.com/help
- مشاكل GitHub: أنشئ issue في مستودعك

---

## ✅ Deployment Checklist | قائمة التحقق من النشر

- [ ] App deployed to Vercel
- [ ] Custom domain configured (if using)
- [ ] Validation file accessible
- [ ] Pi Network domain verified
- [ ] App Wallet configured in Pi Developer Portal
- [ ] Tested authentication in Pi Browser
- [ ] All pages loading correctly
- [ ] Language switcher working
- [ ] Premium plans displaying correct prices

---

**🎉 Congratulations! Your Conx app is now live!**

**🎉 تهانينا! تطبيق Conx الخاص بك الآن مباشر!**

# 📦 Conx Deployment Guide | دليل نشر Conx

**Last Updated:** December 24, 2025

---

## 🌍 English Version

### Prerequisites
- Git installed on your computer
- GitHub account (free)
- Vercel account (free) - Sign up at [vercel.com](https://vercel.com)
- Pi Network Developer account at [developers.minepi.com](https://developers.minepi.com)

### Step 1: Deploy to Vercel

#### Option A: Using Vercel Dashboard (Recommended)
1. **Download Your Code**
   - Click the 3-dot menu in v0
   - Select "Download ZIP"
   - Extract the ZIP file to your computer

2. **Push to GitHub**
   ```bash
   cd conx-project
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/conx.git
   git push -u origin main
   ```

3. **Deploy on Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository
   - Vercel will auto-detect Next.js
   - Click "Deploy"

4. **Custom Domain Setup**
   - Go to Project Settings → Domains
   - Add your domain: `conx6801.pinet.com`
   - Follow DNS configuration instructions
   - Add these DNS records:
     ```
     Type: A
     Name: @
     Value: 76.76.21.21

     Type: CNAME
     Name: www
     Value: cname.vercel-dns.com
     ```

#### Option B: Using Vercel CLI
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
cd conx-project
vercel

# Follow the prompts:
# - Set up and deploy? Yes
# - Which scope? Your account
# - Link to existing project? No
# - Project name? conx
# - Directory? ./
# - Override settings? No

# For production deployment
vercel --prod
```

### Step 2: Configure Environment Variables

Add these in Vercel Dashboard → Project → Settings → Environment Variables:

```env
# Pi Network Configuration (REQUIRED)
NEXT_PUBLIC_PI_APP_ID=your_pi_app_id_here
PI_API_KEY=your_pi_api_key_here

# App Wallet (REQUIRED)
APP_WALLET_ADDRESS=GDBGP63GWW35YTK3SRNI2AUS6JKL3OEO2VM5RKJIT6MGU36RSFGQLKPI

# Pi Network API (REQUIRED for production)
NEXT_PUBLIC_PI_NETWORK_API_URL=https://api.minepi.com

# Pricing Engine (REQUIRED for dynamic pricing)
NEXT_PUBLIC_PI_MARKET_API=https://api.coingecko.com/api/v3/simple/price?ids=pi-network&vs_currencies=usd
NEXT_PUBLIC_AI_COST_PER_MESSAGE=0.0001
NEXT_PUBLIC_TARGET_PROFIT_MARGIN=0.15

# Development only (for testing)
NEXT_PUBLIC_DEV_SUPABASE_REDIRECT_URL=http://localhost:3000
```

### Step 3: Verify Domain on Pi Network

1. **Check Validation File**
   - Your domain must be live first
   - Validation file is already at: `public/validation-key.txt`
   - Verify it's accessible: `https://conx6801.pinet.com/validation-key.txt`

2. **Pi Developer Portal**
   - Go to [developers.minepi.com](https://developers.minepi.com)
   - Navigate to your app settings
   - Enter domain verification section
   - Input: `https://conx6801.pinet.com/validation-key.txt`
   - Click "Verify Domain"
   - Wait for confirmation (usually instant)

3. **Configure Pi SDK**
   - Add approved domain to your Pi app settings
   - Enable Pi SDK access
   - Copy your App ID and API Key
   - Add them to Vercel environment variables (see Step 2)

### Step 4: Test Your Deployment

1. **Open Pi Browser**
   - Install Pi Browser on your mobile device
   - Navigate to: `https://conx6801.pinet.com`
   - The app should load without errors

2. **Test Authentication**
   - Click "Authenticate with Pi"
   - Pi SDK should initialize (no "SDK not available" error)
   - Complete authentication flow
   - Check if wallet connects successfully

3. **Test Core Features**
   - Send a test message (translation should work)
   - Try a Pi transfer (should show proper fees)
   - Check Premium subscription page (prices should be dynamic)
   - Verify all buttons and navigation work

### Step 5: Monitor and Maintain

1. **Vercel Analytics**
   - Go to Vercel Dashboard → Analytics
   - Monitor page views, performance, errors

2. **Check Build Logs**
   - If deployment fails, check: Dashboard → Deployments → Click deployment → View Logs
   - Common issues and fixes below

### Common Build Issues and Fixes

#### Issue 1: Module Resolution Error
```
Error: Module not found: Can't resolve '@/contexts/language-context'
```

**Fix:** The tsconfig.json is already configured correctly. If you still see this:
1. Ensure `contexts/language-context.tsx` exists in your repo
2. Check that the file is not in `.gitignore`
3. Verify the path alias in `tsconfig.json`:
   ```json
   {
     "compilerOptions": {
       "paths": {
         "@/*": ["./*"]
       }
     }
   }
   ```
4. Clear cache and redeploy:
   ```bash
   vercel --force
   ```

#### Issue 2: Pi SDK Not Loading
**Symptoms:** "Pi SDK not available" error in Pi Browser

**Fix:**
1. Check environment variables are set correctly
2. Verify domain is verified on Pi Developer Portal
3. Ensure your app is approved on Pi Network
4. Check that `next.config.mjs` has correct headers (already configured)

#### Issue 3: Build Timeout
**Fix:**
1. Optimize images and assets
2. Use Vercel Pro plan for longer build times
3. Check for circular dependencies

### Business Model Configuration

The app is configured with NO one-time purchases - only subscriptions:

1. **Pricing Engine:** `lib/pricing-engine.ts`
   - Automatically fetches Pi market price
   - Calculates subscription costs based on API usage
   - Maintains 15% profit margin
   - Updates prices dynamically

2. **Terms of Service:** `app/terms/page.tsx`
   - Legal clause allowing price changes without notice
   - Clear subscription-only policy
   - Both English and Arabic versions

3. **No Single Purchases:**
   - All payment options removed
   - Only monthly subscriptions available
   - Prices adjust based on market conditions

### Support and Resources

- **Pi Network Docs:** [docs.minepi.com](https://docs.minepi.com)
- **Vercel Docs:** [vercel.com/docs](https://vercel.com/docs)
- **Next.js Docs:** [nextjs.org/docs](https://nextjs.org/docs)
- **Conx Support:** Open issue on GitHub or contact via Pi Network

---

## 🇸🇦 النسخة العربية

### المتطلبات الأساسية
- تثبيت Git على جهازك
- حساب GitHub (مجاني)
- حساب Vercel (مجاني) - سجل في [vercel.com](https://vercel.com)
- حساب مطور Pi Network في [developers.minepi.com](https://developers.minepi.com)

### الخطوة 1: النشر على Vercel

#### الخيار أ: استخدام لوحة Vercel (موصى به)
1. **تحميل الكود**
   - انقر على قائمة النقاط الثلاث في v0
   - اختر "Download ZIP"
   - فك ضغط الملف على جهازك

2. **رفع على GitHub**
   ```bash
   cd conx-project
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/conx.git
   git push -u origin main
   ```

3. **النشر على Vercel**
   - اذهب إلى [vercel.com](https://vercel.com)
   - انقر "New Project"
   - استورد مستودع GitHub الخاص بك
   - Vercel سيكتشف Next.js تلقائياً
   - انقر "Deploy"

4. **إعداد النطاق المخصص**
   - اذهب إلى إعدادات المشروع ← Domains
   - أضف نطاقك: `conx6801.pinet.com`
   - اتبع تعليمات تكوين DNS
   - أضف هذه السجلات:
     ```
     النوع: A
     الاسم: @
     القيمة: 76.76.21.21

     النوع: CNAME
     الاسم: www
     القيمة: cname.vercel-dns.com
     ```

#### الخيار ب: استخدام Vercel CLI
```bash
# تثبيت Vercel CLI
npm install -g vercel

# النشر
cd conx-project
vercel

# اتبع التعليمات:
# - الإعداد والنشر؟ نعم
# - أي نطاق؟ حسابك
# - ربط بمشروع موجود؟ لا
# - اسم المشروع؟ conx
# - المجلد؟ ./
# - تجاوز الإعدادات؟ لا

# للنشر الإنتاجي
vercel --prod
```

### الخطوة 2: تكوين متغيرات البيئة

أضف هذه في لوحة Vercel ← المشروع ← الإعدادات ← متغيرات البيئة:

```env
# تكوين Pi Network (مطلوب)
NEXT_PUBLIC_PI_APP_ID=معرف_تطبيق_pi_الخاص_بك
PI_API_KEY=مفتاح_api_الخاص_بك

# محفظة التطبيق (مطلوب)
APP_WALLET_ADDRESS=GDBGP63GWW35YTK3SRNI2AUS6JKL3OEO2VM5RKJIT6MGU36RSFGQLKPI

# Pi Network API (مطلوب للإنتاج)
NEXT_PUBLIC_PI_NETWORK_API_URL=https://api.minepi.com

# محرك التسعير (مطلوب للتسعير الديناميكي)
NEXT_PUBLIC_PI_MARKET_API=https://api.coingecko.com/api/v3/simple/price?ids=pi-network&vs_currencies=usd
NEXT_PUBLIC_AI_COST_PER_MESSAGE=0.0001
NEXT_PUBLIC_TARGET_PROFIT_MARGIN=0.15

# للتطوير فقط (للاختبار)
NEXT_PUBLIC_DEV_SUPABASE_REDIRECT_URL=http://localhost:3000
```

### الخطوة 3: التحقق من النطاق على Pi Network

1. **التحقق من ملف التحقق**
   - يجب أن يكون نطاقك مباشراً أولاً
   - ملف التحقق موجود في: `public/validation-key.txt`
   - تحقق من إمكانية الوصول إليه: `https://conx6801.pinet.com/validation-key.txt`

2. **بوابة مطوري Pi**
   - اذهب إلى [developers.minepi.com](https://developers.minepi.com)
   - انتقل إلى إعدادات التطبيق الخاص بك
   - أدخل قسم التحقق من النطاق
   - أدخل: `https://conx6801.pinet.com/validation-key.txt`
   - انقر "Verify Domain"
   - انتظر التأكيد (عادةً فوري)

3. **تكوين Pi SDK**
   - أضف النطاق المعتمد إلى إعدادات تطبيق Pi الخاص بك
   - فعّل الوصول إلى Pi SDK
   - انسخ معرف التطبيق ومفتاح API
   - أضفهما إلى متغيرات بيئة Vercel (انظر الخطوة 2)

### الخطوة 4: اختبار النشر

1. **افتح متصفح Pi**
   - ثبّت متصفح Pi على جهازك المحمول
   - انتقل إلى: `https://conx6801.pinet.com`
   - يجب أن يتم تحميل التطبيق بدون أخطاء

2. **اختبار المصادقة**
   - انقر "Authenticate with Pi"
   - يجب أن يتم تهيئة Pi SDK (لا يوجد خطأ "SDK not available")
   - أكمل عملية المصادقة
   - تحقق من نجاح الاتصال بالمحفظة

3. **اختبار الميزات الأساسية**
   - أرسل رسالة تجريبية (يجب أن تعمل الترجمة)
   - جرب تحويل Pi (يجب أن تظهر الرسوم الصحيحة)
   - تحقق من صفحة اشتراك Premium (يجب أن تكون الأسعار ديناميكية)
   - تحقق من عمل جميع الأزرار والتنقل

### الخطوة 5: المراقبة والصيانة

1. **تحليلات Vercel**
   - اذهب إلى لوحة Vercel ← التحليلات
   - راقب مشاهدات الصفحة، الأداء، الأخطاء

2. **التحقق من سجلات البناء**
   - إذا فشل النشر، تحقق من: اللوحة ← عمليات النشر ← انقر على النشر ← عرض السجلات
   - المشاكل الشائعة والحلول أدناه

### المشاكل الشائعة في البناء والحلول

#### المشكلة 1: خطأ في حل الوحدة
```
Error: Module not found: Can't resolve '@/contexts/language-context'
```

**الحل:** ملف tsconfig.json مُكوَّن بشكل صحيح بالفعل. إذا ما زلت ترى هذا:
1. تأكد من وجود `contexts/language-context.tsx` في المستودع
2. تحقق من أن الملف ليس في `.gitignore`
3. تحقق من اختصار المسار في `tsconfig.json`:
   ```json
   {
     "compilerOptions": {
       "paths": {
         "@/*": ["./*"]
       }
     }
   }
   ```
4. امسح الذاكرة المؤقتة وأعد النشر:
   ```bash
   vercel --force
   ```

#### المشكلة 2: لا يتم تحميل Pi SDK
**الأعراض:** خطأ "Pi SDK not available" في متصفح Pi

**الحل:**
1. تحقق من تعيين متغيرات البيئة بشكل صحيح
2. تحقق من التحقق من النطاق في بوابة مطوري Pi
3. تأكد من الموافقة على تطبيقك على Pi Network
4. تحقق من أن `next.config.mjs` يحتوي على headers الصحيحة (تم التكوين بالفعل)

#### المشكلة 3: انتهاء مهلة البناء
**الحل:**
1. حسّن الصور والأصول
2. استخدم خطة Vercel Pro لأوقات بناء أطول
3. تحقق من التبعيات الدائرية

### تكوين نموذج الأعمال

التطبيق مُكوَّن بدون مشتريات لمرة واحدة - اشتراكات فقط:

1. **محرك التسعير:** `lib/pricing-engine.ts`
   - يجلب سعر سوق Pi تلقائياً
   - يحسب تكاليف الاشتراك بناءً على استخدام API
   - يحافظ على هامش ربح 15٪
   - يحدّث الأسعار بشكل ديناميكي

2. **شروط الخدمة:** `app/terms/page.tsx`
   - بند قانوني يسمح بتغيير الأسعار دون إشعار
   - سياسة واضحة للاشتراكات فقط
   - إصدارات بالإنجليزية والعربية

3. **لا مشتريات لمرة واحدة:**
   - تم إزالة جميع خيارات الدفع لمرة واحدة
   - اشتراكات شهرية فقط متاحة
   - الأسعار تتكيف بناءً على ظروف السوق

### الدعم والموارد

- **مستندات Pi Network:** [docs.minepi.com](https://docs.minepi.com)
- **مستندات Vercel:** [vercel.com/docs](https://vercel.com/docs)
- **مستندات Next.js:** [nextjs.org/docs](https://nextjs.org/docs)
- **دعم Conx:** افتح مشكلة على GitHub أو تواصل عبر Pi Network

---

## 🚀 Quick Reference

### Essential Commands

```bash
# Local development
npm run dev

# Build locally (to test build issues)
npm run build

# Deploy to Vercel
vercel --prod

# Check build logs
vercel logs

# List deployments
vercel ls
```

### Important URLs

- **Your App:** https://conx6801.pinet.com
- **Validation File:** https://conx6801.pinet.com/validation-key.txt
- **Vercel Dashboard:** https://vercel.com/dashboard
- **Pi Developer Portal:** https://developers.minepi.com

### Environment Variables Quick Reference

| Variable | Required | Description |
|----------|----------|-------------|
| `NEXT_PUBLIC_PI_APP_ID` | ✅ Yes | Your Pi app ID from developer portal |
| `PI_API_KEY` | ✅ Yes | Your Pi API key |
| `APP_WALLET_ADDRESS` | ✅ Yes | Your app wallet (already set) |
| `NEXT_PUBLIC_PI_NETWORK_API_URL` | ✅ Yes | Pi Network API endpoint |
| `NEXT_PUBLIC_PI_MARKET_API` | ✅ Yes | Price feed API |
| `NEXT_PUBLIC_AI_COST_PER_MESSAGE` | ✅ Yes | AI translation cost |
| `NEXT_PUBLIC_TARGET_PROFIT_MARGIN` | ✅ Yes | Target profit (0.15 = 15%) |

---

**Need Help?** 
- Check the FAQ section in README.md
- Contact Pi Network support
- Open an issue on GitHub

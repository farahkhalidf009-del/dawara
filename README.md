# دوّرها — النشر على Vercel

## من GitHub والمتصفح

1. ألغِ مفتاح OpenAI القديم الذي كان موجودًا في `config.js` وأنشئ مفتاحًا جديدًا. لا ترفعه إلى GitHub ولا تضعه في ملفات المتصفح.
2. أنشئ مستودعًا على GitHub، ثم اختر **Add file → Upload files**.
3. ارفع الملفات التالية مباشرة في جذر المستودع، وليس داخل مجلد إضافي:
   - `indx.html`, `scan.html`, `map.html`, `about.html`
   - `logo.png`, `logo.jpeg`, `image.jpeg`
   - `package.json`, `vercel.json`
   - مجلد `api` كاملًا، ويحتوي `analyze.js`
   - ملفا `.gitignore` و`.vercelignore` إن كانا ظاهرين
4. لا ترفع مجلد `_test` أو أي ملف `.env` أو مفاتيح سرية.
5. افتح https://vercel.com/new وسجّل الدخول بحساب GitHub، ثم اختر المستودع واضغط **Import**.
6. اختر **Framework Preset: Other** و**Root Directory: ./ **. اترك Build Command وOutput Directory بالإعداد الافتراضي، ولا تضف أمر بناء.
7. في **Environment Variables** أضف `OPENAI_API_KEY` وقيمته المفتاح الجديد. المتغير `OPENAI_MODEL` اختياري، والقيمة الافتراضية `gpt-4.1-mini`.
8. اضغط **Deploy**، ثم افتح الرابط الناتج.
9. جرّب الصفحة الرئيسية، ثم الكاميرا وتحليل صورة والخريطة. امنح المتصفح صلاحية الكاميرا والموقع عند الحاجة.

إذا أضفت المفتاح أو عدّلته بعد النشر، نفّذ **Redeploy** ليُستخدم في النشر الجديد.

المسار `/` يعرض `indx.html` مع الحفاظ على الروابط القديمة. الفحص يتصل بالدالة `/api/analyze`، والمفتاح يُقرأ على الخادم فقط. فتح HTML مباشرة من الجهاز لا يشغّل دالة الفحص.

دالة الفحص متاحة لزوار الموقع وتستهلك رصيد OpenAI عند الاستخدام؛ إخفاء المفتاح لا يحدّ عدد الطلبات. راقب الاستخدام واضبط الحماية المناسبة من Vercel إذا شاركت الموقع على نطاق واسع.

## مراجع

- https://vercel.com/docs/functions/runtimes/node-js
- https://developers.openai.com/api/reference/overview

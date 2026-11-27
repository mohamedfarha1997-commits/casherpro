# ZAD Restaurant Management System — Phase 2

نسخة Full-stack تأسيسية: واجهة إدارة + API + قاعدة بيانات SQLite + تسجيل دخول وصلاحيات + عمليات بيع ومخزون.

## المتطلبات
- Node.js 20 أو أحدث
- npm

## التشغيل المحلي
1. افتح مجلد `server` في Terminal.
2. نفّذ `npm install`
3. انسخ `.env.example` إلى `.env` وعدّل `JWT_SECRET` إلى قيمة طويلة عشوائية.
4. نفّذ `npm run seed` لإنشاء بيانات أولية.
5. نفّذ `npm start`
6. افتح `http://localhost:3000`

## حساب التجربة بعد seed
- المستخدم: `admin`
- كلمة المرور: `ChangeMe123!`

غيّر كلمة المرور فورًا قبل أي استخدام حقيقي. الحساب التجريبي مخصص للتشغيل المحلي فقط.

## ما تمت إضافته
- Backend باستخدام Express.
- SQLite عبر better-sqlite3.
- JWT login وتجزئة كلمات المرور باستخدام bcrypt.
- أدوار: owner, manager, cashier, kitchen, inventory.
- فروع ومستخدمون وأصناف وخامات ووصفات وموردون وطاولات وطلبات ومصروفات.
- إنشاء طلب بيع داخل transaction، وتسجيل تفاصيله وخصم مكونات الوصفة من المخزون تلقائيًا.
- تغيير حالة الطلب، وإدارة CRUD أساسية للبيانات.
- سجل تدقيق للأحداث الأساسية.
- تصدير نسخة احتياطية من قاعدة البيانات عبر endpoint محمي.

## API مختصر
- `POST /api/auth/login`
- `GET /api/auth/me`
- `GET /api/dashboard`
- `GET|POST /api/products`
- `GET|POST /api/inventory`
- `GET|POST /api/branches`
- `GET|POST /api/tables`
- `GET|POST /api/suppliers`
- `GET|POST /api/staff`
- `GET|POST /api/expenses`
- `GET|POST /api/orders`
- `PATCH /api/orders/:id/status`
- `GET /api/backup`

كل المسارات عدا تسجيل الدخول وhealth تتطلب Bearer token. راجع `server/src/routes.js`.

## حدود هذه النسخة
هذه حزمة تطوير قابلة للتشغيل محليًا وليست اعتمادًا إنتاجيًا نهائيًا. لم يتم ربطها بمزود دفع أو طابعة حرارية فعلية أو الفاتورة الإلكترونية المصرية أو WhatsApp/SMS. SQLite مناسبة كبداية وتشغيل على جهاز/خادم واحد؛ عند تشغيل عدة فروع متزامنة على نطاق كبير يوصى بالانتقال إلى PostgreSQL. يلزم قبل النشر العام إعداد HTTPS، أسرار إنتاجية، نسخ احتياطي مجدول خارج الجهاز، مراقبة، اختبارات أمنية ووظيفية، مراجعة الضرائب والفوترة مع مختص، وخطة صلاحيات واعتماد نهائية.

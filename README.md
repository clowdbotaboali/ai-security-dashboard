# ⚡ LLM Jailbreak Testing Dashboard

لوحة اختبار شاملة لتقنيات اختراق نماذج اللغة الكبيرة — AI Safety Red Teaming

## 📊 الإحصائيات

- **75** تقنية jailbreak
- **20** فئة مختلفة
- **18** نموذج مدعوم عبر OpenRouter
- يغطي: Roleplay, Encoding, Optimization, Agent/MCP, Code Execution, Unicode, Image, Audio, Recursive, DoS, Identity, Data Extraction

## 🚀 التشغيل السريع

### 1. تثبيت المتطلبات

```bash
cd backend
pip install -r requirements.txt
```

### 2. إعداد البيئة

```bash
cp .env.example .env
# عدّل ال_VALUES حسب حاجتك
```

**المتغيرات المطلوبة:**

| المتغير | مطلوب | الوصف |
|---------|-------|-------|
| `OPENROUTER_API_KEY` | ✅ | مفتاح OpenRouter API (بيتحفظ على السيرفر فقط) |
| `DASHBOARD_API_KEY` | ⚠️ | كلمة سر لوحة التحكم (اتركها فاضية للتطوير) |

### 3. تشغيل السيرفر

```bash
cd backend
python server.py
```

افتح المتصفح على `http://localhost:8765`

## 🔐 الأمان

- **API Key على السيرفر فقط** — المفتاح مش بيتخزن في الفرونت إند ولا بيتعرض للمستخدم
- **Dashboard Auth** — كل الـ endpoints محمية بـ `X-API-Key` header
- **CORS مقيّد** — افتراضياً على `localhost` فقط
- **Rate Limiting** — على كل الـ endpoints مع cleanup تلقائي
- **`.gitignore` شامل** — `.env` وقواعد البيانات مستبعدة

## 🔑 API Key

هتحتاج OpenRouter API Key للاختبارات الحقيقية:
1. سجّل على [OpenRouter](https://openrouter.ai/)
2. أضف المفتاح في `.env` كـ `OPENROUTER_API_KEY`

> ⚠️ المفتاح بيتحفظ على السيرفر فقط — مش بيتبعت للفرونت إند

## 📁 هيكل المشروع

```
ai-security-dashboard/
├── backend/
│   ├── server.py              # Flask API server
│   └── requirements.txt       # Python dependencies
├── frontend/
│   └── index.html             # Dashboard UI
├── .env.example               # Configuration template
├── .gitignore
└── README.md
```

## 📡 API Endpoints

| Method | Endpoint | الوصف | Auth |
|--------|----------|-------|------|
| `GET` | `/api/health` | Health check | ❌ |
| `GET` | `/api/config` | Frontend config | ✅ |
| `GET` | `/api/models` | قائمة النماذج المتاحة | ✅ |
| `GET` | `/api/techniques` | قائمة التقنيات | ✅ |
| `POST` | `/api/generate-prompt` | توليد jailbreak prompt | ✅ |
| `POST` | `/api/test` | اختبار تقنية واحدة | ✅ |
| `POST` | `/api/test-batch` | اختبار جماعي | ✅ |
| `GET` | `/api/results` | سجل النتائج | ✅ |
| `GET` | `/api/results/stats` | إحصائيات مجمعة | ✅ |
| `DELETE` | `/api/results/clear` | مسح كل النتائج | ✅ |

### المصادقة

لو `DASHBOARD_API_KEY` متنظمة في `.env`، كل الـ endpoints (عدا `/api/health`) محتاجة:

```
X-API-Key: your_dashboard_password_here
```

## 🛡️ ملاحظات أمنية

- لا تشارك API Key مع أي شخص
- استخدم `.env` لإدارة الإعدادات الحساسة
- السيرفر يستخدم rate limiting مع cleanup تلقائي
- في Production، استخدم reverse proxy (nginx/caddy)
- CORS مقيّد على localhost افتراضياً

## 📄 الرخصة

MIT License

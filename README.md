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
# عدّل القيم حسب حاجتك
```

### 3. تشغيل السيرفر

```bash
cd backend
python server.py
```

افتح المتصفح على `http://localhost:8765`

## 🔑 API Key

هتحتاج OpenRouter API Key للاختبارات الحقيقية:
1. سجّل على [OpenRouter](https://openrouter.ai/)
2. أدخل المفتاح في لوحة التحكم

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

## 🔧 الإعدادات

| المتغير | الافتراضي | الوصف |
|---------|----------|-------|
| `FLASK_DEBUG` | `false` | تفعيل وضع التطوير |
| `FLASK_HOST` | `0.0.0.0` | عنوان السيرفر |
| `FLASK_PORT` | `8765` | المنفذ |
| `DATABASE_PATH` | `jailbreak_results.db` | مسار قاعدة البيانات |
| `ALLOWED_ORIGINS` | `*` | Origins المسموحة (CORS) |

## 📡 API Endpoints

| Method | Endpoint | الوصف |
|--------|----------|-------|
| `GET` | `/api/health` | Health check |
| `GET` | `/api/models` | قائمة النماذج المتاحة |
| `GET` | `/api/techniques` | قائمة التقنيات |
| `POST` | `/api/generate-prompt` | توليد jailbreak prompt |
| `POST` | `/api/test` | اختبار تقنية واحدة |
| `POST` | `/api/test-batch` | اختبار جماعي |
| `GET` | `/api/results` | سجل النتائج |
| `GET` | `/api/results/stats` | إحصائيات مجمعة |
| `DELETE` | `/api/results/clear` | مسح كل النتائج |

## 🛡️ ملاحظات أمنية

- لا تشارك API Key مع أي شخص
- استخدم `.env` لإدارة الإعدادات الحساسة
- السيرفر يستخدم rate limiting افتراضياً
- في Production، استخدم reverse proxy (nginx/caddy)

## 📄 الرخصة

MIT License

# 🔧 הוראות הגדרת סנכרון Google Drive

## שלב 1: יצירת פרויקט ב-Google Cloud

1. גש ל-[Google Cloud Console](https://console.cloud.google.com/)
2. לחץ על "Select a project" → "NEW PROJECT"
3. שם הפרויקט: "Tax Calculator"
4. לחץ "CREATE"

---

## שלב 2: הפעלת Google Drive API

1. בתפריט השמאלי: **APIs & Services** → **Library**
2. חפש: **"Google Drive API"**
3. לחץ עליו → **ENABLE**

---

## שלב 3: יצירת API Key

1. **APIs & Services** → **Credentials**
2. לחץ **+ CREATE CREDENTIALS** → **API key**
3. העתק את ה-API Key
4. לחץ **RESTRICT KEY**:
   - Application restrictions: **HTTP referrers (web sites)**
   - Website restrictions: הוסף את כתובת האתר שלך (לדוגמה: `https://yourusername.github.io/*`)
   - API restrictions: **Restrict key** → בחר **Google Drive API**
5. לחץ **SAVE**

---

## שלב 4: יצירת OAuth Client ID

1. באותו מסך **Credentials**
2. לחץ **+ CREATE CREDENTIALS** → **OAuth client ID**
3. אם מופיע "Configure Consent Screen":
   - לחץ עליו
   - User Type: **External**
   - App name: "Tax Calculator"
   - User support email: האימייל שלך
   - Developer contact: האימייל שלך
   - לחץ **SAVE AND CONTINUE** (דלג על Scopes ו-Test users)
4. חזרה ל-**Credentials** → **+ CREATE CREDENTIALS** → **OAuth client ID**
5. Application type: **Web application**
6. Name: "Tax Calculator Web"
7. Authorized JavaScript origins:
   - הוסף את כתובת האתר שלך (לדוגמה: `https://yourusername.github.io`)
8. לחץ **CREATE**
9. העתק את **Client ID**

---

## שלב 5: עדכון הקוד

פתח את `tax-calculator-complete.html` ומצא את השורות:

```javascript
const GDRIVE_CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com';
const GDRIVE_API_KEY = 'YOUR_API_KEY';
```

החלף:
- `YOUR_CLIENT_ID.apps.googleusercontent.com` → ה-Client ID שלך
- `YOUR_API_KEY` → ה-API Key שלך

---

## שלב 6: פרסום

העלה את 3 הקבצים לשרת (GitHub Pages/Netlify):
- `tax-calculator-complete.html`
- `manifest.json`
- `service-worker.js`

---

## 🎉 סיימנו!

עכשיו כשתלחץ על **"☁️ סנכרון Google Drive"**:

1. תתבקש להתחבר לחשבון Google
2. תאשר גישה לאפליקציה
3. הנתונים נשמרים אוטומטית ל-Google Drive שלך
4. כל מחשב שתיכנס אליו עם אותו חשבון יראה את אותם נתונים!

---

## 🔒 אבטחה

- הנתונים נשמרים **רק ב-Google Drive שלך**
- אף אחד אחר לא יכול לגשת אליהם
- הסיסמה היא חשבון Google שלך
- האפליקציה לא שומרת שום דבר בשרתים חיצוניים

---

## ❓ שאלות נפוצות

**ש: האם זה בטוח?**
ת: כן! הנתונים נשמרים רק ב-Google Drive האישי שלך.

**ש: כמה זה עולה?**
ת: חינם לגמרי! Google Drive נותן 15GB חינם.

**ש: מה קורה אם אני לא מסנכרן?**
ת: הנתונים נשמרים רק במחשב הזה (localStorage).

**ש: האם אני חייב להשתמש בזה?**
ת: לא! זה אופציונלי. האפליקציה עובדת גם בלי.

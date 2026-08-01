# Simvy — מסמכים משפטיים (אתר סטטי)

אתר סטטי לאחסון המסמכים המשפטיים של אפליקציית Simvy. מתארח ב-GitHub Pages, ללא תלות
בספריות חיצוניות וללא בנייה (build).

## דפים

- `index.html` — דף נחיתה עם קישורים לשלושת המסמכים.
- `privacy.html` — מדיניות פרטיות (סעיפים 1–9). סעיף 6 נושא `id="delete-account"`.
- `terms.html` — תקנון ותנאי שימוש (סעיפים 1–11). הסעיפים המהותיים הם 2, 7, 8.
- `delete-account.html` — דף מחיקת חשבון (דרישת חנות; נגיש ללא התחברות).
- `theme.css` — עיצוב משותף.
- `fonts/` — Assistant ו-Manrope כ-woff2, מאוחסנים מקומית.

## עיצוב

הטוקנים ב-`theme.css` משקפים 1:1 את מערכת העיצוב של האפליקציה:

- `:root` — "Atelier Dark" (`src/theme/nocturnalAtelier.ts`), ברירת המחדל.
- `@media (prefers-color-scheme: light)` — "Gallery Light" (`src/theme/galleryLight.ts`).

הפונטים מאוחסנים ב-repo ולא נטענים מ-Google Fonts, כדי שעמוד מדיניות פרטיות לא יעביר
את כתובת ה-IP של המבקר לצד שלישי.

**`terms.html` נושא בלוק `<style>` מוטמע שמשכפל את כללי `.legal-highlight`.** זה מכוון:
לפי חוק החוזים האחידים ההדגשה של הסעיפים המהותיים חייבת להיררנדר גם אם `theme.css`
לא נטען. הבלוק מוצהר **לפני** תגית ה-`<link>` כדי ש-`theme.css` ינצח בספציפיות שווה —
כך הוא נכנס לפעולה רק כשגיליון הסגנון חסר.

## כתובות (URLs)

הדומיין: `https://legal.simvy.app/<page>.html` (רשומת CNAME ב-Hostinger → `danielrubin8-arch.github.io`,
בתוספת קובץ `CNAME` ב-repo). GitHub מפנה אוטומטית מהכתובת הישנה
`danielrubin8-arch.github.io/simvy-legal/*`.

| מסמך | קובץ | חיווט באפליקציה |
|------|------|------------------|
| פרטיות | `privacy.html` | `EXPO_PUBLIC_PRIVACY_URL`, fallback ב-`src/config/urls.ts` |
| תקנון | `terms.html` | `EXPO_PUBLIC_TERMS_URL`, fallback ב-`src/config/urls.ts` |
| מחיקת חשבון | `delete-account.html` | ליסטינג החנות בלבד — האפליקציה משתמשת ב-`privacy.html#delete-account` |

## עדכון תוכן (אחרי סקירת עו"ד)

כל התוכן נמצא ישירות בקבצי ה-HTML. לעריכה:

1. ערוך את הטקסט בקובץ הרלוונטי.
2. עדכן את "עודכן לאחרונה" בראש הדף **ואת התאריך בכרטיס המתאים ב-`index.html`**.
3. `git add -A && git commit -m "..." && git push` — GitHub Pages מתעדכן אוטומטית תוך כדקה.

## TODO לפני פרסום סופי

- [x] שם המפעיל — "דניאל רוקוטניץ רובין" (privacy.html §1, terms.html §1).
- [x] ניסוח אחיד ל-"מפעיל האפליקציה" (זכר) בכל הדפים.
- [ ] סקירת עו"ד (התוכן הוא טיוטה).
- [ ] הוספת מספר עוסק לפתיח, לפני מעבר למסלול בתשלום.

## הערות

- כל הקישורים בין הדפים **יחסיים** — עובדים בכל כתובת בסיס.
- `.nojekyll` מבטיח ש-GitHub Pages מגיש את הקבצים כמות שהם.

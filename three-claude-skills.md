# שלושה skills של Claude שכמעט אף אחד לא מכיר

> נבדק מול ה-README של כל אחד מהשלושה ב-26.10.2026.

שלושה skills קטנים שמוסיפים ל-Claude Code יכולת שאין לו מהקופסה. כל אחד בחינם, קוד פתוח (רישיון MIT).

---

## 1 · Chief of Staff
**נותנים לו מטרה אחת, והוא מפעיל צוות שלם שעובד בשבילכם ברקע.**

- הקוד: [mattpocock/skills › chief-of-staff](https://github.com/mattpocock/skills/tree/main/skills/in-progress/chief-of-staff)
- הוא עדיין בתיקיית «in-progress» של היוצר, כלומר בפיתוח, ולכן הוא לא נכלל בפלאגין של הריפו. מתקינים ידנית:
  1. מורידים את התיקייה `chief-of-staff` מהקישור למעלה.
  2. מעתיקים אותה ל-`~/.claude/skills/chief-of-staff/` (בתיקייה צריך להיות הקובץ `SKILL.md`).
  3. מפעילים בתוך Claude Code עם הפקודה `/chief-of-staff`. הוא לא נדלק לבד.

## 2 · Marketing Psychology
**יותר מחמישים עקרונות של פסיכולוגיה, כמו שנאת הפסד ותמחור, ישר על המודעות שלכם.**

- הקוד: [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
- התקנה, בטרמינל:
  ```
  npx skills add coreyhaines31/marketingskills --skill marketing-psychology -a claude-code
  ```
  או בתוך Claude Code:
  ```
  /plugin marketplace add coreyhaines31/marketingskills
  ```
- אם מריצים את פקודת ה-npx, חשוב להשאיר את `-a claude-code`. בלי זה ההתקנה נכנסת לתיקייה ש-Claude Code לא קורא.
- בלי מפתח ובלי עלות.

## 3 · Last 30 Days
**נותנים לו כל נושא, גם את העסק שלכם, והוא מביא מה אנשים אמרו עליו בחודש האחרון.**

- הקוד: [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill)
- התקנה בתוך Claude Code:
  ```
  /plugin marketplace add mvanhorn/last30days-skill
  /plugin install last30days
  ```
  או בטרמינל:
  ```
  npx skills add mvanhorn/last30days-skill -g
  ```
- חשוב לדעת: Reddit עובד בלי מפתח. YouTube צריך את `yt-dlp` מותקן. TikTok, Instagram ו-X עובדים רק עם מפתח של שירות חיצוני (ScrapeCreators, X).

---

## שאלות נפוצות
- **זה בחינם?** הקוד חינמי. ב-Last 30 Days, הסריקה של TikTok ו-X דורשת מפתח של שירות חיצוני.
- **עובד גם בלי Claude Code?** Marketing Psychology ו-Last 30 Days אפשר להתקין גם לסוכנים אחרים (לפי ה-README שלהם). Chief of Staff נבנה ל-Claude Code.
- **למה Chief of Staff לא בפלאגין?** הוא עדיין בפיתוח אצל היוצר, ולכן מתקינים אותו ידנית.

נתקעתם? כתבו לי בתגובות.

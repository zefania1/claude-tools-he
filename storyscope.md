# StoryScope · ה-skill שמלמד את Claude לכתוב פחות כמו AI

מחקר של University of Maryland ו-Google DeepMind על יותר משישים אלף סיפורים. המבנה לבד, בלי הסגנון, מזהה טקסט של AI ב-93% מהמקרים. למשל: AI מסביר את המסר במפורש ב-77% מהסיפורים, מול 52% אצל בני אדם. לכל מודל יש טביעת אצבע משלו, ואצל Claude המתח עולה הכי פחות.

כאן תמצאו את המאמר, ואיך בונים ממנו skill בתוך Claude Code.

---

## 1 · המאמר
- העמוד: https://arxiv.org/abs/2604.03136
- הורדה כ-PDF: https://arxiv.org/pdf/2604.03136
- קוד המחקר הרשמי: [jenna-russell/storyscope](https://github.com/jenna-russell/storyscope)

## 2 · בונים את ה-skill ב-Claude Code
1. מורידים את המאמר כ-PDF (הקישור למעלה).
2. מתקינים את skill-creator הרשמי של Anthropic, בתוך Claude Code:
   ```
   /plugin marketplace add anthropics/skills
   ```
   ```
   /plugin install example-skills@anthropic-agent-skills
   ```
3. פותחים שיחה, מצרפים את ה-PDF וכותבים:
   ```
   קרא את כל הממצאים במאמר הזה. תתייחס לכל ממצא כחוק שאסור לשבור כשאתה כותב. עכשיו תבנה מזה skill בשם human-scope, שאני מפעיל לפני כל משימת כתיבה.
   ```
4. מעכשיו מפעילים `/human-scope` לפני כל טקסט.

## 3 · ב-Claude.ai (בלי טרמינל)
אותו דבר בשיחה רגילה. להעלאת skill מותאם, לפי ההוראות הרשמיות: [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)

---

## חשוב לדעת
- המחקר נעשה על **סיפורים** (כ-5,000 מילים כל אחד), לא על מודעות או פוסטים קצרים. העקרונות (פחות הסבר-יתר, יותר קצוות פתוחים) עוזרים גם בטקסט שיווקי, אבל זה לא מה שנמדד.
- זה לא כלי לעקיפת גלאים. המטרה היא כתיבה שנשמעת אנושית יותר.
- ב-ChatGPT או Gemini אין skills. אפשר להדביק את אותם עקרונות כהוראות קבועות (Custom Instructions או Project).

## שאלות נפוצות
- **זה בחינם?** המאמר חינמי. Claude לפי המנוי שלכם.
- **זה עובד ב-ChatGPT?** כעקרונות בהוראות קבועות, כן. ה-skill עצמו הוא של Claude.

נתקעתם? כתבו לי בהודעה פרטית באינסטגרם [@barzefania](https://instagram.com/barzefania).

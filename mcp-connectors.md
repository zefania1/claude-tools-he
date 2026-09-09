# ארבעת הקונקטורים לקלוד — המדריך

> נכתב 7.9.26 **מהתיעוד הרשמי של כל אחד מהארבעה.** כל מקור מסומן.
> ⚠️ **שניים מהארבעה דורשים חשבון או מפתח בתשלום — זה כתוב כאן במפורש.**

## מה צריך לפני
- ‏Claude Code מותקן, או Claude Desktop עם קונקטורים.
- ‏Node.js (בדיקה: `node --version`). שלושה מהארבעה רצים דרך `npx`.

---

## 1 · Perplexity — מחקר עם מקורות בזמן אמת
**מה זה עושה:** ‏4 כלים — `search` · `ask` · `research` · `reason`.
```
claude mcp add --transport http perplexity https://api.perplexity.ai/mcp --header "Authorization: Bearer YOUR_API_KEY"
```
🔴 **דורש מפתח-API של Perplexity — חשבון בתשלום.** ‏(אומת 7.9.26: הקצה מחזיר `HTTP 401` בלי מפתח.)
**מקור:** `github.com/perplexityai/modelcontextprotocol` · חבילה: `@perplexity-ai/mcp-server` **v1.2.1** (אומת ב-npm, 7.9.26).

## 2 · Firecrawl — קורא כל אתר ומחזיר טקסט נקי
**מה זה עושה:** הופך דף למרקדאון/JSON נקי; מטפל ב-JavaScript דינמי, פאגינציה והגנות-בוט.
```
claude mcp add firecrawl -- npx -y firecrawl-mcp
```
**מדרג-חינם:** ‏`scrape` · `search` · `parse` עובדים **בלי מפתח** (מוגבלי-קצב: ‏10 scrape/דקה · 5 search/דקה).
‏`crawl` · `map` · `agent` דורשים מפתח (משתנה `FIRECRAWL_API_KEY`).
**נמדד אצלנו 7.9.26:** ‏5 קריאות דרך ה-API החינמי — ‏0.46 · 0.47 · 0.63 · 0.72 · **0.84 שניות**
(האחרונה: ערך ויקיפדיה, ‏71,854 תווים). **הכל מתחת לשנייה.**
**מקור:** `github.com/firecrawl/firecrawl-mcp-server` · חבילה: `firecrawl-mcp` **v3.24.0** (אומת ב-npm).

## 3 · Playwright — דפדפן אמיתי, כולל עכבר
**מה זה עושה:** ‏Chromium/Firefox/WebKit · ~30 כלים · ניווט, לחיצה, הקלדה, מילוי טפסים.
```
claude mcp add playwright -- npx -y @playwright/mcp@latest
```
**כדי שיזיז עכבר בפועל** (‏`browser_mouse_move_xy` · `browser_mouse_click_xy` · `browser_mouse_drag_xy`):
```
claude mcp add playwright -- npx -y @playwright/mcp@latest --caps=vision
```
בלי הדגל הזה השרת עובד על **עץ-הנגישות** ולא על פיקסלים — מהיר וזול יותר, אבל בלי עכבר.
✅ **חינם, קוד-פתוח רשמי של מיקרוסופט.**
**מקור:** `playwright.dev/mcp` · חבילה: `@playwright/mcp` **v0.0.80** (אומת ב-npm).

## 4 · Composio — מאות אפליקציות בחיבור אחד
**מה זה עושה:** ‏500+ אפליקציות (Gmail · Slack · Notion · Google Workspace · Meta Ads · TikTok)
דרך **endpoint אחד** עם גילוי-כלים דינמי (`Tool Router`). ההתקנה היא הוספת קונקטור ואישור
הרשאה — **בלי לכתוב שורת קוד.**
🔴 **דורש חשבון Composio.** מדרג-החינם **לא נבדק על-ידינו.**
**מקור:** `composio.dev` · נקודת-הכניסה `mcp.composio.dev` אומתה חיה (‏HTTP 200, 7.9.26).
**[לאימות]** הנתיב המדויק של הקונקטור משתנה לפי החשבון — נלקח מהדשבורד שלכם.

---

## מה לבדוק אחרי
```
claude mcp list
```
אמור להחזיר את מה שהוספתם עם `✓ Connected`.

## הסייגים, בלי לרכך
- **שניים מהארבעה עולים כסף או דורשים חשבון:** ‏Perplexity (מפתח בתשלום) · Composio (חשבון).
- **חינם באמת:** ‏Playwright. **חינם חלקית:** ‏Firecrawl (מדרג-חינם מוגבל-קצב).
- 🔴 **אין «פרומפט אחד שמתקין את כל הארבעה», וזו הסיבה שהמדריך הזה הוא מדריך.**
  שניים מהארבעה דורשים הרשמה **לפני** שהפקודה בכלל רצה; פרומפט שמתיימר לעקוף את זה
  ייכשל בשקט. **(הכרעת בר, 7.9.26: *"פרומפט ל-4 התקנות זה לא ריאלי"*.)**
- הגרסאות שלמעלה נבדקו ב-npm ב-7.9.26 והן זזות. `@latest` יביא את העדכנית.

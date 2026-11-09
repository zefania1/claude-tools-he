<meta charset="utf-8">
# lemo-opuscar: סרטי אנימציה בקוד, בכל סגנון, על המנוי של Claude: המדריך המלא

הריל: 10 סגנונות אנימציה עם Claude, אותה מכונית אדומה שממריאה, בעשרה עולמות שונים. כל פריים נכתב בקוד.

הריפו: https://github.com/lemomo-ai/lemo-opuscar (קוד פתוח, MIT)

> נבדק אצלנו ב-8.11.26 ו-9.11.26: התקנה דרך `git clone` (המסלול השני למטה), ושש הרצות של קליפ בן 5 שניות, על המנוי, בלי קרדיטים. את פקודות הפלאגין ואת שאר הפרטים לקחנו מה-README. בתחתית הדף: הפרומפטים לכל עשרת הסגנונות מהריל. בריל, כמה מהסגנונות קיבלו סבב תיקון אחד אחרי הפרומפט הראשון; הפרומפטים כאן כבר כוללים את התיקונים.

## מה זה, בשורה

ספרייה של 66 סגנונות-סרט לקלוד קוד (נספר ב-8.11.26). Claude כותב כל פריים בקוד (canvas או three.js), והסרט מרונדר בדפדפן אצלכם במחשב. אין כאן מודל וידאו ואין קרדיטים. לפי ה-README, סרטון שאתם מייצרים הוא שלכם, בלי חובת קרדיט.

## לפני שמתחילים: 6 דברים שכדאי לדעת

1. **זה צורך מכסה מהמנוי.** כל סרט רץ על המנוי של Claude שלכם. קליפ של 5 שניות לקח לנו בין 4 ל-13 דקות. סרט מלא: 30 עד 60 דקות לפי ה-README. דיווח אחד ברשת (80aj.com, 25.9.26), שלא מדדנו בעצמנו: סרטון מוזיקה מלא צרך כ-10% מהמכסה השבועית של Max 5x.
2. **הסגנונות מכוילים ל-Opus 5.5.** על מודל אחר התוצאה עלולה לא להיראות כמו בגלריה (כך כתוב ב-README).
3. **שבעה מעשרת הסגנונות בריל לא נמצאים בספרייה כמו שהם.** Claude בנה אותם מתיאור: Glow Sketch · PS2 · Comic · Flat Vector · Minimal Line · CGI · 3D Animation. הפרומפטים למטה בונים אותם. Pixel Art, Chalkboard ו-Lego קיימים בספרייה בשמות `pixel-rpg` · `chalkboard` · `brick-toy`.
4. **העדכון דורס.** סקריפט ההתקנה מעדכן את הספרייה עם `git reset --hard` בכל הרצה. אל תשנו קבצים בתוך `~/lemo-opuscar` (issue #24 בריפו).
5. **Claude עלול לסרב להתקין.** הוא יכול לפרש את ההתקנה כהרצת קוד מרוחק. במקרה כזה מריצים את שתי פקודות ההתקנה בעצמכם, בטרמינל.
6. **שכבת הקריינות שולחת טקסט למיקרוסופט** (Edge TTS). הסרטים בריל שקטים, בלי קריינות.

## מה צריך

- Claude Code על מנוי Claude
- Node 20 ומעלה
- ffmpeg 7 ומעלה
- Python 3.11 ומעלה, או uv. במק, ה-python3 של המערכת (3.9) לא מספיק. `brew install uv` פותר את זה.

## התקנה, צעד אחרי צעד

1. בטרמינל:
```
claude plugin marketplace add lemomo-ai/lemo-opuscar
claude plugin install lemo-opuscar@lemolab
```
2. פותחים את Claude Code וכותבים:
```
/lemo-opuscar:lemo-opuscar
```
ואומרים לו איזה סגנון ועל מה.
3. בשימוש הראשון הוא מוריד את הספרייה ל-`~/lemo-opuscar` ומתקין חבילות npm, דפדפן headless וסביבת פייתון. בסך הכול כ-350MB.

**בלי הפלאגין:**
```
git clone https://github.com/lemomo-ai/lemo-opuscar.git
cd lemo-opuscar
claude
```

## הפרומפטים לעשרת הסגנונות מהריל

אלה הבריפים שהרצנו בפועל ב-8.11.26. מדביקים ב-Claude Code אחרי ההתקנה. הם באנגלית בכוונה, כי הסגנונות מכוילים לאנגלית. מחליפים את «a red open roadster» במה שאתם רוצים להראות.

**הבסיס, לכל אחד מהעשרה. מדביקים אותו, ומיד אחריו את שורת הסגנון:**
```
Use lemo-opuscar. Make a 5-second silent vertical clip, 1080x1920, 24fps.
Hero: one red two-seat open roadster (#D7261E), low and wedge-shaped, nose to the right, with two thrusters under the body.
Action: 0 to 0.8s the thrusters ignite and smoke builds · 0.8 to 3.2s it lifts off with smoke swelling below · 3.2 to 5s it hovers.
Framing: the car fills at least 80% of the width, car + thrusters + smoke at least 35% of the height, centred, no empty third.
Style:
```

1. **Pixel Art**
```
16-bit Pixel RPG (pixel-rpg). Add a rising ALT meter, a ROADSTER banner, a night skyline with a sunset, and a pixel crowd holding a WOW sign.
```
2. **Chalkboard**
```
Chalkboard (chalkboard). The board fills the frame. Title "Roadster 101", write "THRUST < WEIGHT", wipe it and rewrite "THRUST > WEIGHT" with a tick, a yellow THRUST arrow up and a pink WEIGHT arrow down, a stick figure saying "woah!", and a height graph that draws as it climbs.
```
3. **Glow Sketch**
```
A custom glow-sketch look (base: hologram-hud). The car is only a red dotted outline, no fill, on near-black, with warm gold light beams under it, dotted launch rings, a dotted stick-figure onlooker and a faint ROADSTER label.
```
4. **PS2**
```
A custom early-2000s console look (base: brick-toy three.js + lowpoly-island). Low-poly facets, low internal resolution, blur and haze, muted dusk sky, smeary window textures, an H helipad that stays readable, blocky onlookers fully inside the frame.
```
5. **Comic**
```
A custom pop-art comic look (base: halftone-dossier). Thick ink, Ben-Day dots, a jagged yellow "WHOOOSH!" burst, two panels with a surprised onlooker in the lower one.
```
6. **Flat Vector**
```
A custom flat vector look (base: midcentury-toon). Flat fills, a night-blue skyline, a big cream moon, confetti, cream smoke discs, orange flame jets, a crowd with phones up.
```
7. **Minimal Line**
```
A custom minimal white-line look (base: one-line). Thin white lines and dots on pure black, geometric construction circles the car rises into, a tiny stick figure, rows of dot lights at the bottom.
```
8. **CGI**
```
A custom premium CGI commercial look (base: glass-product + three.js). Glossy clearcoat paint, a window-lit night city with depth of field, a glowing blue ring pad, volumetric smoke, a soft blurred wet floor (no sharp second-car reflection).
```
9. **Lego**
```
Brick Toy (brick-toy). A brick-built roadster, a brick city behind, smoke made of round white bricks, minifig onlookers.
```
10. **3D Animation**
```
A custom soft animated-feature 3D look. Rounded toy-like car with satin paint, muted warm-grey haze, close camera, shallow depth of field, squash-and-stretch on lift-off.
```

**אם ב-Pixel Art הפריים יוצא שחור:** זה באג שמצאנו ברוחב אנכי. מבקשים מ-Claude לתקן את הפונקציה `mosaic()` כך שתעבוד גם ברוחב אי-זוגי.

## המספרים, עם תאריך

| | |
|---|---|
| כוכבים בגיטהאב | 13,605 (8.11.26) |
| סגנונות בספרייה | 66 (8.11.26) |
| רישיון | MIT לקוד · CC BY 4.0 לדמואים של הספרייה |
| זמן לקליפ של 5 שניות אצלנו | 4 עד 13 דקות (8.11.26) |

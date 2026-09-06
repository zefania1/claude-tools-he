# LTX-Video · מדריך התקנה

> נשלח למי שכתב **וידאו** בתגובות. כל מה שכאן **הורץ על מק M4 Pro עם 24GB**
> ב-27.8.2026 · לא הועתק מתיעוד.

## מה תקבלו

מודל וידאו של **לייטריקס** שרץ על המחשב שלכם. בלי חשבון, בלי מנוי, בלי מפתח API.
**רישיון:** חופשי לשימוש מסחרי לעסקים מתחת ל-**עשרה מיליון דולר** הכנסה שנתית.

## מה צריך

| | |
|---|---|
| מק | ‏Apple Silicon (‏M1 ומעלה) · **16GB מינימום, 24GB ומעלה נוח** |
| ווינדוס/לינוקס | כרטיס NVIDIA |
| מקום בדיסק | **‏27GB** למודל |
| זמן הורדה | פעם אחת. אצלי לקח כשעתיים |

## ההתקנה · ארבע פקודות

**1 · סביבה מבודדת** (‏`uv` · אם אין לכם, ‏`brew install uv`)

```bash
mkdir -p ~/ltx && cd ~/ltx && uv venv && source .venv/bin/activate
```

**2 · הספריות**

```bash
uv pip install torch diffusers transformers accelerate sentencepiece imageio-ffmpeg
```

**3 · סקריפט הייצור** · העתיקו לקובץ `gen.py`

```python
import torch
from diffusers import LTXPipeline
from diffusers.utils import export_to_video

pipe = LTXPipeline.from_pretrained("Lightricks/LTX-Video", torch_dtype=torch.bfloat16)
pipe.to("mps")   # מק. בווינדוס/לינוקס עם NVIDIA: "cuda"

prompt = "Abstract liquid chrome metal flowing in zero gravity, mirror-like reflective surface, dark background, macro lens, slow motion, cinematic"
negative = "worst quality, low resolution, blurry, deformed, watermark, text"

frames = pipe(prompt=prompt, negative_prompt=negative,
              width=896, height=512, num_frames=73,
              num_inference_steps=40,
              generator=torch.Generator().manual_seed(11)).frames[0]

export_to_video(frames, "out.mp4", fps=24)
```

**4 · הרצה** · ההורדה הראשונה קורית כאן, פעם אחת

```bash
python gen.py
```

## מה שכדאי לדעת לפני שתתאכזבו

**ההגדרות הן ההבדל.** ‏`704x416` ו-25 צעדים החזירו לי מריחה.
**‏`896x512` ו-40 צעדים החזירו רמת פרסומת.** אותו מודל, אותה מכונה.
**מחיר:** ‏~6 דקות לקליפ של 3 שניות על M4 Pro.

**במה הוא חזק:** אש · מתכת נוזלית · מים · אור · נוף · אווירה · אנשים מרחוק.
**במה הוא נכשל:** גרפים · חצים · מסכים · טקסט · חפץ מוגדר בקלוז-אפ.
*(הוא גם המציא לי לוגו של רשת שידור בפינת פריים. שווה להסתכל לפני שמשתמשים.)*

**לא כל שוט יוצא.** אצלי שניים מארבעה היו טובים. **אבל גלגול חוזר לא עולה כלום · וזה כל ההבדל מול ספרייה שמחייבת אותך על כל הורדה.**

## אותו זרע, אותו וידאו

```python
generator=torch.Generator().manual_seed(11)
```

שני ריצות עם אותו `seed` החזירו אצלי **‏sha256 זהה בייט-בבית**.
מי שבונה סדרה ורוצה שהרקע יהיה עקבי בין סרטונים · זו הסיבה.

## קישורים

- קוד: `github.com/Lightricks/LTX-Video`
- משקלים: `huggingface.co/Lightricks/LTX-Video`
- רישיון: `github.com/Lightricks/LTX-2/blob/main/LICENSE-2_x`

## אם נתקעתם

**‏"out of memory"** · הורידו ל-`width=704, height=416` ו-`num_frames=49`.
**‏"mps not available"** · אתם על מק ישן מדי, או שה-torch לא תומך. עדכנו torch.
**איטי מאוד** · זה תקין. זו המכונה שלכם ולא שרת.

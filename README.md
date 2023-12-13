 Final-Project
open source - fairpy


תקציר: בשנים האחרונות אונבריסטאות רבות אימצו שיטה לחלוקה הוגנת של מקומות בקורסים  בצורה אוטומטית ע"י אלגוריתם לפי שיטת הצעת מחיר. הצורה בה מתרגמים את הנקודות ללמערכת שעות לסטודנטים הוא דבר מוכר בספרות של מדעי המחשב ומאמר זה יובאו חמישה אלגוריתמים ומשווים ביניהם לפי קטגוריות: הוגנות, יעילות ותאימות.
ישנם תנאים שונים בין מצבי בחירת קורסים שונים לדוגמא: לפעמים הוגנות ויעילות יהיו חשובים יותר  מתאימות ולפעמים התאימות הוא החשוב ביותר וכדו. לכן יש להתאים את האלגוריתם הנכון לסיטואציה הנכונה.

 הקדמה:הקצאת קיבולת כיתה מועטה לסטודנטים היא תהליך מאתגר עבור אוניברסיטאות רבות כאשר מספר 
קורסים מסוימים חווים עודף ביקוש משמעותי.

ישנם שלושה מדדים:
מדדי יעילות הקצאה – לא ניתן לשפר את מצבו של אף תלמיד מבלי להחמיר מצבו של תלמיד אחר. 
מדדי הגינות – לוודא שסטיית התקן היא כמה שיותר נמוכה ופיזור משמעותי במספר הקורסים המוקצים לסטודנט.
מדדי תאימות – כדי לבדוק מדד זה כל סטודנט מקבל עבור כל קורס ערך פרטי וערך משותף.ככל שהערך הפרטי של סטודנט מתקדם לערך המשותף של אותו קורס יש לו יותר סיכוי לקבל את הקורס הזה.

האלגוריתמים שנעבוד איתם:
TTC)top trading-cycle( - אלגוריתם שעובד בשיטת סבב סבב ומחקה את אלגוריתם מחזור המסחר העליון
SP - אלגוריתם שמחקה את תיאוריית המכרזים כך שכל סטודנט מקבל מספר מסויים של נקודות וצריך לחלק איך שהוא רוצה בין 
 הקורסים ובכל סבב האלגוריתם יבצע כמין "מכירה פומבית" כך שמי ששם את מירב הנקודות על הקורס הוא יזכה בו.
 לכל אחת משיטות אלו יש גם את שיטת האופטימיזציה שלה בתוך הסבבים שמתמקדים יותר בהוגנות. נחקור את ההשפעה של האופטימזציה באמצעות סימולציה.
 OC - אלגוריתם שלא עובד בשיטת סבב סבב אלא מבצע אופטימיזציה על פני השוק כולו. אלגוריתם זה מתייחס לצורך בתועלת תוך אישית ולא רק הוגנות בין אישית. OC מתפקד היטב בתחומי יעילות והוגנות.

 בהמשך נדון בתוצאות הסימולציות המשוות בין חמשת האלגוריתמים הנ"ל לבין שתי שיטות נפוצות (Draft, BPM) תוך שימוש במדדי היעילות, הוגנות ותאימות.

 BPM - זהו אלגוריתם פשוט למדי בו כל סטודנט מחלק מספר נקודות לכל קורס , האלגוריתם מבצע רשימה של ההצעות לקורסים ומחלק לפי הסדר את הקורסים לסטודנטים (כמובן במידה ולוח הזמנים של הסטודנט לא מלא, הקורס לא מתנגש עם קורס אחר). 
 באלגוריתם זה נעשה שימוש (עם וריאצות קטנות )בבית ספר רבים. BPM מתמקדת רק במיקסום יעילות ההקצאה ואינה מתייחסת לשיוויון בין התלמידים. 
 Draft - אלגוריתם שעובד בשיטת סבב סבב, כך שכל סטודנט מחלק את הנקודות בין הקורסים הרצויים לו, האלגוריתם מבצע רשימה אקראית של הסטודנטים ומחלק להם את הקורס הרצוי ובכל סיבוב זוגי הסדר שלהם הפוך כן שמנגנון זה יותר הוגן מBPM אך עם זאת עדיין אין שיווין בין הסטודנטים כיון שהמנגנון לא מבחין בין העדפה קלה להעדפה כבדת משקל. 
 דיקטטורה סדרתית אקראית - אלגוריתם שמסדר את רשימת התלמידים באופן אקראי וכל סטודנט בתורו בוחר את כל חבילת הקורסים הרצויה עליו. אלגוריתם זה מונע לגמרי אסטרטגיות אבל אינו מתחשב כלל ביעילות והוגנות. בד"כ אלגוריתם זה משמש כבסיס ועליו נותנים שיפורים דרסטיים בהוגנות ויעילות.
 GS - מזכיר קצת את בBPM בכך שכל סטודנט מכין שתי רשימות אחת של סדר הקורסים ואחת של ניקוד לכל קורס. האלגוריתם יתחיל מהקורס שקיבל את הניקוד הגבוה ביותר וינסה להכניס את התלמיד לקורס הזה. אם הצליח, עובר לקורס עם הניקוד הגבוה הבא. אם לא, מעביר את הנקודות של הקורס לקורס הראשון ברשימת סדר הקורסים שעדיין הסטודנט לא השתבץ אליו. כך עד שהסטודנט משובץ לכל הקורסים שצריך. השיטה הזאת יותר יעילה מBPM אבל עלולה לגרום לסטודנטים להתנהג באסטרטגיות וגם, כמו שיטות נוספות, לגרום לכך שלחלק מהסטודנטים לא יוקצו מספיק קורסים
A-CEEI - אלגוריתם לא מובן שעובד בשיטת שיווי משקל תחרותי משוער ולא נראה שבשימוש כל כך 

לבעיית CAP (course allocation problem) נוספו בשנים האחרונות שני זרמי מחקר נוספים:
זרם ראשון - מתאר את הבעיה כדו צדדית כך שגם לקורסים יש העדפות (כגון רוצים את הסטודנטים עם הממוצע הכי גבוה) בפתרונות שקיימים לבעיה זו אין התייחסות לקורסים חופפים.
זרם שני - מסתכל על בעיית CAP בעיית היצע וביקוש.

אלגוריתם חדש לבעיית CAP:
סימונים:
C{1...m} - קבוצת הקורסים (יש לנו m קורסים). קורס שקיים בזמנים שונים נחשב לכמה קורסים שונים.
j - יהיה בין 1 לm וייצג את המספר המתאר של הקורס
q - מספר המקומות המוקצים לקורס (q יהיה מסומן עם j  בקטן כדי לסמן כמות המקומות לקורס j (
I{1...n} - קבוצת הסטודנטים שהוקצו לקורס j
k - כל סטודנט יכול לקחת k קורסים במסטר
Uij - כמות התועלת שמביא קורס j לסטודנט i
bij - הצעת המחיר של סודנט i לקורס j (לבדוק מה ההבדל בין זה לבין u). סך כל הצעות מחיר של סטודנט i לכל הקורסים חייב להיות קטן שווה לאלף.
rij - מארגן אוטומטית את רשימת הקורסים( לפי b) בסדר יורד כך ש:
∀j, j': rij ≤ rij’ ⇔bij ≤ bij’
Si - חבילת קורסים מותאמת לסטודנט i כך שאין חפיפות בין הקורסים והחבילה מכילה לכל היותר k קורסים - עדיין לא ידוע מתי נוצרת החבילה.
xij - משתנה בינארי כך שהוא 1 אם סטודנט i קיבל את קורס j ו0 אחרת.
Ojj' - משתנה בינארי כך שהוא 1 כאשר יש חפיפה בין קורסים או שמדובר באותו קורס בזמנים שונים. יש אפשרות להגדיר משתנה זה כטרנזטיבי (לא תמיד זה יהיה נכון לכן יש אפשרות ולא בהכרח)
t - אינדקס הסבב )כך שלדוגמא Xijt יהיה 1 במידה וסטודנט i קיבל את קורס j בסבב t)
Eit - קבוצת כל הקורסים הזמינים לסטודנט i בסבב t (זמינים=שם עליהם מחיר וגם יש להם מקומות) בכל סבב הקבוצה משתנה בהתאם
pjt - המחיר של הקורס j בסבב t

אלגוריתם TTC: כל סטודנט מציע הצעה על כל קורס בתקציב מסויים (עד 1000). כל סטודנט "מצביע" על הקורס שהוא הביא לו את ההצעה הגבוה ביותר (מתוך קבוצת הקורסים הזמינים עבורו). כל קורס ניתן לעד  qjt סטודנטים שהציעו את הסכום הגבוה ביותר עבור הקורס ומצביעים עליו. בסוף הסבב מקומות הקורסים מתעדכנים לפי כמות הקורסים שהוא הביא ולכל סטודנט משתנה קבוצת הקורסים הזמינה כרגע בצורה הבאה - מתוך קבוצת הקורסים שהיתה זמינה בסבב t יורד הקורס שהוא הצביע עליו בסבב t (גם אם הוא לא קיבל אותו) אם הוא קיבל את הקורס אז יורדים כל הקורסים שחופפים לקורס שהוא קיבל (לפי הOjj') ויורדים כל הקורסים שנגמר בהם המקום. בכל סיבוב, כל עוד יש סטודנטים שנדחו ולא קיבלו את הקורס שהצביעו עליו, הוא מבצע רק איתם עוד סבב עד שכולם קיבלו קורס בסבב הנוכחי או שאין לאף סטודנט קורס בEit. בשלב הבא הוא יבצע שוב סבב עם כולם עד שכל הסטודנטים קיבלו k קורסים.
Total cardinal utility - הסכום הכולל שהסטודנט הציע על הקורסים שקיבל
Total ordinal utility - סכום המקומות ברשימה של הקורסים שקיבל (הכי פחות שהוא רוצה זה 1)
Total binary utility - כמה קורסים קיבל הסטודנט


open source - fairpy
----


מבוא: בשנים האחרונות אונבריסטאות רבות אימצו שיטה לחלוקה הוגנת של מקומות בקורסים  בצורה אוטומטית ע"י אלגוריתם לפי שיטת הצעת מחיר. הצורה בה מתרגמים את הנקודות למערכת שעות לסטודנטים הוא דבר מוכר בספרות של מדעי המחשב ובמאמר זה יובאו חמישה אלגוריתמים ונשווה ביניהם לפי קטגוריות: יעילות, הוגנות ותאימות תמריצים .

מדדי יעילות הקצאה – כמות הקורסים שחולקו לסטודנטים. לא ניתן לשפר את מצבו של אף סטודנט מבלי להחמיר מצבו של סטודנט אחר.\
מדדי הגינות – לוודא שאין הפרשי תועלת גדולים בין הסטודנטים.\
מדדי תאימות תמריצים– עד כמה דירוג אסטרטגי הוא בעל השפעה גם בקרב הסטודנטים האסטרטגים וגם בקרב הסטודנטים דוברי האמת.

ישנם תנאים שונים בין מצבי בחירת קורסים שונים לדוגמא: לפעמים הוגנות ויעילות יהיו חשובים יותר  מתאימות תמריצים ולפעמים תאימות תמריצים יהיה חשוב יותר וכדו. לכן יש להתאים את האלגוריתם הנכון לסיטואציה הנכונה.

האלגוריתמים שנעבוד איתם:\
TTC (top trading-cycle) וSP (Second Price) הם אלגוריתמים שעובדים בשיטת המכרז. כך שכל סטודנט מקבל מספר מסויים של נקודות וצריך לחלק איך שהוא רוצה בין 
 הקורסים ובכל סבב האלגוריתם יבצע כמין "מכירה פומבית" כך שמי ששם את מירב הנקודות על הקורס הוא יזכה בו.\
 לכל אחת משיטות אלו יש גם את שיטת האופטימיזציה שלה בתוך הסבבים שמתמקדים יותר בהוגנות. נחקור את ההשפעה של האופטימזציה באמצעות סימולציה.\
 OC - אלגוריתם שלא עובד בשיטת סבב סבב אלא מבצע אופטימיזציה על פני השוק כולו. מתפקד היטב בתחומי יעילות והוגנות.

 בהמשך נדון בתוצאות הסימולציות המשוות בין חמשת האלגוריתמים הנ"ל לבין שתי שיטות נפוצות (Draft, BPM) תוך שימוש במדדי היעילות, הוגנות ותאימות תמריצים.

 BPM (bidding point mechanism) - אלגוריתם בו כל סטודנט מביא נקודות לכל קורס(הרבה נק לקורסים שהוא יותר רוצה, פחות נקודות לקורסים שהוא פחות רוצה). האלגוריתם מכין רשימה ממויינת לפי הנקודות שהסטודנטים הביאו כך שסטודנט שהביא הכי הרבה נק לקורס מסויים הוא יהיה הראשון ברשימה. האלגוריתם עובר לפי הרשימה ומחלק לסטודנט שהציע את מירב הנקודות לקורס כלשהו את הקורס (כמובן אם נשאר מקום בקורס.) נראה בהמשך (בגרפים) שאלגוריתם זה גרוע יחסית לשאר האלגוריתמים ברוב המדדים
 
 Draft - אלגוריתם שעובד בשיטת סבב סבב, כך שכל סטודנט מחלק את הנקודות בין הקורסים הרצויים לו, האלגוריתם מבצע רשימה אקראית של הסטודנטים ומחלק להם את הקורס הרצוי ובכל סיבוב זוגי הסדר שלהם הפוך כך שמנגנון זה יותר הוגן מBPM אך עם זאת עדיין אין שיווין בין הסטודנטים כיון שהמנגנון לא מבחין בין העדפה קלה להעדפה כבדת משקל. 
 
 דיקטטורה סדרתית אקראית - אלגוריתם שמסדר את רשימת התלמידים באופן אקראי וכל סטודנט בתורו מקבל מהאלגוריתם את כל חבילת הקורסים הרצויה עליו. אלגוריתם זה מונע לגמרי אסטרטגיות אבל אינו מתחשב כלל ביעילות והוגנות. בד"כ אלגוריתם זה משמש כבסיס ועליו נותנים שיפורים דרסטיים בהוגנות ויעילות.
 
GS (Gale–Shapley) - כל סטודנט מכין שתי רשימות אחת של סדר הקורסים ואחת של ניקוד לכל קורס. (שתי הרשימות לא בהכרח חייבות להיות מתאימות). באלגוריתם, כל סטודנט מצביע על הקורס הכי גבוה (שהוא עוד לא קיבל ויש בו מקום) ברשימת סדר הקורסים. האלגוריתם מחלק מקומות ישיבה (לפי כמות המקומות שיש לו) לסטודנטים שהציעו את ההצעות הגבוהות ביותר. אם שתי הרשימות מתאימות ביניהן האלגוריתם יתן אותה תוצאה כמו BPM.\ 
אלגוריתם זה מעודד התנהגות אסטרטגית ולכן לא נשתמש בו במאמר.



לבעיית CAP (course allocation problem) נוספו בשנים האחרונות שני זרמי מחקר נוספים:
זרם ראשון - מתאר את הבעיה כדו צדדית כך שגם לקורסים יש העדפות (כגון רוצים את הסטודנטים עם הממוצע הכי גבוה) בפתרונות שקיימים לבעיה זו אין התייחסות לקורסים חופפים.\
זרם שני - מסתכל על בעיית CAP בעיית היצע וביקוש. במאמר זה נתייחס לבעיה לפי הזרם השני.

סימונים:\
C{1...m} - קבוצת הקורסים (יש לנו m קורסים). קורס שקיים בזמנים שונים נחשב לכמה קורסים שונים.\
j - יהיה בין 1 לm וייצג את המספר המתאר של הקורס\
q - מספר המקומות המוקצים לקורס (q יהיה מסומן עם j  בקטן כדי לסמן כמות המקומות לקורס j)\
I{1...n} - קבוצת הסטודנטים שהוקצו לקורס j\
k - כל סטודנט יכול לקחת k קורסים בסמסטר (במאמר הk הוא קבוע, במימוש נצטרך למצוא פתרון לk  משתנה)\
Uij - כמות התועלת שמביא קורס j לסטודנט i\
bij - הצעת המחיר של סודנט i לקורס j .סך כל הצעות מחיר של סטודנט i לכל הקורסים חייב להיות קטן שווה לכמות מוסכמת מראש (בד"כ אלף).\
rij - מארגן אוטומטית את רשימת הקורסים( לפי b) בסדר יורד כך ש:\
∀j, j': rij ≤ rij’ ⇔bij ≤ bij’\
Si - חבילת קורסים מותאמת לסטודנט i כך שאין חפיפות בין הקורסים והחבילה מכילה לכל היותר k קורסים.\
xij - משתנה בינארי כך שהוא 1 אם סטודנט i קיבל את קורס j ו0 אחרת.\
Ojj' - משתנה בינארי כך שהוא 1 כאשר יש חפיפה בין קורסים או שמדובר באותו קורס בזמנים שונים. יש אפשרות להגדיר משתנה זה כטרנזטיבי (לא תמיד זה יהיה נכון לכן יש אפשרות ולא בהכרח)\
t - אינדקס הסבב )כך שלדוגמא Xijt יהיה 1 במידה וסטודנט i קיבל את קורס j בסבב t)\
Eit - קבוצת כל הקורסים הזמינים לסטודנט i בסבב t (זמינים=שם עליהם מחיר וגם יש להם מקומות) בכל סבב הקבוצה משתנה בהתאם\
pjt - המחיר של הקורס j בסבב t

Total cardinal utility - הסכום הכולל שהסטודנט הציע על הקורסים שקיבל\
Total ordinal utility - סכום המקומות ברשימה של הקורסים שקיבל (הכי פחות שהוא רוצה זה 1)\
Total binary utility - כמה קורסים קיבל הסטודנט

--------------------
האלגוריתמים איתם נעבוד:


אלגוריתם TTC: כל סטודנט מציע הצעה על כל קורס בתקציב מסויים (עד 1000). כל סטודנט "מצביע" על הקורס שהוא הביא לו את ההצעה הגבוה ביותר (מתוך קבוצת הקורסים הזמינים עבורו). כל קורס ניתן לעד  qjt סטודנטים שהציעו את הסכום הגבוה ביותר עבור הקורס ומצביעים עליו. בסוף הסבב מקומות הקורסים מתעדכנים לפי כמות הקורסים שהוא הביא ולכל סטודנט משתנה קבוצת הקורסים הזמינה כרגע בצורה הבאה - מתוך קבוצת הקורסים שהיתה זמינה בסבב t יורד הקורס שהוא הצביע עליו בסבב t (גם אם הוא לא קיבל אותו) אם הוא קיבל את הקורס אז יורדים כל הקורסים שחופפים לקורס שהוא קיבל (לפי הOjj') ויורדים כל הקורסים שנגמר בהם המקום. בכל סיבוב, כל עוד יש סטודנטים שנדחו ולא קיבלו את הקורס שהצביעו עליו, הוא מבצע רק איתם עוד סבב עד שכולם קיבלו קורס בסבב הנוכחי או שאין לאף סטודנט קורס בEit. בשלב הבא הוא יבצע שוב סבב עם כולם.

אלגוריתם SP: דומה מאד לאלגוריתם TTC אבל עם החזרי נקודות כך שבכל סיבוב כל סטודנט מצביע על הקורס הראשון ברשימת הקורסים הזמינים שלו. האלגוריתם יחלק את הקורסים לכל היותר לqjt סטודנטים שמציעים את הסכום הגבוה ביותר. במידה ויש מקום לכולם, הקורס היה "בחינם" והנקודות שהציעו עליו עוברות לקורס הבא ברשימה של כל סטודנט. במידה וללפחות אחד הסטודנטים לא היה מקום, מחיר הקורס יתעדכן לסכום הכי גבוה שהוצע מבין הצעות הסטודנטים שנדחו. הסטודנטים שכן היה להם מקום, ישלמו את המחיר החדש ואת שאר הנקודות יעבירו לקורס הבא ברשימה שלהם והסטודנטים שנדחו לא שילמו בכלל על הקורס וכל הנקודות של אותו סבב עוברות לקורס הבא ברשימה. בכל סיבוב, כל עוד יש סטודנטים שנדחו ולא קיבלו את הקורס שהצביעו עליו, הוא מבצע רק איתם עוד סבב עד שכולם קיבלו קורס בסבב הנוכחי או שאין לאף סטודנט קורס בEit. בשלב הבא הוא יבצע שוב סבב עם כולם.

TTC מול SP:\
מבחינת סכום כולל של קורסים ובחירת הקורסים הגבוהים ברשימה יותר ברשימה שני האלגוריתמים שווים.\
מבחינת ordinal fairness- עדיפות בSP\
מבחינת cardinal fairness - עדיפות בTTC

עד עכשיו TTC וגם SP עבדו בצורה חמדנית. עכשיו אנחנו מדברים על אופטימיזציה לאלגוריתמים הנ"ל.\
בTTC-O: האלגוריתם עובד כמו TTC, בנוסף בכל סבב נבצע אופטימיזציה ע"י הגדרת פונקציית מטרה ואילוצים בצורה הבאה:
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/6e474f45-c132-47b7-a30b-6504503030e8)

בSP-O: שוב, האלגוריתם עובד כמו SP, בנוסף בכל סבב נבצע אופטימזציה ע"י הגדרת פונקציית מטרה ואילוצים בצורה הבאה:
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/35f43a3d-369e-48b8-8e85-5e796a1c2cd2)

נשים לב שבשביל לבצע את האופטמזציה של SP-O נצטרך תחילה לבצע את האופטימזציה של TTC-O.

אלגוריתם OC: אלגוריתם זה מבצע אופטמזציה על TTC-O וSP-O באופן גורף ולא סבב סבב ע"י הגדרת פונקציית מטרה ואילוצים בצורה הבאה:
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/cb638dc3-7a6c-4323-9050-dc55d7080323)
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/1e22cfb4-18d6-4c72-abdd-9abd039ddb54)

-----------------------------------
סימולציות והשוואות:
מריצים את הסימולציה 100 פעמים.\
כל אחד מהסימולציות מכיל 900 סטודנטים.\
בכל אחד יש 83 קורסים זמינים.\
וסה"כ 112 הופעות של קורסים (יש 19 קורסים שחוזרים על עצמם כמה פעמים).\
כמות המקומות בכל קורס בכל סימלציה הוגרלו כך: 10%, 30% ו-60% מכמות מופעי הקורסים התפלגו אחיד עם הסתברויות של {15, 25, 35}, {40, 50, 60} ו-{70, 80, 90, 100}, בהתאמה. (יוצא בממוצע קצת מעל 5400 מקומות, מה שאומר שככל הנראה כמעט תמיד יהיה מקום לכל סטודנט ל6 קורסים)\
כל סטודנט יכול לקבל עד 6 קורסים.\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/e4942760-aec5-4ea4-bcd9-4983d5ed1385)\
בגרף מוצג ממוצע הפספוסים של כל אלגוריתם. כמה מקומות מסך כמות המקומות שהסטודנטים היו אמורים לקבל (כמות סטודנטים * k) ולא קיבלו (יכול להיות שנשארו עוד מקומות בקורסים מסויימים אבל הסטודנט לא יכול לקחת אותם כי זה מתנגש לו במערכת).\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/202543ba-81dd-4d25-9847-4a5cb6c4d69b)\
ממוצע השונות של כמות הקורסים שקיבל כל סטודנט.\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/d68ac4ce-0cb9-4bf5-940e-a12200b1779d)\
הממוצע של סכום דירוגי הקורסים שהסטודנטים קיבלו (תועלת אורדינלית)\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/170b5ea0-8229-4637-ad92-94c168ebb0bd)\
הממוצע של הטווח בין הסטודנט בעל התועלת האורדינלית הכי נמוכה לסטודנט בעל התועלת האורדינלית הכי גבוהה.(ככל שההממוצע יהיה נמוך יותר נדע שהאלגוריתם הוגן יותר)\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/9d2027bd-3d68-4346-9e33-e294fcd7d2c3)\
ממוצע סטיות התקן של התועלת האורדילנית לפי אלגוריתם.\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/d0c01da2-5f9a-456e-aa03-e1b37b64920e)\
ממוצע של סכומי התועלת הקרדינלית (סכומי הb). ככל שיהיה יותר גבוה כנראה הסטודנט קיבל את הקורסים שהוא יותר מעדיף (כי הוא שם עליהם הרבה כסף). באיור זה ניתן לראות שOC וBPM הם המובילים\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/ba01f1c4-c622-40cb-92ea-860794b99305)\

הממוצע של הטווח בין הסטודנט בעל התועלת הקרדינלית הכי נמוכה לסטודנט בעל התועלת הקרדינלית הכי גבוהה.(ככל שההממוצע יהיה נמוך יותר נדע שהאלגוריתם הוגן יותר). כאן ניתן להבין איך BPM מוביל באיור 6, וזה ע"י לקיחת סכומים קרדינלים גבוהים מאד ונמוכים מאד כך שהממוצע יוצא טוב אבל ההוגנות ממש רעה.\
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/0c280bc2-5877-493f-9f1b-ef24de3003e8)\
ממוצע סטיות התקן של התועלת הקרדינלית לפי אלגוריתם.\

-----------------------------------
עד כאן בדקנו מה קורה בכל אלגוריתם במידה והסטודנטים לא מפעילים אסטרטגיות, זאת אומרת מכניסים מחירים בדיוק לפי כמה שהם רוצים קורס מסוים.\
בחלק זה נבדוק איך עובד כל אלגוריתם במידה והסטודנטים כן מכניסים אסטרטגיות.\
נגדיר שלושה משתנים חדשים\
CVj - התועלת המשותפת של כל קורס\
P - אחוז הסטודנטים האסטרטגיים. נגדיר אותו לקבל רק 5 אפשרויות (מלבד 0 כאשר אין אסטרטגיים) 20%,40%,60%,80%,100%\
wi - מספר בין 0-1 שמשוייך לכל סטודנט, המצביע על כמה הוא אסטרטגי. כך שמי שמעל wiמסוים שנבחר, הוא אסטרטגי. גם כאן נגדיר רק חמש אופציות (0.6,0.7,0.8,0.9,1) \
ככל שWi גדל, זה אומר שהסטודנט חילק את הנקודות שלו לפי הערך המשותף ופחות לפי הערך האישי כך שאם wi=0.5 זה אומר שהערך המשותף לא עניין אותו בכלל והוא שם נקודות בדיוק לפי הערך האישי(הסטודנט לא היה אסטרטג כלל).
כעת יהיו לנו 25 נסיונות (5 של P כפול 5 של wi):
P=20%
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/c8725358-1c18-498d-a284-395136e8f297)\
ניתן לראות שככל שה-wi גדלה (המעידה על השפעה אסטרטגית חזקה יותר), התועלת הממוצעת של תלמידים אסטרטגיים פוחתת בכל האלגוריתמים מלבד BPM.
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/3e83d158-3a45-4fe0-ac1c-606cc71de4e8)
התוצאות מראות ירידה בתועלת הסידורית לתלמידים דוברי אמת ברוב האלגוריתמים. המשמעות היא שבממוצע, סטודנטים אמיתיים מקבלים קורסים בדירוג נמוך יותר(ממה שהיו אמורים לקבל אם לא היו סטודנטים אסטרטגיים) חשוב לציין, ב-BPM, הירידה הזו בתועלת הסידורית לתלמידים דוברי אמת היא משמעותית יותר בהשוואה לאלגוריתמים אחרים.
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/2eb9795f-e6ca-45dc-a296-4b1b43c6d221)
שילוב של שני הגרפים שלמעלה, ניתן לראות את הפער בין השינויים בתועלת הסידורית עבור תלמידים אסטרטגיים ואמיתיים באלגוריתמים שונים.באלגוריתם BPM, תלמידים אסטרטגיים מרוויחים באופן משמעותי על ידי דיווח שגוי של העדפות, והתנהגותם האסטרטגית פוגעת בתלמידים דוברי אמת. באלגוריתמים כמו TTC-O, SP-O וdraft, ההבדל בין שינויי התועלת הסידוריים של תלמידים אסטרטגיים ואמיתיים קטן יותר מאשר באלגוריתמים אחרים.אלגוריתם OC מראה פער גדול יותר בין התועלת הסידורית לתלמידים אמיתיים ואסטרטגיים (לטובת דוברי האמת), אך פער זה קטן יחסית לTTC וSP.
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/8d666ec0-ac79-40d2-94ed-4baff1f03a69)
בכל המקרים, יש סטיות תקן גדולות יחסית, מה שמצביע על כך שסטייה מדברי אמת היא הצעה מסוכנת ללא קשר לאלגוריתם. המשמעות היא שבעוד שחלק מהתלמידים עשויים להפיק תועלת ממשחק אסטרטגי, אחרים עלולים לאבד תועלת, והתוצאות משתנות, כפי שמתבטא בסטיית התקן.

הגרפים למעלה הציגו מקרה בו P=20%, כעת נבדוק מה קורה אם p>20%.
במאמר מוצג P=80% את הממצאים לP=20%,60%,100% ניתן למצוא בנספח B (במאמר הם מוסיפים שכשאר ישנם 100% סטודנטים אסטרטגיים כולם יפסידו).
בשביל החישובים בגרפים הבאים נגדיר:
ΔOU_{str} - השינוי הממוצע בתועלת האורדינלית עבור סטודנטים אסטרטגיים.
ΔOU_{tr} - השינוי הממוצע בתועלת האורדינלית עבור סטודנטים דוברי אמת. 
כך ש:
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/c2b2fecc-4c7e-46b9-96da-ac155b3c3ffe)
את התוצאות ניתן לראות בגרפים הבאים:
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/17973724-0640-44d2-aef9-bf6123e73466)
ניתן לראות שרק באלגוריתם BPM יש יתרון משמעותי לסטודנטים אסטרטגיים ושאר האלגוריתמים די ניטרליים.

![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/f5ca23b7-7886-4a66-81f7-1f872c079d5e)
ניתן לראות שרק באלגוריתם BPM יש חסרון משמעותי לסטודנטים דוברי אמת.
![image](https://github.com/MoriyaEster/Final-Project/assets/120458205/619595e9-bb5f-45e2-b696-058a12291ede)
לפי הגרף הנ"ל ניתן לראות שבאופן כללי באלגוריתם BMP יש יתרון משמעותי למשחק אסטרטגי, שאר האלגוריתמים ובמיוחד הOC מראים שאין כ"כ השפעה על התנהגת אסטרטגית והטיפה השפעה אין לדעת אם תהיה לרעת או לטובת האסטרטג ולכן בשימוש באלגוריתם OC הממלצה היא לבחור קורסים ללא אסטרטגיות.

-----------------
סיכום ומסקנות
-
במאמר הוצגו חמש וריאציות של אלגוריתמים ( TTC, SP, TTC-O, SP-O, OC) שהושוו למול שני אלגוריתמים ידועים (draft, BPM) במדדי הוגנות, יעילות ותאימות תמריצים. המדדים לוקחים בחשבון סך (או ממוצע), טווח וסטיית תקן של תועלת בינארית, אורדינל וקרדינלית.

מדד יעילות - ה-OC שולט, TTC וSP הרחק מאחור.
מדד הוגנות - ה-OC שולט, במיוחד ביעילות בינארית וסדרתית.
מדד תאימות תמריצים - בדרך כלל, כל האלגוריתמים, למעט BPM, מספקים תועלת מועטה מאוד לאסטרטגיה, כשהסיכונים עולים על התועלת הפוטנציאלית.

לסיכום:\
האלגוריתמם הכי פחות טוב - BPM. ולכן בהשוואה של שאר האלגוריתמים OC בולט כאלגוריתם הטוב ביותר אלא אם כן הצורך באלגוריתם שלא יתחשב באסטרטגיה עולה על הצורך בהוגנות ויעילות, נבחר בTTC-O וSP-O 














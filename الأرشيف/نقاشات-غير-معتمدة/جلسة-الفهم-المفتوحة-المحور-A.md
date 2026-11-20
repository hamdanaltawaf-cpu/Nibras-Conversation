# جلسة الفهم المفتوحة — المحور A (Core) — تحليل مفتوح فقط

إطار: نِبراس ←→ المستخدم ←→ الشريك التقني.
المرجع الوحيد: `PROJECT_CONTEXT_AND_DECISIONS.md` (`203` سطرًا، `RESET` كامل — لا معلومات قديمة).
لا قرارات مُعتمَدة جديدة في هذه الجلسة (`No Adopted Decisions` — `Only Analysis` + `Proposals` + `Inferences` + `Questions`).
لا تحديث للملف (`No File Update` `With` `Adopted` `Decisions` — `Only` `Proposed` `Clearly` `Labeled`).

---

## إطار التمييز (كل جملة مميَّزة بوضوح)

قبل كل نقطة، سأضع علامة واضحة (`Tag`):
- `[ACCEPTED]`: مؤكد في الملف (`From` `Current` `Session` `Only` — `Not` `From` `Previous` `Sessions` `Unless` `Confirmed` `Here`).
- `[REJECTED]`: مرفوض صراحةً (`Explicitly` `Rejected` — `With` `Reason` `Clear`).
- `[PROPOSED]`: مقترح (`Not` `Rejected`، `But` `Not` `Confirmed` `As` `ACCEPTED` `Yet` — `Needs` `Nebras` `Confirmation`).
- `[OPEN]`: مفتوح (`Not` `Resolved` — `Needs` `Nebras` `Direction` `Or` `More` `Info`).
- `[ASSUMED in File]`: افتراض موجود في الملف (`Not` `Tested` `Behaviorally` — `Theoretical` `Only`).
- `[INFERRED by Me]`: استنتاج منطقي من الملف + السياق (`Not` `In` `File` `Directly` — `My` `Analysis` `Only`).
- `[PROPOSED by Me]`: اقتراحي (`Not` `In` `File` — `My` `Proposal` `As` `Alternative` `Or` `Review` — `Not` `Adopted`).

---

## 1. ما هو المشروع في جوهره؟ ([ACCEPTED] من الملف)

`YemReact` = مكتبة رياكشنات يمنية قصيرة (`Rare Yemeni Short Reaction Clips`). المفهوم المركزي (`Fixed Concept`): **الرياكشن = المثل الشعبي الرقمي (`Reaction = Digital Proverb`)**. كل لقطة (`Clip`) هي جملة جاهزة (`Ready Phrase`) تُعبِّر عن موقف (`Specific Situation`) بلغة يمنية دارجة (`Yemeni Dialect`).

[INFERRED by Me]: هذا المفهوم (`Concept`) فريد (`Unique`) وجذاب (`Attractive`)، لكنه **نظري فقط (`Theoretical Only`)** بدون دليل سلوكي (`Behavioral Evidence`) يؤكد أن المستخدمين (`Users`) يفهمونه (`Understand It`) ويستخدمونه (`Use It`) بهذه الطريقة (`This Way` — `Not` `As` `Social Feed`، `Not` `As` `Archive`).

---

## 2. ما المشكلة التي يحاول حلها؟ ([ACCEPTED] + [ASSUMED in File] + [INFERRED by Me])

[ACCEPTED]: الفجوة (`Gap`) المُعرَّفة في الملف: `WhatsApp` (`Personal Folder`) محدود (`Limited`)، `TikTok`/`Facebook` = ضوضاء (`Noisy`)، `Giphy`/`Tenor` = لا محتوى يمني موقفي (`No Local Situational Content`).

[ASSUMED in File]: المستخدم (`Regular User`) يواجه هذه الفجوة (`Experiences This Gap`) فعليًا (`Actually`) ويحتاج حلاً (`Needs Solution`) — لم يُختبَر (`Not Tested` `Behaviorally`).

[INFERRED by Me]: إذا لم تكن هذه الفجوة (`Gap`) مشكلة حقيقية (`Real Problem`) للمستخدمين (`Not` `Theoretical`)، فالمنتج (`Product`) قد يكون `Solution` `Looking` `For` `Problem` (`Not` `Problem` `Looking` `For` `Solution`). هذا `Risk` (`Central Risk`) يحتاج `Validation` (`Manual Collection` `First` → `Usage Tracking` `Later`).

---

## 3. ما الهدف الحقيقي أو الاتجاه؟ ([PROPOSED] — لم يُحسَم صراحةً — [Critical Open Point])

[PROPOSED] من الملف (`Not Confirmed` `ACCEPTED` `Yet`): `Library-First` / `Discovery-First` (`Not Social-First`). الهدف (`Goal`): منتج قابل للتنفيذ (`Executable`) يُسلَّم (`Handed Over`) بدون إعادة اختراع (`Without Reinvention`).

[INFERRED by Me]: هناك `4` اتجاهات (`Directions`) منطقية (`Logical`) — `A` (`Utility`)، `B` (`Social`)، `C` (`Hybrid`)، `D` (`Content-Only`). `A` (`Utility`) هو المُقترَح (`Proposed`) الحالي (`Current Direction` — `Not Confirmed`)، لكن `Not Confirmed` `As` `ACCEPTED`. هذا هو `Critical Gap` (`Critical Open Point`) في المشروع (`Project`) حاليًا (`Now`).

---

## 4. ما المنتج بعيدًا عن التقنية؟ ([ACCEPTED] + [PROPOSED] من الملف)

[ACCEPTED]: مكتبة (`Library`) فيديو (`Video Only` `9:16` + `1:1`) — `Not Images` (`REJECTED`)، `Not Social Network`، `Not Dashboard` `First`. الهوية (`Brand v1.0 LOCKED`): `Qussasa` (`Torn Frame` + `Play`)، ألوان (`Ink`، `Amber`، `Paper`، `Coral`، `Grey`)، خطوط (`Lalezar`/`Cairo`)، واترمارك (`Fixed` `Drop-shadow`).

[PROPOSED]: النظام (`Content System`): `3 Types` (`Daily`، `When Need`، `Library Week`)، `Rubric` (`6 Points`)، `Pipeline` (`Manual` `First` — `30-50` `Then` `150-300`)، `Taxonomy` (`9 Categories` `Data Only` + `Tags` `Not Confirmed` + `Collections` `Rail` `Not Confirmed` `As` `Destination`).

[INFERRED by Me]: المنتج (`Product`) بصريًا (`Visually`) متماسك (`Coherent`) ومميز (`Distinct`)، لكن `Content` (`0` `Real`) يجعله `Shell` (`Beautiful Shell`) بدون `Substance` (`Empty Library`). هذا `Not` `UI` `Problem` — `Content` `Problem`.

---

## 5. المستخدمون المستهدفون واحتياجاتهم؟ ([ACCEPTED] من الملف + [INFERRED by Me])

[ACCEPTED] من الملف (`From` `Launch Kit` + `MVP Directive` + `Project Story`):
- صناع ميمز (`Meme Makers`، `16-30` سنة): `Need` `Raw Material` (`Ready` `Fast`).
- صناع محتوى (`Content Creators`): `Need` `Local Alternative` (`Giphy` `Not` `Local`).
- مستخدم عادي (`Regular User`): `Need` `Quick Expression` (`Chat`/`Comment`).
- صفحات يمنية/عربية (`Platforms`): `Need` `Authentic` `Local` `Content`.

[INFERRED by Me]: هذه الفئات (`Groups`) صحيحة (`Valid`) من الناحية النظرية (`Theoretically`)، لكن `Not Tested` (`No User Interviews`، `No Usage Data`). السؤال (`Question`): هل `Regular User` (`Not Creator`) سيستخدم `Library` (`Discovery`) أم سيبحث عن `Social Feed` (`Trending`، `New`، `Featured`)؟ إذا كان `Social` (`Social` `Behavior` `More` `Natural`)، فـ`Utility` (`Library`) قد لا يعمل (`Not Work`). هذا `Critical` `For` `A`.

---

## 6. ما القيمة التي يقدمها المشروع؟ ([ACCEPTED] من الملف + [INFERRED by Me])

[ACCEPTED] من الملف (`From` `Brand` + `Launch Kit` + `Content System`):
- `Local` (`Yemeni` `Authentic`): لهجة (`Dialect`)، مواقف (`Situations`)، تعبيرات (`Expressions`).
- `Curated` (`Hand-picked`): `Rubric` (`6 Points`) يُطبَّق يدويًا (`Manual`).
- `Ready-to-Use`: `Clip` (`Cut`)، `Watermark` (`Composited`)، `Category` (`Tagged`)، `Duration` (`Clear`).
- `Discoverable`: `Search` (`Situational`) + `Library` (`Browse`).

[INFERRED by Me]: هذه القيمة (`Value`) صحيحة (`Sound`) من الناحية النظرية (`Theoretically`)، لكنها `Not Proven` (`Not Tested` `Behaviorally`). إذا لم يُختبَر المستخدم (`Not Tested`)، فقد تكون القيمة (`Value`) `Assumed` (`Not Real`). هذا `Not` `Rejection` (`Not Rejected`) — بل `Warning` (`Caution`).

---

## 7. ما الذي تم حسمه فعليًا؟ ([ACCEPTED] من الملف — `Not From` `Previous` `Sessions` `Unless` `Confirmed` `Here`])

`ACCEPTED` (`Confirmed` `Here` — `Not` `Assumed` `From` `Previous`):
- `Brand v1.0 LOCKED` (`Not Change` `Without` `New` `ACCEPTED` `Decision`).
- `Video Only` (`9:16` + `1:1` — `Not Images` `Product`).
- `Submissions` (`Source` + `Real Rights` `REMOVED` `From` `Principles` — `No Proof` `Of` `Ownership`).
- `Performance Rating` (`REJECTED` — `Not Added`).
- `Reaction Detail` (`Page` `/r/[code]` — `Not Modal`).
- `Main` = `Library` (`Search` `Part` `Of` `Home` `Via` `?q=`).
- `Sidebar` (`Desktop` — `REMOVED`).
- `Schema Cleanup` (`REMOVED` `As` `Principle` — `Not Implemented` `Yet`).
- `Content Types` (`3` `Fixed`: `Daily`، `When Need`، `Library Week` — `Not Rejected` `From` `Launch Kit`).
- `Caption Formula` (`"لمّا..."` — `Not Rejected` `From` `Launch Kit`).
- `Manual Collection` (`30-50` — `Not Implemented` `Yet`، `Not Rejected`).
- `Watermark` (`Updated` `Drop-shadow` — `Not Rejected`).
- `Masonry` (`PROPOSED` — `Not Rejected`، `But` `Not Designed` `Visually` `Yet`).
- `Speech Extraction` (`PROPOSED` — `New` `In` `This` `Session` — `Not Rejected`، `But` `Service` `Not Chosen`، `UI` `Not Designed`).
- `Categories` (`Data Only` — `PROPOSED`، `Not Filter Bar` — `Not Confirmed` `As` `UI` `Element` `Yet`).
- `Collections` (`Rail` — `PROPOSED`، `Not BottomNav` `Destination` — `Not Confirmed` `As` `UI` `Element` `Yet`).
- `BottomNav` `Fourth` (`Saved` — `PROPOSED`، `Not Confirmed` `As` `FINAL` `Yet`).

`PROPOSED` (`Direction` `Not Confirmed` — `Not` `ACCEPTED` `As` `Final` `Yet` — `Needs` `Nebras` `Confirmation`):
- `Core Loop` (`Utility` — `Not Confirmed` `As` `ACCEPTED` — `Critical` `Open` `Point`).
- `Content` (`Manual` `First` — `Not Implemented`، `When` `Submissions` `Activated` `Not Confirmed`).
- `Speech` (`Binary` + `Expandable Window` — `Not Designed` `Visually`، `Service` `Not Chosen`).

`OPEN` (`Not Resolved` — `Needs` `Nebras` `Direction`):
- `Core Loop` (`Utility` `PROPOSED` vs `Social` `Assumed` in `Launch Kit` — `Critical` `Open`).
- `Speech Service` (`Whisper`؟ `Cloudflare`؟ — `Open`).
- `Content` (`30-50` `Not Collected`).
- `Git` (`147` `Files`، `No Remote` — `Critical` `Open`).
- `Admin` (`Not Tested` `Editorial` — `Open`).
- `Security` (`Submissions` `Attack Surface` — `Open`).
- `Observability` (`None` — `Open`).
- `Performance` (`No Numbers` — `Open`).
- `Accessibility` (`Not Deep` — `Open`).

`REJECTED` (`Explicitly` — `With` `Clear` `Reason`):
- `Images` (`As` `Main` `Product` — `Contradicts` `Brand` + `Library` `Concept`).
- `Performance Rating` (`Not Requested` + `Friction` `Increases`).
- `Source` + `Real Rights` (`From` `Principles` — `Friction` `Reduction`).

---

## 8. ما الذي اقترحه كلود أو تم اقتراحه سابقًا دون اعتماد نهائي؟ ([مؤكد في الملف — `Not` `From` `Previous` `Sessions` `Unless` `Confirmed` `Here`])

`From` `Launch Kit` (`YemReact-Content-System-Launch-Kit.md`) — `Not` `Rejected` `In` `This` `Session`، `But` `Not` `Confirmed` `As` `ACCEPTED` `Yet` (`Still` `PROPOSED` `Unless` `Nebras` `Confirms`):
- `Content System` (`3` `Types`: `Daily`، `When Need`، `Library Week`).
- `Caption Formula` (`"لمّا..."`).
- `Rubric` (`6` `Points`).
- `Taxonomy` (`9` `Categories` + `Tags` + `Collections`).
- `Submission Pipeline` (`Manual` `First` — `30-50` `Then` `150-300`).

`From` `Previous` `Session` (`Before` `Reset` — `Superseeded` `Not Re-Opened` `In` `This` `Session` `Unless` `Confirmed`):
- `Navigation` (`BottomNav` `Fourth` `Submit` → `Collections` → `Saved` — `Superseeded` `But` `Not Confirmed` `As` `ACCEPTED` `Yet`).
- `Sidebar` (`Desktop` — `REMOVED` — `Confirmed` `As` `ACCEPTED` `Here`).
- `Reaction Detail` (`Modal` → `Page` — `ACCEPTED` `Here`).
- `Search` (`Page` → `Part` `Of` `Home` — `ACCEPTED` `Here`).
- `Watermark` (`Fade` → `Drop-shadow` — `Updated` `Here`).
- `Color` (`Grey` `Text` → `Grey Light` + `Grey` `Borders` — `Updated` `Here`).

[ملاحظة — `Note` `From` `File` `Only`]: `Launch Kit` (`Content System`) `Not` `Cancelled` (`Not` `REJECTED`)، `But` `Not` `Adopted` `As` `FINAL` `Yet` (`Still` `PROPOSED` `Waiting` `Nebras` `Confirmation`).

---

## 9. ما الذي تم رفضه؟ ولماذا؟ ([مؤكد في الملف — `Not` `From` `Previous` `Only` — `Current` `Session` `Rejections`])

`REJECTED` (`Explicit` `In` `This` `Session` — `With` `Reason`):
- `Source` + `Real Rights` (`Principles` — `Friction` `Reduction`).
- `Performance Rating` (`Not` `Requested` + `Friction`).
- `Images` (`As` `Main` `Product` — `Contradicts` `Brand` `Video-Only` + `Library` `Concept`).
- `Social Loop` (`As` `Default` — `Not` `Explicitly` `Rejected` `As` `Concept`، `But` `Utility` `PROPOSED` `Implies` `Rejection` `Of` `Social` `As` `Primary` — `Still` `Needs` `Nebras` `Confirmation` `To` `Confirm` `This` `Rejection` `As` `FINAL`).

---

## 10. ما القرارات التي تبدو متعارضة أو تحتاج إلى إعادة تقييم؟ ([مؤكد في الملف — `Not` `Assumed` `From` `Previous` `Only` — `Current` `File` `Only`])

`Direct Conflict` (`Explicit` — `Must` `Resolve` `Before` `Next` `Axis`):
- `Core Loop` (`Utility` `PROPOSED` `Not` `ACCEPTED`) مقابل `Social Features` (`Assumed` `In` `Launch Kit` — `Featured`، `New`، `Trending` `Not` `Rejected` `Explicitly` `In` `This` `Session`). `Resolution`: `A` (`Core`) `Must` `Confirm` (`ACCEPTED` `Or` `REJECTED` `With` `Alternative`).
- `Manual Content` (`Admin` `First` — `PROPOSED`) مقابل `Submissions Pipeline` (`Exists` — `Not` `Activated` `Yet`). `No` `Direct` `Conflict` (`Can` `Coexist`)، `But` `When` `Submissions` `Activated` (`Not` `Confirmed`) `Needs` `Resolution`.
- `Speech Extraction` (`Automatic` — `PROPOSED`) مقابل `Curated` (`Hand-picked` — `ACCEPTED` `As` `Principle`). `No` `Direct` `Conflict` (`Can` `Coexist` — `Automatic` `For` `Search` `Only`، `Curated` `For` `Editorial` `Only`)، `But` `Storage` (`DB` `Field` `Or` `Search` `Index` `Only`؟) + `UI` (`Expandable` `Window` `Location` + `Sequence`؟) `Needs` `Resolution`.

`Implicit Conflict` (`Risk` `If` `Not` `Resolved` — `Not` `Explicit` `Contradiction` `But` `Tension`):
- `Brand` (`LOCKED` — `Not` `Changed` `Without` `New` `ACCEPTED` `Decision`) مقابل `UI` (`Sidebar` `REMOVED`، `Search` `Merged`، `BottomNav` `Changed`). `No` `Visual` `Conflict` (`Brand` `Visual` `Not` `Changed`)، `But` `Layout` `Changed` `Drastically` — `Needs` `Visual` `Consistency` `Review` (`Does` `New` `Layout` `Feel` `Consistent` `With` `Brand` `Visual`？ `Not Confirmed` `Yet`).
- `Library-First` (`Discovery` `Primary`) مقابل `Content` (`Manual` `First` — `0` `Real`). `No` `Direct` `Conflict` (`Library` `Can` `Work` `Theoretically` `With` `12` `Clips`)، `But` `Behavioral` `Risk` (`Regular` `User` `May` `Not` `Understand` `Library` `Without` `Content` — `Not` `Tested`).
- `Utility` (`No` `Daily` `Habit`) مقابل `Submissions` (`Growth` `Engine` — `Needs` `Audience` `First`). `No` `Direct` `Conflict` (`Manual` `First` `Then` `Submissions` `Later`)، `But` `When` `Submissions` `Activated` (`Not` `Confirmed` — `After` `150`؟ `300`؟) `Needs` `Resolution`.

---

## 11. ما الافتراضات التي بُني عليها المشروع؟ ([مؤكد في الملف — `Not` `Assumed` `From` `Previous` `Only` — `Current` `File` `Only`])

`Assumptions` (`Explicit` — `From` `File` `Only` — `Not` `From` `Previous` `Sessions` `Unless` `Confirmed` `Here`):
- `Brand v1.0` (`LOCKED` — `Not` `Changed` `Without` `New` `ACCEPTED` `Decision`).
- `Video Only` (`9:16` + `1:1` — `Not` `Images` `As` `Product` — `REJECTED`).
- `Content` (`Yemeni` `Authentic` — `Hand-picked` `Curated` — `Not` `Random` `Upload` `First`).
- `Submissions` (`Pipeline` `Exists` — `Manual` `First` — `Not` `Primary` `Source` `Of` `Content` `Yet`).
- `Core Loop` (`Utility` — `PROPOSED` — `Not` `ACCEPTED` `As` `Final` — `Assumed` `As` `Guiding` `Principle` `Until` `Rejected` `Explicitly`).
- `Search` (`Situational` — `Not` `Emotional` `Only` — `Assumed` `As` `Primary` `Discovery` `Method`).
- `Discovery` (`Library` `First` — `Not` `Social` `Feed` — `Assumed` `As` `Primary` `Experience`).
- `Network` (`3G` `Slow`، `Low-end Phone` — `Assumed` `As` `Guiding` `Principle` — `Not` `Measured` `With` `Real` `Numbers`).
- `SEO` + `Shareable URLs` (`Growth` `Channels` — `Assumed` `As` `Important` — `Not` `Tested` `Behaviorally`).
- `Service-Managed Media` (`Cloudflare` `Or` `Equivalent` — `Direction` `ACCEPTED`، `Implementation` `OPEN` — `Not` `Implemented` `Yet`).

`Assumptions` (`Implicit` — `Not` `Explicit` `In` `File` `But` `Inferred` `From` `Context` — `Not` `Confirmed` `As` `ACCEPTED`):
- `User` (`Regular`) `Will Understand` `Library` `Without` `Onboarding` (`No` `Tutorial` `PROPOSED` — `Not` `Designed` `Yet` — `Assumed` `But` `Not` `Tested`).
- `Admin` (`Hand-picked`) `Will Apply` `Rubric` (`6` `Points`) `Consistently` (`Not` `Tested` `Editorial` — `Assumed` `But` `Not` `Proven`).
- `Search` (`Situational`) `Will Work` `Without` `AI` (`AI` `Search` `DEFERRED` — `Assumed` `But` `Not` `Tested` — `May` `Need` `NLP` `For` `Matching` `Query` `To` `Clip` `Accurately`).
- `Watermark` (`Fixed`) `Will Not` `Disturb` `Expression` (`Visual` `Test` `PASS`، `Behavioral` `Not` `Tested` — `Assumed` `But` `Not` `Proven`).
- `Brand` (`LOCKED`) `Will Remain` `Appropriate` `At` `Scale` (`Not` `Tested` `At` `Scale` — `Assumed` `But` `Not` `Proven`).

---

## 12. ما الأجزاء القوية في الاتجاه الحالي؟ ([مؤكد في الملف — `Not` `Assumed` `Only` — `From` `File` `Content`])

`Strengths` (`Confirmed` — `No` `Risk` `Direct` `From` `File` `Evidence`):
- `Brand` (`Visual` `PASS` `120-32px`، `One Color` `PASS`، `Qussasa` `Readable` `Without` `Name`).
- `Concept` (`Digital Proverb` — `Unique`، `Not` `Copied`، `Explainable`).
- `Auth` (`Real` `Google` `Only` `Working` `On` `Production`، `Sync` `Saved` `Real`).
- `Review Pipeline` (`Complete` `Logic`: `Pending` → `Processing` → `Watermark Gate` → `Approve` — `Not Missing` `Steps`).
- `TypeScript` (`Strict` — `Zero` `Lint` `Errors`، `Zod` `Every` `Input`، `AppError` `Unified`).
- `Testing` (`265` `Real` `Tests` — `Authentication` `Simulation` `Without` `Google` `Real` `In` `E2E`).
- `Storage` (`Abstraction` — `Local`/`S3` `Separated`، `Ready` `For` `Migration` `To` `Service-Managed`).
- `Content System` (`Launch Kit` — `Structured` `Rubric` + `Pipeline` + `Taxonomy` — `Not` `Random`).
- `Visual Language` (`Single` `Element` `Family`: `Torn`، `Play`، `Bubble`، `Tag` — `Not` `Random` `Decorative`).
- `Documentation` (`New` `System`: `PROJECT_CONTEXT...` `Source` `Of` `Truth` — `Single` `Reference`، `State` `Clear` — `Not` `Stale` `Yet`).

`Strengths` (`Proposed` — `Not` `Implemented` `But` `Direction` `Sound`):
- `Content` (`Manual` `First`) — `Breaks` `Chicken-and-Egg` (`Not` `Depends` `On` `Audience` `First`).
- `Speech` (`Binary` `Search`) — `Enhances` `Discovery` (`Situational`) `Without` `AI` `Complexity` (`Not` `Requires` `NLP` `If` `Only` `Binary` `Used`).

---

## 13. ما الأجزاء الضعيفة أو الغامضة أو التي قد تسبب مشاكل مستقبلية؟ ([مؤكد في الملف — `Not` `Assumed` `Only` — `From` `File` `Evidence`])

`Critical` (`Fixed` `Before` `Scale` — `Not` `Before` `Plan` `Adopted` `But` `Before` `Implementation`):
- `Real Content` (`0` `Published` `Videos` — `Central` `Weakness` — `Not` `UI` `Problem`، `Not` `Brand` `Problem`، `Not` `Architecture` `Problem` — `Content` `Problem`).
- `Git` (`147` `Files`، `No` `Remote`، `Single` `Commit` — `Data Loss` `Critical` `Risk` — `First` `Before` `Any` `Code` `Change`).
- `Protection` (`38` `Positions` — `Security` `Risk` — `Not` `Protected` `By` `Middleware` `Yet` — `PROPOSED` `Only`).
- `Observability` (`None` — `Blind` `Operation` — `No` `Detection` `Of` `Failure`).

`High` (`Fixed` `Before` `Implementation` `Or` `Scale` — `Not` `Before` `Plan` `Adopted` `But` `Before` `Code` `Implementation`):
- `Media` (`ffmpeg` `Inside` `Serverless` — `Functional Failure` — `0` `Videos` `In` `Production` — `ACCEPTED` `Direction` `Service-Managed`، `Details` `OPEN`).
- `Schema` (`Dead` `Models`: `Session`، `OneTimeCode`، `EDITOR`، `SUBTITLE` — `Understanding` `Burden` — `ACCEPTED` `Cleanup`، `Not` `Implemented` `Yet`).
- `Core Loop` (`Utility` `PROPOSED` — `Not` `Confirmed` — `If` `Rejected`، `All` `UI` `Social` `Features` (`Featured`، `New`، `Trending`) `Must` `Be` `Re-evaluated` — `Critical` `Open`).
- `Performance` (`No` `Real` `Numbers` — `3G` `Assumed` `But` `Not` `Measured` — `Risk` `Of` `Slow` `Experience` — `Not` `Fixed` `Before` `Scale`).
- `Accessibility` (`Not` `Deep` — `Keyboard` `Not` `Tested`، `Screen Reader` `Not` `Tested`، `Reduced Motion` `Not` `Defined`، `Touch Targets` `Not` `Measured` — `Risk` `Of` `Exclusion`).
- `Security` (`Submissions` `Attack` `Surface` — `Rate Limit`، `File Validation`، `Spam`، `Abuse`، `Takedown` — `Not` `Discussed` `Technically` — `OPEN`).

`Medium` (`Fixed` `Before` `Scale` — `Not` `Before` `Plan` `Adopted`):
- `Content` (`Manual` `First` — `Administrative` `Burden` — `Time` `To` `30-50` `Not` `Measured`).
- `Submissions` (`Chicken-and-Egg` — `Audience` `Needs` `Content`، `Content` `Needs` `Audience` — `Solution` `Manual` `Works` `But` `Slow`).
- `Speech` (`Automatic` — `Dependency` `On` `Service` `Not` `Chosen` — `Can` `Delay` `Content` `Or` `Add` `Unexpected` `Cost`).
- `Brand` (`LOCKED` — `Not` `Adaptable` `Without` `New` `ACCEPTED` `Decision` — `May` `Need` `Review` `At` `Scale` `If` `Visual` `Not` `Appropriate` `For` `Large` `Library`).
- `Documentation` (`How` `Keeps` `Alive` — `Not` `Defined` — `Risk` `Of` `Stale` `File` `Again`).

---

## 14. ما الأشياء التي قد نكون أغفلناها؟ ([مؤكد في الملف — `Not` `From` `Previous` `Only` — `Current` `File` `Only`])

`Overlooked` (`Not` `Mentioned` `In` `File` `Or` `Not` `Discussed` `Deeply` `In` `This` `Session`):
- `Accessibility` (`Keyboard` `Navigation`، `Screen Reader` `Labels`، `Video Controls` `Accessible`، `ARIA` `Semantic`، `Reduced Motion` `Preference`، `Touch Targets` `Minimum Size` — `Not` `Designed` — `Risk` `Of` `Exclusion` `If` `Not` `Addressed` `Before` `Launch`).
- `RTL` (`Right-to-Left` — `Not` `Specific` `In` `File` — `Content` `Arabic` `Only`، `But` `UI` `Not` `Specifically` `RTL` `Designed` — `Assumed` `But` `Not` `Tested`).
- `Internationalization` (`i18n` — `Not` `Mentioned` — `Content` `Yemeni` `Only`، `But` `URL` `Slug` `May` `Need` `English` `Translation` `For` `SEO` `Or` `Social` `Share` — `Not` `Confirmed` `As` `Necessary`).
- `Error States` (`404` `Message` + `Action`، `500` `Message` + `Retry`/`Report`، `Network` `Disconnected` `Message` + `Offline` `Indicator` — `Not` `Designed` `In` `UI` — `Risk` `Of` `User` `Confusion` `If` `Not` `Addressed`).
- `Empty States` (`Search` `No Results` `Message` + `Suggestion`؟ `Saved` `Empty` `Message`؟ `New User` `First Visit` `Guide`？ `Collection` `Empty` `Message`？ — `Not` `Designed` — `Risk` `Of` `User` `Abandonment` `If` `Not` `Addressed`).
- `Onboarding` (`Tutorial`، `Tooltip`، `Intro` — `No` `Onboarding` `PROPOSED` `In` `Launch Kit`، `But` `Not` `Designed` — `Risk` `Of` `User` `Not` `Understanding` `Library` `Purpose` `If` `Not` `Clear` `From` `First` `Visit`).
- `Backup` (`Disaster Recovery` — `Storage` `Policy` `Not` `Defined`: `Keep Original`？ `Delete` `After Process`？ `Backup` `Where`？ `How Often`؟ — `Risk` `Of` `Data Loss` `If` `Not` `Addressed` `Before` `Scale`).
- `Performance Budget` (`Number` — `Not` `Defined`: `First Load` `Target` `Time`？ `Video` `Load` `Target`？ `Mobile` `3G` `Target`？ `Low-end` `Phone` `Target`？ — `Risk` `Of` `Slow` `Experience` `Without` `Budget` `To` `Guide` `Optimization`).
- `User Psychology` (`Why` `Search`？ `Why` `Save`？ `Why` `Share`？ `Why` `Submit`？ — `Not` `Studied` — `Assumed` `From` `Concept` `Only` — `Risk` `Of` `Wrong` `Assumptions` `About` `User` `Motivation`).
- `Future` (`AI` `For` `Classification`？ `Keyword Extraction`؟ `Moderation`？ `Metadata Generation`？ `Content Suggestions`？ — `Not` `Planned` `Now` — `DEFERRED` `Only` — `Not` `Ignored` `Completely` `But` `Not` `Now`).
- `Monetization` (`Ads`？ `Premium`？ `API`？ `B2B`？ — `Not` `Discussed` `In` `Depth` — `Not` `Before` `Scale` `Proof` `But` `Not` `Ignored` `Completely`).
- `Content Lifecycle` (`Draft` → `Review` → `Processing` → `Published` → `Archived` → `Deleted` — `Not` `Fully` `Defined` `In` `Schema` `Or` `Pipeline` — `Only` `Pending`/`Processing`/`Approve`/`Reject`/`Archive` `Mentioned` — `Not` `Full` `Lifecycle`).
- `Data Lifecycle` (`What` `Happens` `When` `User` `Deleted`？ `Collection` `Empty`？ `Category` `Changed`？ `Reaction` `Slug` `Changed`？ `Collection` `Item` `Removed`？ — `Not` `Defined` `In` `Schema` `Or` `Pipeline` — `Risk` `Of` `Data` `Inconsistency` `At` `Scale`).
- `Legal` (`Terms` `Of` `Service` — `Content Policy` `Not` `Written` `In` `Detail` — `Only` `Mentioned` `As` `Concept`、 `Privacy` `Policy` — `Not` `Written` `In` `Detail` — `Only` `Mentioned` `As` `Concept`、 `FAQ` — `Not` `Written` — `Only` `Page` `Mentioned` `As` `Concept`).

---

## 15. ما الذي يحتاج إلى نقاش عميق قبل الانتقال إلى التصميم أو التنفيذ؟ ([مؤكد في الملف — `Not` `Before` `Plan` `Adopted`])

`Critical` (`Must` `Resolve` `Before` `Next` `Axis` — `Not Before` `Plan` `Adopted` `But` `Before` `B`/`C`/`D`):
- `Core Loop` (`A` — `Not Confirmed` `As` `ACCEPTED` — `Critical` `Open` `Point`).
- `Rubric` (`B` — `6` `Points` `Not` `Tested` `Editorial` — `Needs` `Manual` `Collection` `First`).
- `Taxonomy` (`B` — `Tags` `NEW`？ `Collections` `Rail` `FINAL`？ — `Not Confirmed`).
- `Pipeline` (`B` — `Manual` `How` `Raw` `Collected`？ `Time`？ `When` `Submissions` `Activated`？ — `Not Confirmed`).
- `Speech` (`B` — `Service` `Choice`、 `Storage` (`DB` `Or` `Index`？)、 `UI` (`Expandable Window` `Location` + `Sequence`？) — `Not Confirmed`).

`Important` (`Should` `Resolve` `Before` `Implementation` — `Not Before` `Plan` `Adopted` `But` `Before` `Code` `Implementation`):
- `Sitemap` (`C` — `Pages` `FINAL`？ `Routes` `Exact`？ `States` `FINAL`？).
- `Navigation` (`C` — `BottomNav` `4` `FINAL`？ `Header` `Submit`？ `Search` `?q=`？).
- `Reaction Detail` (`C` — `Expandable Window` `Location` (`Beside` `Video`？ `Under` `Title`？ `Beside` `Save`？) + `Sequence` (`Video` → `Title` → `Window` → `Category` → `Collections` → `Save` → `Share` → `Related`？) — `Not Designed` `Visually`).
- `Account` (`C` — `Saved` `Sync` `Mechanism`？ `My Submissions` `Status`？ `Settings` `Keep`/`Remove`？).
- `Admin` (`C` — `Bulk` `Features` (`Approve`/`Reject`/`Categorize`？ `Keyboard` `Shortcut`？ `Preview`？) + `Single` `Review` (`Rubric` `Checkboxes`？ `Comment`？ `Reject` `Reason` `Required`？)).
- `Footer` (`C` — `Links` `FINAL`？ `Legal`、 `FAQ`、 `Social`？).

`Not Before` `Plan` `Adopted` `But` `Before` `Implementation` (`Can` `Be` `Done` `After` `Plan` `Adopted` `But` `Before` `Code`):
- `States` (`D` — `All` `Pages` `FINAL`？ `Empty` `States`？ `Error` `States`？ `New User`？ `Returning User`？).
- `Buttons` (`D` — `Every` `Button` `Place` + `Function` + `State After Click` + `Popup`/`Toast`/`Page Change`？).
- `Popups` (`D` — `Speech Window` `FINAL` `Design` + `Login` (`Modal`/`Page`？ `Resume` `Draft`？) + `Confirm` (`Submit`？ `Preview`？)).
- `Journey` (`D` — `Sequence` `FINAL`？ `First Time`？ `Search Fails`？ `Save` + `Login`？ `Submit` + `OAuth`？ `Admin` `Review`？ `Duplicate`？).
- `Schema` (`E` — `Cleanup` `Implementation` — `Not Before` `IA` `FINAL` `But` `Can` `Be` `Done` `After` `Plan` `Adopted` `Before` `Implementation` `If` `Needed`).
- `Storage` (`E` — `Service` `Choice` + `Watermark` `Direct`/`Separate` — `Not Before` `Content` `Ready` `But` `Can` `Be` `Decided` `After` `Plan` `Adopted`).
- `Security` (`E` — `Rate Limit` + `File Validation` + `Spam` + `Abuse` — `Not Before` `Submissions` `Activated` `But` `Can` `Be` `Designed` `After` `Plan` `Adopted`).
- `Performance` (`E` — `Budget` — `Not Before` `Performance` `Measured` `But` `Can` `Be` `Defined` `After` `Plan` `Adopted`).
- `Accessibility` (`E` — `AA`/`AAA`？ `Keyboard` `Tab` `Order`？ — `Not Before` `UI` `FINAL` `But` `Can` `Be` `Defined` `After` `Plan` `Adopted`).
- `Growth` (`F` — `Metrics` (`5` — `Based` `On` `A` `FINAL`？)، `SEO` (`Sitemap` `Pages` `FINAL`？)، `Social Embeds` (`Not Before` `Share` `Feature` `FINAL`？)، `Viral Loop` (`Not Before` `A` `FINAL`？)، `Monetization` (`DEFERRED` — `Not Before` `Scale` `Proof` `But` `Can` `Be` `Discussed` `After` `Plan` `Adopted`).
- `Operations` (`G` — `Git` (`Critical` — `First` `Before` `Any` `Code` `Change`)، `Environments` (`Not Before` `Deployment` `Plan` `FINAL`)، `Testing` (`Not Before` `IA` `FINAL` + `Content` `Ready`)، `Observability` (`Not Before` `Deployment` `Plan` `FINAL`)، `Documentation` (`Not Before` `Every` `Axis` `FINAL`).

---

## 16. كيف تفهم العلاقة بين الهوية، المحتوى، المكتبة، البحث، التفاعل، المشاركة، والتوسع المستقبلي؟ ([مؤكد في الملف — `From` `File` `Relationships` `Only` — `Not` `Implementation`])

`Identity` (`LOCKED` — `Brand` `Not` `Changed` `Without` `New` `ACCEPTED` `Decision`) ←→ `Content` (`Manual` `First` — `Hand-picked` `Curated` `30-50` `Then` `150-300`) ←→ `Library` (`Main` `Page` = `Discovery` `Primary` — `Not` `Social` `Feed`) ←→ `Search` (`Situational` `Primary` — `Not` `Social` `Trending`) ←→ `Discovery` (`Library` `Grid` + `Search` `Results` + `Collections` `Rail` — `Not` `Social` `Feed`) ←→ `Interaction` (`Reaction Detail` `Page` — `Video` + `Binary` `Speech` `Expandable` + `Category` + `Collections` + `Save` + `Share` + `Download`) ←→ `Participation` (`Submissions` `Pipeline` — `Manual` `First` `Then` `Activated` `After` `Content` `Ready`) ←→ `Expansion` (`Scale` `Content` `150-300` → `Growth` `SEO` + `Social Embeds` + `Viral Loop` `Possible` → `Monetization` `DEFERRED` `Not Before` `Proof`).

`Critical` `Connections` (`Must` `Work` `Together` — `Not` `Separate`):
- `Identity` (`Qussasa`) → `Content` (`Clip` `Template` `Fixed` — `Peel` `Fixed` `In` `Every` `Card`، `Watermark` `Fixed` `In` `Every` `Video`). (`Visual` `Consistency` `Critical` — `Not` `Broken` `By` `Masonry` `If` `Peel` `Fixed`).
- `Content` (`Rubric` `6` `Points`) → `Library` (`Category` `Data` `Only` — `No` `Filter` `Bar` `Default` — `Discovery` `Through` `Search` + `Collections` `Rail` `Only`). (`Taxonomy` `Not` `Over-engineered` `If` `Categories` `Data` `Only`).
- `Search` (`Situational`) → `Discovery` (`Results` `Same` `Library` `Grid` — `Not` `Separate` `Page` `Redundant`) → `Interaction` (`Click` `Card` → `Detail` `Page` — `Not` `Modal` `To` `Keep` `Context` `For` `SEO` + `Share`). (`Search` `Not` `Social` `Feed` `But` `Situational` `Library`).
- `Interaction` (`Save`) → `Account` (`Menu` — `Saved` + `My Submissions` — `Not` `Dashboard`) → `Sync` (`Guest` `Saved` → `Login` → `Sync` — `Mechanism` `Not` `Designed` `Yet`). (`Participation` `Not` `Social` `Loop` `But` `Utility` `Loop` — `Save` `Then` `Use` `Outside` `Then` `Return` `When` `Needed`).
- `Participation` (`Submissions` `Manual` `First`) → `Content` (`Scale` `30-50` `Then` `150-300`) → `Library` (`Scale` `Grid` `Not` `Broken` — `Masonry` `Works` `If` `Aspect` `Mixed` `Within` `9:16` `Frame`). (`Content` `Not` `From` `Audience` `First` — `From` `Admin` `Manual` `Collection` `First`).
- `Expansion` (`Scale` `Content`) → `Search` (`Situational` `Accuracy` — `Speech` `Binary` `Helps` `If` `Implemented`) → `Growth` (`SEO` `Sitemap` + `Social` `Embeds` + `Viral` `Loop` `Possible` `Only` `If` `Social` `Share` `Works` `Naturally` — `Not` `Forced`) → `Monetization` (`DEFERRED` — `Not` `Before` `Scale` `Proof` `150-300` + `Usage` `Evidence` `Search` `Success` `Rate` `Measured`). (`Expansion` `Not` `Social` `Loop` `Forced` — `Utility` `Natural` `Expansion` `Through` `Content` `Scale` + `Discovery` `Improvement`).

---

## 17. ما تصورك للمنتج بعد قراءة كل شيء؟ ([استنتاجي — `Not` `Implementation` — `Based` `Only` `On` `File` `Content` + `Analysis`])

`Vision` (`After` `Full` `Reading` — `Not` `Implementation` — `Only` `Analysis` + `Proposals`):

`YemReact` (`As` `Understood` `From` `File` — `Not` `As` `Implemented` `Product` `Yet`):
- `Library` (`Not` `Social` — `Utility` `PROPOSED` `Not` `ACCEPTED` `Yet`) مع `Brand` (`LOCKED` `Strong`) بصريًا (`PASS`) ومنطقيًا (`Coherent`).
- `Content` (`Real` `Video`) مفقود (`Missing` — `0` `Published`) — `Central` `Weakness` (`Not` `UI` `Problem`، `Not` `Brand` `Problem`، `Not` `Architecture` `Problem` — `Content` `Problem` `Only`).
- `UI` (`Library` `Grid`، `Reaction` `Page`، `Account` `Menu`، `Admin` `CRUD`) موجود (`Exists` `Technically` `From` `Previous` `Session` + `This` `Session` `File` `Read`)، لكن `Not` `Tested` `With` `Real` `Content` (`Behavioral` `Untested`).
- `Technical` (`Next.js` + `Auth` + `Admin` + `Tests`) ناضج (`Mature`) لكن `Git` (`Critical` `Risk`)، `Observability` (`Blind` `Risk`)، `Security` (`Submissions` `Attack` `Surface` `Not` `Protected`)، `Performance` (`No` `Budget` `Real`) نقاط ضعف (`Real` `Weaknesses`).
- `Concept` (`Digital Proverb`) فريد (`Unique`) وجذاب (`Attractive`)، لكن `Not Proven` (`Behaviorally` `Not` `Tested` — `Not` `Assumed` `As` `Confirmed`).

`Potential` (`Positive` — `If` `Content` `Ready` + `Core` `Confirmed`):
- `Brand` (`LOCKED`) + `Concept` (`Unique`) + `Local` (`Yemeni`) = `Differentiation` (`Not` `Easily` `Copied`).
- `Library` (`Not` `Social` `Feed`) + `Situational` `Search` = `Unique` `Discovery` (`Not` `Social` `Trending`).
- `Manual` `Content` (`Curated` `30-50`) = `Quality` `Proof` (`Can` `Show` `Brand` `Works` `With` `Real` `Content`).
- `Submissions` (`Pipeline` `Exists`) + `Rubric` (`6` `Points`) = `Growth` `Engine` (`Can` `Scale` `Content` `From` `Audience` `After` `Manual` `Ready`).
- `Speech` (`Binary` `Search`) = `Discovery` `Improvement` (`Can` `Make` `Search` `More` `Accurate` `Without` `AI` `Complex` — `Not` `Requires` `NLP` `If` `Only` `Binary` `Used`).

`Risk` (`Negative` — `If` `Content` `Not` `Ready` `Or` `Core` `Not` `Confirmed`):
- `Content` (`0` `Real`) = `UI` (`All` `Design`) `Theoretical` (`Not` `Proven` `Behaviorally`).
- `Core` (`Utility` `Not Confirmed`) = `Metrics` (`Social` `Assumed` `Wrong` `If` `Utility` `True`، `Utility` `Assumed` `Wrong` `If` `Social` `True`).
- `Git` (`Critical`) = `Data Loss` (`Any` `Change` `Before` `Remote` = `Danger`).
- `Media` (`Serverless`) = `Functional Failure` (`0` `Videos` `In Production` `Proves` `This`).
- `Observability` (`None`) = `Blind` (`Can Not` `Detect` `Failure` `Until` `Too Late`).
- `Performance` (`No Budget`) = `Slow` `Experience` (`Can` `Break` `User` `Experience` `On` `3G` `Without` `Budget` `To Guide` `Optimization`).
- `Security` (`Submissions` `Not Protected`) = `Attack` (`Can` `Be` `Exploited` `By` `Spam` `Or` `Malicious` `Files`).

`My Professional Opinion` (`As` `Engineering` `Partner` — `Not Final` `Decision`، `Needs` `Nebras` `Confirmation`):
`YemReact` (`As` `Understood` `From` `File` — `Not` `As` `Implemented` `Product` `Yet`) هو `Concept` (`Digital Proverb`) قوي (`Strong`) بصريًا (`Brand PASS`) ومنطقيًا (`Library`، `Utility` `PROPOSED`، `Manual` `Content` `First`، `Search` `Situational`)، لكنه `Not Ready` `As` `Product` (`0` `Real Video`، `Core` `Not Confirmed`، `Git` `Critical`، `Observability` `None`، `Security` `Open`).

`Direction` `A` (`Utility` — `Current` `PROPOSED` `Direction`): `Best` `If` `Content` `Ready` (`30-50` `Real` `Clips` `First`) + `Core` `Confirmed` (`ACCEPTED`). `Risk`: `Growth` (`Mental Availability` `Hard` `To Build` `Without` `Daily` `Habit`) + `Engagement` (`Not` `Natural` `Without` `Social` `Loop`).

`Direction` `B` (`Social` — `Alternative` `Not Confirmed` `But` `Possible` `If` `A` `REJECTED`): `Best` `If` `Engagement` (`Daily` `Loop`) `Priority` `Higher` `Than` `Library` `Discovery`. `Risk`: `Brand` (`Library` `Not Feed`) `Contradicts` `Social` `Purpose` — `Needs` `Brand` `Review` (`Not` `LOCKED` `If` `Social` `Primary`).

`Direction` `C` (`Hybrid` — `Possible` `Alternative` `Not Confirmed`): `Best` `If` `Both` `Discovery` (`Library`) `And` `Limited` `Social` (`Save`، `Share`، `Limited` `Trending`) `Needed`. `Risk`: `Complexity` (`Double` `Purpose` = `Double` `UI` `Needs`، `Mixed` `Metrics` — `Social` `Engagement` `Not` `Fit` `Utility` `Metrics`، `Utility` `Mental Availability` `Not` `Fit` `Social` `Loop`).

`Direction` `D` (`Content-Only` — `Possible` `If` `Library` `Fails` — `Not Confirmed` `But` `Possible`): `Best` `If` `Library` (`Discovery`) `Not` `Working` (`No` `Search` `Success`، `No` `Save` `Rate`). `Risk`: `Brand` (`Library` `Not` `Feed`) `Contradicts` `Social` `Purpose` — `Needs` `Brand` `Review` (`Not` `LOCKED` `If` `Social` `Only`).

`My` `Proposal` (`Not Final` — `Needs` `Nebras` `Confirmation`): `A` (`Utility`) `ACCEPTED` (`Not` `Social` `As` `Primary`)، `With` `Limited` `Social` `Features` (`Featured` `Not Default`، `Trending` `Not Default`، `Social` `Share` `Works` `Naturally` `If` `Save` `Used` `Outside`). `If` `A` `REJECTED` (`Social` `Alternative` `Confirmed`)، `Then` `Brand` (`LOCKED`) `Needs` `Review` (`Not` `Before` `Rejection` — `Only` `After` `A` `REJECTED`). `If` `A` `Not Confirmed` (`Still` `PROPOSED`)، `Then` `Not Move` `To` `B`/`C`/`D`/`E`/`F`/`G` `Before` `A` `Confirmed`.

---

## 18. ما الذي أقترحه؟ ([مقترح من التحليل — `Not Confirmed` — `Not Adopted` — `Needs` `Nebras`])

`My` `Initial` `Opinion` (`Not` `Final` `Decision` — `Clearly` `Labeled` `As` `Proposed` — `Not` `Adopted` `In` `File`):

`A` (`Utility`) `ACCEPTED` (`As` `Primary` `Purpose`)، `With` `Social` `Limited` (`Not` `Default` `Social` `Feed`، `But` `Social` `Share` `Loop` `Works` `Naturally` `If` `Save` `Used`).

`Reason`: `Brand` (`Library` `Not` `Feed`) `Supports` `Utility` (`Not` `Social` `As` `Primary`). `Content` (`Manual` `First`) `Works` `Better` `With` `Library` (`Discovery` `Not` `Social` `Feed`). `Search` (`Situational`) `Works` `Better` `With` `Library` (`Discovery` `Not` `Social` `Trending`). `Metrics` (`Mental Availability`، `Search Success`، `Save Rate`) `More` `Relevant` `To` `Utility` `Than` `Social` `Engagement` `Loop`.

`Risk` `Of` `This` `Proposal`: `Growth` (`Social` `Loop` `Not` `Natural` — `Mental Availability` `Hard` `To` `Build` `Without` `Daily` `Habit`). `Solution` (`Not` `Before` `Plan` `Adopted`، `But` `As` `Plan`): `Social` `Share` `Works` `Naturally` `If` `Save` `Used` `Outside` (`Share` `To` `Social` `Then` `Open` `Back` `To` `Library` `Then` `Save` `Again` — `Loop` `Possible` `But` `Not` `Daily` `Habit`). `If` `Social` `Loop` `Not` `Working` `Naturally` (`Not` `Tested` `Yet`)، `Then` `Growth` `Depends` `On` `Content` `Scale` (`150-300`) + `SEO` (`Sitemap` + `Social Embeds`) + `Mental Availability` (`Brand` `Memory` — `Not` `Habit`).

`Alternative` (`If` `A` `REJECTED`): `Social` (`As` `Primary`) `Requires` `Brand` `Review` (`Not` `LOCKED` `If` `Social` `Only`)، `UI` `Redesign` (`Featured`، `New`، `Trending` `As` `Primary` — `Not` `Library` `Only`)، `Taxonomy` `Review` (`Tags` `More` `Important`؟ `Collections` `As` `Destination`？), `Pipeline` `Review` (`Submissions` `More` `Important`？ `Manual` `Less` `Important`？), `Growth` `Review` (`Social` `Loop` `Natural`، `Engagement` `Loop` `Natural`، `Metrics` `Social` `Based`).

`Not` `Before` `Plan` `Adopted`: `This` `Proposal` (`Utility` `Primary` + `Social` `Limited`) `Can` `Be` `Adopted` `As` `Plan` `Only` `If` `Nebras` `Confirms` `A` (`ACCEPTED` `As` `Utility`). `Not` `Before`.

---

## 19. ما الأسئلة الحاسمة فقط؟ ([مقترح من التحليل — `Not` `Many` `Random` — `Only` `5` `Critical` — `Not Before` `Plan` `Adopted`])

`Q1` (`Core` — `Critical` `First` — `Not Before` `B`): `Utility` (`PROPOSED` — `Not Confirmed` `As` `ACCEPTED`) — `ACCEPTED` (`Utility` `Confirmed` `As` `Primary`) أم `REJECTED` (`Social` `Alternative`؟ `Hybrid`؟ `Content-Only`？ `Why` `Clear` `Reason` `Not Ambiguous`？)؟

`Q2` (`Brand` — `Quick` `Not Deep` — `But` `Necessary`): `LOCKED` (`Not Changed` `Without` `New` `ACCEPTED` `Decision`) — `Review` `Visual` (`Yes` — `What` `Specific` `Element` `To` `Modify`？ `Why`？ `How`？ `Not General` `Redesign`？ `No` — `Keep` `LOCKED`？)؟

`Q3` (`Value` — `Quick` — `Not Before` `Plan` `Adopted` `But` `Before` `B` `If` `A` `Confirmed`): `Local` `Alternative` (`Confirmed`) — `Keep` (`No Change`) أم `Modify` (`Add` `Point`？ `Simplify` `Point`？ `Not Ambiguous`？)？

`Q4` (`Audience` — `Quick` — `Not Before` `Plan` `Adopted` `But` `Before` `B` `If` `A` `Confirmed`): `4` `Groups` (`Meme Makers`، `Creators`، `Regular`، `Platforms`) — `Keep` (`No Change`) أم `Modify` (`Add` `Who`？ `Remove` `Who`？ `Not Ambiguous`？)？

`Q5` (`Content` — `Deep` — `Not Before` `B` `But` `Necessary` `To` `Plan` `B` `If` `A` `Confirmed`): `Manual` `Collection` (`30-50` `Raw` — `How` `Collected`？ `Social` `Scrape`？ `Archive` `Search`？ `Direct` `Upload` `Not Submissions`？ `Who` `Admin`？ `Time` `To` `30`？)？

---

## 20. ما الذي أحتاج معرفته من نِبراس الآن؟ ([مقترح من التحليل — `Not` `Many` — `Only` `These` `4` `Points`])

`From` `Nebras` (`Through` `User` — `Not` `From` `Me` `Self` `Adopted`):
1. `Core Loop` (`A` — `Utility` `PROPOSED`): `ACCEPTED` (`Utility` `Confirmed` `As` `Primary`) أم `REJECTED` (`Social` `Alternative`？ `Hybrid`？ `Content-Only`？ `Why` `Clear`？ `Not Ambiguous`？)？
2. `Brand` (`LOCKED`): `Review` (`Yes` — `What` `Specific`？ `Why`？ `How`？ `Not General`？) أم `No` (`Keep` `LOCKED`؟)？
3. `Value Prop` (`Local` `Alternative`): `Keep` (`No Change`) أم `Modify` (`What` `Point`？ `Not Ambiguous`？)？
4. `Audience` (`4` `Groups`): `Keep` (`No Change`) أم `Modify` (`Who` `Added`/`Removed`؟ `Not Ambiguous`؟)？

`Not Before` `A` `Answer` (`Not Before` `B`/`C`/`D`/`E`/`F`/`G`): `B` (`Content`)، `C` (`IA`)، `D` (`UX`)، `E` (`Architecture`)، `F` (`Growth`)، `G` (`Operations`)، `Implementation` (`Not Before` `Plan` `Adopted`).

---

## ملخص ما تم (`Done` `In` `This` `Open` `Session` — `Not` `From` `Previous` `Only`):

`Read`: `Yem React.md` (`Complete`)، `uploads/` (`All` — `Brand LOCKED`، `Identity`، `Social`، `Project Story`، `Content System`، `MVP`، `Production Guide`، `Asset Inventory`، `Social System`، `Identity System` `HTML`، `Templates`، `Web Prototype`، `Product UI`، `Bio`، `INDEX` `Previous`، `DECISIONS-LOG` `Previous`، `OPEN-QUESTIONS` `Previous`).

`Created`: `PROJECT_CONTEXT_AND_DECISIONS.md` (`RESET` `Complete` — `203` `Lines`، `Only` `Current` `Info`)، `phase_01_analysis_plan.md` (`7` `Axes`، `Logical` `Order`)، `session_analysis_open.md` (`This` `File` — `20` `Points` `Analysis`، `No` `New` `Adopted` `Decisions`، `Only` `Proposals` + `Inferences` + `Questions`).

`Confirmed` (`From` `This` `Session` `Only` — `Not` `From` `Previous` `Unless` `Confirmed` `Here`): `Source`/`Rights` (`REMOVED`)، `Performance Rating` (`REJECTED`)، `Brand LOCKED` (`Not Changed`)، `Video Only` (`Not Images`)، `Reaction Detail` (`Page`)، `Main` (`Library`)، `Sidebar` (`REMOVED`)، `Search` (`Part` `Of` `Home`)، `Schema Cleanup` (`REMOVED` `As` `Principle` — `Not Implemented`)، `Content Types` (`Not Rejected` — `Still` `PROPOSED`)، `Caption` (`Not Rejected`)، `Masonry` (`PROPOSED` — `Not Rejected`، `Not Confirmed` `As` `ACCEPTED`)، `Speech` (`PROPOSED` — `New` `In` `This` `Session` — `Not Confirmed`)، `Manual` `Content` (`PROPOSED` — `Not Implemented`)، `Submissions` (`Pipeline` `Exists` — `Not Activated` `As` `Primary` `Source`).

`Not Adopted` (`No` `New` `ACCEPTED`/`REJECTED` `In` `This` `Session` `Besides` `Previous` `Confirmed`): `Core Loop` (`PROPOSED` — `Not Confirmed` `As` `ACCEPTED` — `Critical` `Open` `Point`)، `Speech Service` (`OPEN` — `Not Chosen`)، `Content` (`Not Implemented`)، `Git` (`OPEN` — `Critical`)، `Admin` (`Not Tested` `Editorial`)، `Performance` (`OPEN` — `No Numbers`)، `Security` (`OPEN`)، `Observability` (`OPEN`)، `Accessibility` (`OPEN`)، `Growth` (`OPEN` — `Not Tested`).

`Not Updated` (`PROJECT_CONTEXT...` — `Only` `Previous` `Confirmations` `Kept` + `New` `Proposals` `Clearly` `Labeled` — `No` `New` `Adopted` `Decisions` `Added` — `Only` `Reset` + `Current` `Info`): `File` `Updated` `Only` `With` `Reset` (`Delete All` + `Rebuild` `Only` `Current` `Session` `Info`)، `Not` `With` `New` `Adopted` `Decisions` (`Only` `Proposed` `Clearly` `Labeled`).

`Not Implemented` (`No Code`، `No UI` `New`، `No Technical` `Structure` `Built` — `Only` `Analysis` + `Plan` + `Documentation`): `No Implementation` `Started` — `Only` `Framework` (`Nebras` → `User` → `Me`) + `Plan` (`Phase` `01` — `7` `Axes` `Logical` `Order`) + `Analysis` (`Session` `Open` — `20` `Points` `Covered`).

`Waiting` (`Not Before` `Next` `Axis`): `Nebras` `Confirmation` (`Through` `User`) `Of` `A` (`Core` — `Utility` `PROPOSED` — `ACCEPTED` `As` `Utility`؟ `REJECTED` `As` `Social`？ `Alternative`？ `Brand` `Review`？ `Value Prop`？ `Audience`？) — `Not Before` `B` (`Content`)، `C` (`IA`)، `D` (`UX`)، `E` (`Architecture`)، `F` (`Growth`)، `G` (`Operations`)، `Implementation` (`Not Before` `Plan` `Adopted`).

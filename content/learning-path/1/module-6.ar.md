---
style: module
title: الفحص النشط - تحليل رسائل البريد الإلكتروني الضارة
description: ستعلّمك هذه الوحدة كيفية تفسير وفهم رسائل البريد الإلكتروني الضارة والعثور على البنية التحتية المرتبطة بها. سواءً كانت عبارة عن هندسة اجتماعية بحتة، أو تصيد احتيالي، أو تسليم برامج ضارة، فإن رسائل البريد الإلكتروني الضارة يمكن أن تكون معقدة للغاية. في حين تهدف هذه المهارة مباشرة إلى التعرّف على البنية التحتية للمهاجمين، تُعدّ هذه المهارات المتقدمة لعكس رسائل البريد الإلكتروني المعقدة أيضًا تحضيرًا جيدًا لفهم حملات المهاجمين وهي مقدمة جيدة لتحليل البرمجيات الضارة الأكثر تعقيدًا. يمكن أن تساعدك بعض هذه التقنيات أيضًا في تحليل الرسائل المشبوهة المرسلة عبر وسائل أخرى مثل واتسآب.
weight: 6
---
## حالة استخدام

ستعلّمك هذه الوحدة كيفية **تفسير وفهم رسائل البريد الإلكتروني الضارة** و**العثور على البنية التحتية المرتبطة بها**. سواءً كانت عبارة عن هندسة اجتماعية بحتة، أو تصيد احتيالي، أو تسليم برامج ضارة، فإن رسائل البريد الإلكتروني الضارة يمكن أن تكون معقدة للغاية. في حين تهدف هذه المهارة مباشرة إلى التعرّف على البنية التحتية للمهاجمين، تُعدّ هذه المهارات المتقدمة لعكس رسائل البريد الإلكتروني المعقدة أيضًا تحضيرًا جيدًا لفهم حملات المهاجمين وهي مقدمة جيدة لتحليل البرمجيات الضارة الأكثر تعقيدًا. يمكن أن تساعدك بعض هذه التقنيات أيضًا في **تحليل الرسائل المشبوهة المرسلة عبر وسائل أخرى مثل واتسآب**.

لاحظ أنه أثناء التحقيق النشط، قد تضطر إلى تنفيذ إجراءات تُنبه المهاجم إلى وجود تحقيق (أو على الأقل أن شخصًا ما يتفاعل مع الفخ)، وضع في اعتبارك ما إذا كانت هذه تكلفة مقبولة لإكمال التحقيق أم لا.

من الأفضل إجراء نوع التحليل هذا من جهاز افتراضي أو جهاز مخصص. لأجل زيادة الحماية قد يكون من الجيد استخدام شبكة ظاهرية خاصة ذات سمعة طيبة لا تُسرب عنوان بروتوكول إنترنت الخاص بك عند إجراء تحقيق نشط.

تتناول هذه الوحدة تحليل نص رسالة بريد إلكتروني ضارة، في حين أن وحدة ا[لفحص غير النشط: تحليل رؤوس البريد الإلكتروني](/en/learning-path/1/module-5/) مع رأس البريد الإلكتروني. لإجراء التحقيقات المناسبة، ستحتاج إلى استخدام كلتا المهارتين ولاحظ أن مسار تعلّم تحليل البرمجيات الضارة يغطي تحليل محتويات وسلوكيات مرفقات البريد الإلكتروني.


## الأهداف

بعد استكمال هذا الموضوع الفرعي، يجب أن يكون الممارسون قادرين على القيام بما يلي:

- تحليل التعليمات البرمجية للغة تمييز النص التشعبي للبريد الإلكتروني وفهم أساسيات ملحقات بريد الإنترنت متعددة الأغراض.
- فهم واكتشاف بكسلات التتبع والمحتوى النشط المماثل.
- استخدم أدوات مثل فايروس توتال ويو آر إل سكان (URLScan) لتقييم المرفقات وعناوين مواقع ويب بحثًا عن المحتوى الضار.
---
## العرض

### المعرفة الأساسية: رسائل البريد الإلكتروني بلغة تمييز النص التشعبي وملحقات بريد الإنترنت متعددة الأغراض

من أجل التمرن عليها ستحتاج إلى فهم أساسيات رسائل البريد الإلكتروني بلغة تمييز النص التشعبي وملحقات بريد الإنترنت متعددة الأغراض. إذا كنت تشعر أنه من الضروري تحسين هذا الموضوع قليلًا راجع بعض الموارد حول الموضوعات الرئيسية أدناه:

- تُرسل غالبية رسائل البريد الإلكتروني بصيغة لغة تمييز النص التشعبي مما يسمح باستخدام طرق ذكية مختلفة للعرض والخداع من قبل المستخدمين المخادعين.
- مع أنه من غير الضروري أن تتمتع بالقدرة على كتابة لغة تمييز النص التشعبي أو تصميم صفحات الويب، يجب أن يكون الممارسون مرتاحين لفتح ومراجعة التعليمات البرمجية لمصدر البريد الإلكتروني المكتوب بلغة تمييز النص التشعبي وفهم العناصر الأساسية الموجودة. لأجل القيام بذلك اقرأ هذه المقدمة حول ملحقات بريد الإنترنت متعددة الأغراض [MIME ](<https://learn.microsoft.com/en-us/previous-versions/office/developer/exchange-server-2010/aa494197(v=exchg.140)>)والبريد الإلكتروني المكتوب بلغة تمييز النص التشعبي.
- لا بد من تعلّم القليل عن لغة تمييز النص التشعبي ويمكن أن توفر موارد [W3Schools](https://www.w3schools.com/html/) مثل نقطة انطلاق جيدة. لاحظ أيضًا أن بعض برمجيات البريد (على سبيل المثال آوتلوك) لا تسمح لك بتنزيل كامل نص البريد الإلكتروني.
- تُعدّ ملحقات بريد الإنترنت متعددة الأغراض معيار إنترنت يُوسع تنسيق رسائل البريد الإلكتروني إلى ما وراء رسائل البريد الإلكتروني ذات النص العادي ويسمح بالنص في مجموعات أحرف بخلاف مجموعة أحرف ASCII والمرفقات غير النصية ونصوص الرسائل ذات الأجزاء المتعددة ومعلومات الرؤوس في مجموعات الأحرف التي لا تنتمي إلى مجموعة أحرف ASCII. يمكن إساءة استخدام ميزات ملحقات بريد الإنترنت متعددة الأغراض لإخفاء المحتوى وإرفاق المحتوى الضار. تُقدم مقالة ويكيبيديا[مقالة ويكيبيديا](https://en.wikipedia.org/wiki/MIME) هذه مقدمة أولية جيدة.


### التعرّف على التهديدات المحتملة: الصور المضمّنة وبكسلات التتبع

عند فحص رسائل البريد الإلكتروني الضارة المحتملة لاكتشاف البنية التحتية للمهاجمين، لا تبحث فقط عن الروابط والمرفقات وقد يقوم المهاجمون بتضمين أجهزة التتبع في رسائل البريد الإلكتروني الخاصة بهم تمامًا كما يفعله المسوقون. تشرح هذه [ المقالة للمسوقين](https://www.nutshell.com/blog/email-tracking-pixels-101-how-do-tracking-pixels-work) كيفية عمل تتبع البريد الإلكتروني. لاحظ أنه يمكن استخدام أي مورد يتم تحميله من الويب للتتبع وليس فقط الصور. راجع أنواع المعلومات التي يمكن الحصول عليها من خلال بكسل التتبع أو عنصر التتبع بما في ذلك بروتوكول الإنترنت (الموقع الجغرافي) ومعلومات بصمات المتصفح. أنشأت إنترنيوز (Internews) تمرينًا تدريبيًا (موضحًا في قسم الممارسة أدناه) سيساعدك على التعرّف أكثر على أدوات التتبع وبعض المعلومات التي يمكنها اكتشافها.

### أدوات وسير عمل لتحليل البريد الإلكتروني الضار

بمجرد فهم المفاهيم الأساسية والتهديدات المحتملة، ستحتاج إلى سير عمل وأدوات للتحليل.

- يوفر سير عمل البريد الإلكتروني المشبوه الهادف إلى التصيد الاحتيالي[ Suspicious Phishing Email](https://communitydocs.accessnow.org/58-Suspicious_Phishing_Email.html) الذي تُقدمه آكسس ناو (Access Now) نهجًا منهجيًا لتقييم رسائل البريد الإلكتروني المشبوهة، ويتضمن قائمة بالخطوات من الملاحظة الأولية إلى تصنيف التهديدات والإبلاغ عنها.
- يمكن استخدام فايروس توتال[VirusTotal](https://virustotal.com/) لتقييم عناوين مواقع ويب والمرفقات للمحتوى الضار المعروف، ولاحظ أنه يمكن الوصول إلى عناوين مواقع ويب والملفات المقدمة من قبل مستخدمين آخرين، وقد يؤدي ذلك إلى تنبيه المهاجم إلى وجود تحليل يجري عليه. عادة ما يكون هذا خطرًا فقط أثناء الحملات المستهدفة للغاية، وفي حالات أخرى، يفترض الخصوم عمومًا أن شخصًا ما اكتشف أنماط هجومهم ويقوم بتحليلها.
- ألقِ نظرة على[ بعض أدوات تحليل البريد الإلكتروني الموضحة في هذه المقالة](https://intezer.com/blog/incident-response/automate-analysis-phishing-email-files/). يمكنهم التحقيق في محتوى البريد الإلكتروني والمرفقات ويعتمد عدد منها على سطر الأوامر، وهو أمر مفيد بشكل خاص للمحللين الذين يبحثون في المحتوى الذي تم إنشاؤه بواسطة جهات فاعلة متطورة، والذين قد يحاولون صياغة الرسائل بطرق تستغل الثغرات الأمنية داخل برمجيات البريد الإلكتروني. تُوضح [المقالة](https://blog.joshlemon.com.au/analysing-malicious-email-files-d85d8ff76a91) أيضًا بعض التقنيات التي تستخدمها الجهات الفاعلة في التهديد لإحباط التحليل وتبحث هذه المقالة بالمثل في كيفية تحويل ملفات آوتلوك إلى ملفات نصية عادية وتحليلها من خلال نوتباد أو سطر الأوامر وذلك لتقليل الأجزاء المعرضة للهجوم من البريد الإلكتروني الضار الذي يستغل أخطاء آوتلوك.

## الممارسة

[تلخص جميع الروابط في العرض بالإضافة إلى أي موارد إضافية لتضمينها]

اقرأ دراستي الحالة أدناه بالكامل، مع ملاحظة جميع العناصر الجديدة بالنسبة لك والتي تتطلب تمرينًا إضافيًا:
- [تحليل ملفات البريد الإلكتروني الضارة | تأليف جوش ليمون (Josh Lemon) | ميديم (Medium)](https://blog.joshlemon.com.au/analysing-malicious-email-files-d85d8ff76a91)
- [تحليل رسائل البريد الإلكتروني الضارة. مقدمة إلى تحليل البريد الإلكتروني للتصيد الاحتيالي | تأليف كايل بوبب (Kyle Bubp) | ميديم](https://medium.com/@kylebubp/analyzing-malicious-emails-fb4ddcf0663e)
- أنشأ مشروع إنترنيوز الذي يركز على أمن الصحفيين [تمرين محاكاة](https://internews.org/resource/guide-to-facilitating-a-technical-simulation-with-canary-tokens/) لمساعدة الناس على فهم وممارسة العمل مع أدوات التتبع بشكل أفضل. اقرأ المشروع وأكمل بعض التمارين.

## اختبار مهارة

اطلب من نظير أو مُرشِد أن يرسل لك بريدًا إلكترونيًا ويفضل أن يحتوي على العديد من العناصر مثل بكسلات التتبع والمرفقات والروابط التي ستستفيد من التحليل المتعمق. انتقل بدلًا من ذلك إلى صندوق الوارد الخاص بك واختر بريدًا إلكترونيًا غير ضار. استخدم المهارات المستخدمة في هذه الوحدة لتحليله:

- هل يمكنك قراءة رؤوس البريد الإلكتروني لمعرفة عنوان المرسل؟
- هل يمكنك تأكيد موثوقية المرسل؟ هل من المحتمل أن البريد الإلكتروني مزيف؟
- ما هي البنية التحتية التي تم استخدامها في تسليم الرسالة؟
- ما المحتوى النشط (ملحقات بريد الإنترنت متعددة الأغراض، بكسل التتبع) المضمن في البريد الإلكتروني؟
- ما البيانات التي يمكن تسريبها عن طريق فتح البريد الإلكتروني والتفاعل معه؟
- ماذا يريد المرسل منك أن تفعله عند استلام البريد الإلكتروني؟

## موارد التعلّم

{{% resource title="مقدمة إلى البريد الإلكتروني بتنسيق لغة تمييز النص التشعبي" description="مقدمة موجزة حول مفهوم إرسال رسائل البريد الإلكتروني التي تحتوي على لغة تمييز النص التشعبي" languages="عدة" cost="مجانًا" url="https://en.wikipedia.org/wiki/HTML_email" %}}

{{% resource title="مدخل إلى ملحقات بريد الإنترنت متعددة الأغراض" description="الوصف : مقدمة موجزة عن تنسيق ملحقات بريد الإنترنت متعددة الأغراض للرسائل" languages="عدة" cost="مجانًا" url="https://en.wikipedia.org/wiki/MIME" %}}

{{% resource title="كيفية تضمين الصور في البريد الإلكتروني" description="على الرغم من أن هذه الصفحة موجهة لمرسلي البريد الإلكتروني، إلا أنها تتناول الطرق التي قد يقوم بها المهاجمون بتضمين الصور في بريدهم الإلكتروني" languages="الإنجليزية" cost="مجانًا" url="https://mailchimp.com/resources/embed-image-in-email/" %}}

{{% resource title="تعلّم لغة تمييز النص التشعبي" description="تستخدم معظم رسائل البريد الإلكتروني الضارة للتصيد الاحتيالي لغة تمييز النص التشعبي لخداع المستخدمين، ومن أجل استخراج عناوين مواقع ويب (وبالتالي عناوين الخادم) من رسائل البريد الإلكتروني، سيتعين عليك تعلّم القليل عن لغة تمييز النص التشعبي" languages="عدة (ترجمة تلقائية)" cost="مجانًا" url="https://www.w3schools.com/html/" %}}

{{% resource title="مقدمة إلى بكسلات التتبع" description="عند فحص رسائل البريد الإلكتروني الضارة المحتملة لاكتشاف البنية التحتية للمهاجمين، لا تبحث فقط عن الروابط والمرفقات وقد يقوم المهاجمون بتضمين أجهزة التتبع في رسائل البريد الإلكتروني الخاصة بهم تمامًا كما يفعله المسوقون. تشرح هذه المقالة للمسوقين كيفية عمل تتبع البريد الإلكتروني ولاحظ أنه يمكن استخدام أي مورد يتم تحميله من الويب بقصد التتبع" languages="الإنجليزية" cost="مجانًا" url="https://www.nutshell.com/blog/email-tracking-pixels-101-how-do-tracking-pixels-work" %}}

{{% resource title="(VirusTotal) فايروستوتال" description="أداة لتقييم عناوين مواقع ويب والمرفقات بحثًا عن نية خبيثة معروفة، ولاحظ أنه يمكن الوصول إلى عناوين مواقع ويب والملفات المرسلة من المستخدمين الآخرين" languages="الواجهة الرئيسية باللغة الإنجليزية" cost="مجانًا، مع بعض القيود المتعلقة بالأسعار والميزات المدفوعة الإضافية" url="https://www.virustotal.com/gui/home/url" %}}

{{% resource title="سير عمل البريد الإلكتروني الضار" description="دليل إرشادي لما يجب القيام به عند تقييم بريد إلكتروني مشبوه" languages="عدة" cost="مجانًا" url="https://communitydocs.accessnow.org/58-Suspicious_Phishing_Email.html" %}}

{{% resource title="(Exchange) دليل فحص رسائل البريد الإلكتروني الضارة من إكستشينج" description="دليل للتحقيق في رسائل البريد الإلكتروني الضارة في بيئة مايكروسوفت إكستشينج (حيث يتمتع المحقق بوصول مشرف)" languages="الإنجليزية" cost="مجانًا" url="https://learn.microsoft.com/en-us/security/operations/incident-response-playbook-phishing" %}}

{{% resource title="أمثلة على تحليلات رسائل البريد الإلكتروني الاحتيالية" description="تحليلات لعينة من رسائل البريد الإلكتروني للتصيد الاحتيالي تتضمن نظرة على ملفات لغة تمييز النص التشعبي مع البرمجيات النصية الضارة المضمنة والمحتوى المشفر" languages="الإنجليزية" cost="مجانًا" url="https://medium.com/@kylebubp/analyzing-malicious-emails-fb4ddcf0663e" %}}

{{% resource title="أمثلة على تحليلات رسائل البريد الإلكتروني الاحتيالية" description="تحليلات لعينة من رسائل البريد الإلكتروني للتصيد الاحتيالي تتضمن نظرة على ملفات لغة تمييز النص التشعبي مع البرمجيات النصية الضارة المضمنة والمحتوى المشفر" languages="الإنجليزية" cost="مجانًا" url="https://www.vadesecure.com/en/blog/m365-phishing-email-analysis-eevilcorp" %}}

{{% resource title="أمثلة على تحليلات رسائل البريد الإلكتروني الضارة" description="الوصف : نظرًا لأن رسائل البريد الإلكتروني الضارة يمكن أن تستغل الثغرات الأمنية داخل برمجيات البريد الإلكتروني، يوضح هذا الدليل أفضل السبل لتحليلها باستخدام أدوات سطر الأوامر ومحررات النصوص" languages="الإنجليزية" cost="مجانًا" url="https://intezer.com/blog/incident-response/automate-analysis-phishing-email-files/" %}}

{{% resource title="أمثلة على تحليلات رسائل البريد الإلكتروني الضارة" description="الوصف : نظرًا لأن رسائل البريد الإلكتروني الضارة يمكن أن تستغل الثغرات الأمنية داخل برمجيات البريد الإلكتروني، يوضح هذا الدليل أفضل السبل لتحليلها باستخدام أدوات سطر الأوامر ومحررات النصوص" languages="الإنجليزية" cost="مجانًا" url="https://blog.joshlemon.com.au/analysing-malicious-email-files-d85d8ff76a91" %}}


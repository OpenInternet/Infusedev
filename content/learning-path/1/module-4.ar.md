---
style: module
title: الفحص غير النشط - تحليل عناوين مواقع ويب وأسماء المضيفين وعناوين بروتوكول الإنترنت
description: يمكن للممارس استخدام المهارات الموضحة في هذا الموضوع الفرعي لبدء فحص غير نشط ضد الخوادم على الإنترنت. الفحص غير النشط هو فحص لا يقوم بتحميل أي مواقع ويب ولكنه يبحث فقط عن البيانات المتاحة للعامة عليها، وبالتالي لن يتم تنبيه المهاجم إلى أن موقعه على الويب تلقى زيارات إضافية مما قد ينبهه إلى وجود فحص جارٍ.  من خلال تقييم معلومات النطاق والملكية الفكرية، يمكن للمحقق العمل على توليد معلومات تقنية غنية حول الهجوم مفيدة لتثقيف المجتمع، ومشاركة معلومات التهديد، واكتشاف البنية التحتية للمهاجمين المرتبطين، ووضع الهجمات في سياق أنماط هجوم أوسع.
weight: 4
---

## حالة استخدام

يمكن للممارس استخدام المهارات الموضحة في هذا الموضوع الفرعي **لبدء فحص غير نشط ضد الخوادم على الإنترنت**. الفحص غير النشط هو فحص لا يقوم بتحميل أي مواقع ويب ولكنه يبحث فقط عن البيانات المتاحة للعامة عليها، وبالتالي لن يتم تنبيه المهاجم إلى أن موقعه على الويب تلقى زيارات إضافية مما قد ينبهه إلى وجود فحص جارٍ.  من خلال تقييم معلومات النطاق والملكية الفكرية، يمكن للمحقق العمل على توليد معلومات تقنية غنية حول الهجوم مفيدة لتثقيف المجتمع، ومشاركة معلومات التهديد، واكتشاف البنية التحتية للمهاجمين المرتبطين، ووضع الهجمات في سياق أنماط هجوم أوسع.

قد تكون بعض هذه المهارات ضرورية كجزء ضمن عملية التصنيف الأولية، على سبيل المثال لمساعدة المحلل على تحديد ما إذا كان الرابط مشبوهًا، وسيثبت أنها مفيدة للغاية أثناء التحليل المتعمق لرؤوس البريد الإلكتروني الموضحة في القسم التالي.


## الأهداف 

بعد استكمال هذا الموضوع الفرعي، يجب أن يكون الممارسون قادرين على القيام بما يلي:

- فهم هيكل عنوان موقع الويب.
- فهم أنواع سجلات أنواع سجلات نظام أسماء المجالات وهو إز (WHOIS) والفرق بين بروتوكول الإنترنت الإصدار 4 والإصدار 6.
- إجراء استكشاف أساسي للمجالات.
- التعرف على الوكلاء العكسيين الشائعين التي تحمي عناوين بروتوكول الإنترنت الأصلية لأغراض الحماية من حجب الخدمة الموزع أو تحسين توصيل المحتوى، مثل كلاود فلير (CloudFlare) وأكاماي (Akamai) وفاستلي (Fastly).
- اكتشاف أو تعداد النطاقات الفرعية المرتبطة بنطاق.
 
---

## العرض
يستخدم الفحص غير النشط أدوات وموارد استخبارات المصادر المفتوحة التي يمكن أن تعطينا العديد من التفاصيل حول البصمة الرقمية للبنية التحتية للهجوم دون أن يلاحظ المهاجم أننا نجري تحقيقًا. 


### المعرفة الأساسية 

يتعمق هذا القسم في أساسيات عناوين مواقع الويب ونظام أسماء المجالات وبروتوكول الإنترنت الإصدار 4  (IPv4) وبروتوكول الإنترنت الإصدار 6 (IPv6). إذا كنت تشعر بأنك تعرف هذه المفاهيم فهذا رائع، ويمكنك الانتقال إلى قسم "سير العمل". خلاف ذلك تحقق من المستندات والموارد أدناه:

- هيكل عنوان موقع ويب
  - يجب أن تكون قادرًا على قراءة عنوان موقع ويب وفهم أهمية أجزائه، بما في ذلك تحديد المخطط والنطاقات الفرعية والنطاق الأساسي ونطاقات المستوى الأعلى وأي ميزات تعريف للمسار أو المعلمات في عنوان موقع الويب. إذا كنت بحاجة إلى مراجعة هذه الأمور، اطلّع على هذا [المستند من إم دي إن](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL).
    
- أدوات اختصار عناوين موقع الويب
  - قد تستخدم بعض الرسائل الضارة أداة اختصار عناوين موقع الويب لإخفاء الرابط الضار الفعلي. إذا كنت ترغب في رؤية الوجهة النهائية للرابط، يمكنك استخدام خدمة عبر الإنترنت مثل [unshorten.me](https://unshorten.me/) لعرض عنوان موقع الويب الكامل. لكن لاحظ أن إلغاء تقصير عنوان موقع ويب قد ينبه المهاجم إلى أنك تجري تحقيقًا ويجب اعتباره تحليلًا نشطًا.
- نظام أسماء المجالات 
   - [ مقدمةّ إلى نظام أسماء المجالات ](https://aws.amazon.com/route53/what-is-dns/)
   -  [أنواع سجلات نظام أسماء المجالات](https://www.cloudflare.com/learning/dns/dns-records/)
   -  موقع هو إز - يجب أن تفهم كيفية توليد سجلات هو إز وتخزينها وقراءتها والاستعلام عن سجلاتها لأي نطاق [استبدال بمورد]. إذا كنت بحاجة إلى مزيد من المعلومات حول ذلك، اطلّع علىهذا [الدليل](https://www.domain.com/blog/what-is-whois-and-how-is-it-used/).
- بروتوكول الإنترنت الإصدار 4/بروتوكول الإنترنت الإصدار 6 
ما هو بروتوكول الإنترنت الإصدار 4
 [https://bluecatnetworks.com/glossary/what-is-ipv4/](https://bluecatnetworks.com/glossary/what-is-ipv4/)
   - فهم الاختلافات بين بروتوكول الإنترنت الإصدار 4 والإصدار 6.
 [https://www.geeksforgeeks.org/differences-between-ipv4-and-ipv6](https://www.geeksforgeeks.org/differences-between-ipv4-and-ipv6/)
   - فهم عناوين بروتوكول الإنترنت
[https://www.enterprisenetworkingplanet.com/standards-protocols/understanding-ip-addresses/](https://www.enterprisenetworkingplanet.com/standards-protocols/understanding-ip-addresses/)
   - بالإضافة إلى عناوين بروتوكول الإنترنت، من المفيد التعرّف على  [أرقام المنافذ port numbers](https://www.techtarget.com/searchnetworking/definition/port-number).


### مسارات العمل: الأدوات والقدرات

يمكن تقسيم الفحوص غير النشطة لبروتوكول الإنترنت/نظام أسماء المجالات إلى عدة فئات.

الحصول على المعلومات الأساسية حول بروتوكول الإنترنت/نظام أسماء المجالات
إحدى أولى الأمور التي يجب علينا القيام بها في فحصنا هو الحصول على بعض المعلومات الأولية حول النطاقات والمضيفين وهناك عدد من الأدوات وفئات الأدوات التي يمكن أن تساعد في ذلك.

- موقع هو إز WHOIS
سجلات هو إز متاحة للعامة وتحتوي على معلومات مفيدة عن النطاق ويمكنك التعرف على كيفية استخدام الأدوات المساعدة المستندة إلى الويب (على سبيل المثال [ARIN whois](https://search.arin.net/rdap/) أو [who.is](https://who.is/)) أو أدوات سطر الأوامر لعرض سجلات هو إز وتعلّم قراءة معلومات المسجَّل (إذا تم الكشف عنها) والمسجِّل وتاريخ التسجيل وخوادم أسماء نظام أسماء المجالات التي تشير إلى مكان استضافة السجلات الرسمية لمنطقة نظام أسماء المجالات هذه.

يمكن أيضًا تشغيل هو إز على عنوان بروتوكول إنترنت من أجل محاولة تحديد الشركة المسؤولة عن عنوان بروتوكول إنترنت، وبالتالي من المحتمل أن تخبرك بشركة الاستضافة التي تقدم الخدمة لموقع إلكتروني.

- أمرا dig وhost:
سجلات هو إز متاحة للعامة وتحتوي على معلومات مفيدة عن النطاق ويمكنك التعرف على كيفية استخدام الأدوات المساعدة المستندة إلى الويب (على سبيل المثال [ARIN whois](https://search.arin.net/rdap/) أو [who.is](https://who.is/)) أو أدوات سطر الأوامر لعرض سجلات هو إز وتعلّم قراءة معلومات المسجَّل (إذا تم الكشف عنها) والمسجِّل وتاريخ التسجيل وخوادم أسماء نظام أسماء المجالات التي تشير إلى مكان استضافة السجلات الرسمية لمنطقة نظام أسماء المجالات هذه.
تُعد **dig** أداة سطر أوامر إما مثبتة مسبقًا أو متوفرة لأنظمة التشغيل الرئيسية. تسمح لك بالبحث بسهولة ([اتبع الدليل التعليمي هنا](https://phoenixnap.com/kb/linux-dig-command-examples)) عن سجلات نظام أسماء المجالات لأي نطاق ويميز بين أنواع السجلات المختلفة. في حين أن الدليل التعليمي الموجود رابطه يحتوي على العديد من عناصر بناء جملة dig، يُعدّ الاستخدام الأكثر شيوعًا هو البحث في أنواع سجلات A وMX. يحظى dig بشعبية كبيرة بين المحللين لأنه بسيط وسهل الأتمتة. تُعدّ host (انظر [رابط الدليل التعليمي](https://www.geeksforgeeks.org/host-command-in-linux-with-examples/)) أداة سطر أوامر بديلة تقوم بتحويل اسم المضيف بسرعة إلى عنوان بروتوكول إنترنت مع بناء جملة أبسط. هناك أيضًا الكثير من البدائل لأداة dig تتمتع بميزات أكثر أو من الأسهل قراءتها، مثل [doggo](https://github.com/mr-karan/doggo).
انتبه إلى خوادم أسماء الوكيل العكسي الشائعة التي تستخدم لتوزيع المحتوى مثل تلك التي تقدمها أكاماي (على سبيل المثال a1-64.akam.net) وكلاودفلير (على سبيل المثال eve.ns.cloudflare.com) وفاستلي (على سبيل المثال ns3.fastly.net) لأن ستحجب عنوان بروتوكول إنترنت الأصلي للخادم. بعد قضاء القليل من الوقت في الاطلاع على خوادم الأسماء، ستتمكن بسهولة من التعرف على العديد من هؤلاء الوكلاء. إذا قمت على سبيل المثال بتشغيل أمر dig للبحث عن theguardian.com، فسترى أنه يوجهك إلى خوادم فاستلي (Fastly) (على الأقل في وقت كتابة هذا التقرير).

- قاعدة بيانات جيو آي بي (geoIP)
ترتبط عناوين بروتوكول الإنترنت تقريبًا بجغرافيات فعلية، وهذا يعني أنه إذا كنت تعرف عنوان بروتوكول إنترنت، فيمكنك أن تستنج (MaxMind GeoIP searchup demo linked)[you can figure out](https://www.maxmind.com/en/geoip-demo)) بدرجة معينة من اليقين مكان وجود الشخص الذي يستخدم هذا العنوان في العالم (البلد أو المنطقة). توجد العديد من قواعد البيانات المعروفة باسم جيو آي بي والتي تسمح لك بالبحث عن هذا الأمر. لاحظ أن دقة عمليات البحث المستندة إلى بروتوكول الإنترنت يمكن أن تكون متنوعة للغاية ففي بعض الأحيان من الممكن تعقب عنوان بروتوكول إنترنت لمؤسسة معينة، بينما في أحيان أخرى تحصل فقط على التفاصيل على مستوى البلد. 

🛠️ خصص بعض الوقت للتدرب على استخدام هذه الخدمات. يمكنك على سبيل المثال استخدامها لفحص موقع الويب الخاص بك أو موقع مؤسستك.


#### الحصول على المعلومات الأساسية حول بروتوكول الإنترنت/نظام أسماء المجالات

توجد مجموعة متنوعة من الطرق التي يمكن للمرء من خلالها الحصول على معلومات إضافية حول المضيفين في النطاق. لكن لاحظ أن معظم هذه التقنيات لا تعمل إلا في بعض الأحيان وغالبًا ما تفشل، ولكن لا تدع عزيمتك تثبط في حال عدم عمل إحداها، وتشمل بعض هذه الطرق ما يلي:

- استخدام عمليات نقل منطقة نظام أسماء المجالات. تتمثل إحدى ميزات خوادم نظام أسماء المجالات الموثوقة (عادةً ما يتم تعطيلها عبر الإنترنت) في تقديم مجموعة كاملة من سجلات نظام أسماء المجالات لنطاق معين. الغرض من استخدامها في مزامنة خوادم النسخة المتماثلة مع الخادم الأساسي. اطلّع على هذا [الدليل](https://0xffsec.com/handbook/information-gathering/subdomain-enumeration/) حول كيفية استخدام dig والأدوات الأخرى لمعرفة النطاقات الفرعية بناءً على عمليات نقل منطقة نظام أسماء المجالات.
- استخدام القوة العمياء لمعرفة نطاقات فرعية. يمكن للمرء ببساطة تخمين النطاقات الفرعية باستخدام قائمة من بادئات النطاقات الفرعية الشائعة وسؤال خادم نظام أسماء المجالات عن عناوين بروتوكول الإنترنت لتلك الخوادم. (على سبيل المثال webmail.attacker.com وvpn.attacker.com وremoteaccess.attacker.com، إلخ.) طالما أن الخادم يعطي استجابة NXDOMAIN (هذا النطاق غير موجود) لأسماء المضيف غير الموجودة، يمكن للمرء في كثير من الأحيان العثور على النطاقات المخفية بهذه الطريقة. يسرد هذا [الدليل حول تعداد النطاقات الفرعية](https://0xffsec.com/handbook/information-gathering/subdomain-enumeration/) أيضًا بعض أدوات القوة العمياء.
- إجراء بحث عكسي لعناوين بروتوكول الإنترنت المجاورة، حيث ستتيح لك بعض خوادم نظام أسماء المجالات البحث عن اسم المضيف لعنوان بروتوكول إنترنت. من الشائع وجود البنية التحتية المستضافة ذاتيًا في مجموعة صغيرة من عناوين بروتوكول الإنترنت. بالنظر إلى ذلك، من الممكن أحيانًا بالنظر إلى عنوان بروتوكول إنترنت لاسم مضيف واحد (على سبيل المثال 127.0.0.5)، البحث عن أسماء المضيف لعناوين بروتوكول الإنترنت القريبة (على سبيل المثال 127.0.0.1-127.0.0.254).
- 
توجد أدوات تستخدم هذه التقنيات وغيرها لمحاولة اكتشاف موارد الشبكة الإضافية، وإحدى أولى هذه الأدوات التي لا تزال قيد التطوير هي [فيرس (Fierce)](https://www.kali.org/tools/fierce/) وإحدى الأدوات الشائعة الأخرى هي د[ي إن إس ريكون (DNS Recon)](https://securitytrails.com/blog/dnsrecon-tool). يتضمن [منشور المدونة هذا الذي يصف دي إن إس ريكون (DNSRecon)](https://securitytrails.com/blog/dnsrecon-tool#content-alternatives-to-dnsrecon) أيضًا قائمة بأدوات تعداد نظام أسماء المجالات الشائعة الأخرى.



#### إثراء معلومات بروتوكول الإنترنت/نظام أسماء المجالات باستخدام خدمات ماسح الإنترنت

بمجرد حصولك على معلومات المعرّف (النطاقات وعناوين بروتوكول الإنترنت)، يمكنك البحث في هذه البيانات بعمق أكبر باستخدام بعض الخدمات التي تسمح لك بالتحقيق في معلومات إضافية حول المضيف وأي نشاط مرتبط به. 

تعرّف على كيفية عرض المنافذ المفتوحة والخدمات النشطة وشرائط الخدمة من عنوان بروتوكول إنترنت معين باستخدام واحدة من العديد من خدمات المسح الذكي للويب. لاحظ أن هذا لا يزال أسلوب فحص غير نشط لأن هذه الخدمات تفحص الويب بشكل متكرر بحثًا عن مجموعات بياناتها ولن تبدأ نشاطًا جديدًا على البنية التحتية قيد الدراسة:

- استخدم [سينسيس سيرش (Censys Search)](https://search.censys.io/)  لمراقبة المنافذ المفتوحة، وتشغيل الخدمات، وشهادات بروتوكول أمان طبقة النقل، والمزيد حول عنوان بروتوكول إنترنت معين.
- استخدم [شودان (Shodan)](https://www.shodan.io/)(تتطلب الاشتراك لبعض الميزات وتتطلب استخدام فلاتر شودان في الاستعلامات، انظر المرجع والأمثلة) للبحث عن معلومات حول الخدمات التي تعمل على الخادم حسب عنوان بروتوكول إنترنت. يمكن لشودان أيضًا البحث عن جميع الخوادم التي تدير خدمة ذات شعار معين.
- استخدم )[دي إن إس دمبستر (DNS Dumpster](https://dnsdumpster.com/) للبحث عن الأجزاء المعرضة للهجوم المحتملة للخدمات التي تواجه الإنترنت.

يمكن أن تساعدك هذه الخدمات وقواعد البيانات المماثلة في تحديد أنشطة وتاريخ خادم/خدمة محددة.

تجمع خدمات المسح الأخرى أيضًا **سجل نظام أسماء النطاقات** مما يسمح لك بالرجوع في الوقت المناسب لمعرفة تحليلات النطاق الأخرى التي ظهرت لعنوان بروتوكول إنترنت معين ومتى ظهرت أو اختفت، بالإضافة إلى النطاقات الفرعية لنطاق معين.

- [المسارات الأمنية (Security Trails)](https://securitytrails.com/)
- يوفر تحليل[ مايكروسوفت ديفندر الذكي للمخاطر (Microsoft Defender Threat Intelligence)](https://www.microsoft.com/en-us/security/business/solutions/extended-detection-response-xdr) (المعروف سابقًا باسم ريسك آي كيو) تاريخًا محدودًا لنظام أسماء النطاقات والتحليلات لعملاء درجتاه المجانية.


#### إثراء معلومات بروتوكول الإنترنت/نظام أسماء المجالات باستخدام قواعد بيانات معلومات التهديد

ستقوم عدة خدمات بجمع مؤشرات التهديدات وتاريخ السلوك الضار. إذا كنت بحاجة إلى التأكد من عدم بدء أي نشاط مسح جديد (والذي سيكون تحقيقًا نشطًا)، تأكد من أنك لا تبدأ فحصًا جديدًا باستخدام بحثك (على سبيل المثال، بينما يسمح لك فايروس توتال (VirusTotal) بالتحقق من عنوان موقع ويب، فسيطلق فحصًا جديدًا مقابل عنوان موقع ويب، وبالتالي بدء النشاط الذي يمكن كشف أنه تحقيق). 

- ألين فولت أو تي إكس [Alienvault OTX](https://otx.alienvault.com) هو مورد مفتوح يوجهه المجتمع متعلق بالمؤشرات الضارة، وسيعرض البحث عن عنوان بروتوكول إنترنت أو اسم مضيف معلومات مفيدة عن استخبارات المصادر المفتوحة بالإضافة إلى سجلات أي نشاط ضار تم الحصول عليه مسبقًا.
- توفر [مانديانت أدفنتيج (Mandiant Advantage)](https://www.mandiant.com/multi-vendor-security-platform-free-access) (التي تملكها شركة غوغل (Google)) وظائف بحث محدودة على درجتها المجانية. 


#### استخدام البحث عن الشهادات

يستخدم كل موقع ويب تقريبًا يواجهه المستخدم الآن بروتوكول نقل نص تشعبي (HTTPS)، والذي يستخدم تقنية تعرف باسم بروتوكول أمان طبقة النقل (Transport Layer Security واختصارًا TLS). تستخدمه مواقع الويب الضارة أيضًا مما يؤدي جزئيًا إلى اعتقاد المستخدمين بأن بروتوكول نقل نص تشعبي والقفل الذي يظهر في شريط عناوين مواقع ويب للمتصفح يعني أن موقع الويب آمن بغض النظر عن العوامل الأخرى.

نظرًا لأنه يجب توقيع شهادات بروتوكول أمان طبقة النقل من قبل هيئة شهادات موثوقة (Certificate Authority) حتى يثق بها المتصفح، قد تتوفر كمية كبيرة من البيانات حول النطاق لتحقق فيه أثناء البحث عن البنية التحتية المشتركة والنطاقات الفرعية والمعرفات والأصول الأخرى. 

تتوفر كمية كبيرة من بيانات الشهادات للعامة بفضل ممارسة شفافية الشهادات حيث تضيف سلطات الشهادات جميع الشهادات الصادرة إلى سجل عام مقاوم للتلاعب. قد يكون من المفيد فهم هذا النظام، لذا اطلّع على نظرة عامة موجزة على  [ موقع شفافية الشهادات Certificate Transparency website](https://certificate.transparency.dev/) أو تعمّق في نظرة عامة فنية حول [كيفية عمل شفافية الشهادات](https://certificate.transparency.dev/howctworks/) ومن المفيد للمتعلّمين الذين يرغبون في معرفة المزيد حول تتبع واكتشاف البنية التحتية الضارة أن يكون لديهم فهم واسع لهذا النظام.

يمكن التمرّن على استخدام البحث عن الشهادات للنطاقات والنطاقات الفرعية وعناوين بروتوكول الإنترنت وتحديد المعلومات المثيرة للاهتمام مثل تواريخ الإصدار والمعلومات المرتبطة الموجودة في الشهادات الصادرة.

اقرأ الدليل في [الشهادات: هدية استخبارات المصادر المفتوحة التي تتابع العطاء...](https://www.osintcurio.us/2019/03/12/certificates-the-osint-gift-that-keeps-on-giving/) والتي تصف مجالات الفحص الرئيسية وعمليات البحث باستخدام سينسيس وشودان، وشاهد الفيديو المرفق الذي مدته  10 دقائق على يوتيوب](https://www.youtube.com/watch?v=XHltHamQVoA) والذي ينفذ البحث ذاته باستخدام [سي آر تي دوت إس إش (crt.sh)](https://crt.sh/). من المفيد أن تكون قادرًا على استخدام جميع أدوات البحث الثلاثة وعلى وجه الخصوص تأكد من فهمك لما يلي:

- ماهية بعض الحقول "المثيرة للاهتمام" ضمن الشهادة عند إجراء تحقيق
- كيفية البحث ضمن تلك الحقول على المنصات المختلفة
- كيفية تحديد النطاقات الفرعية وعناوين بروتوكول الإنترنت المضيفة والنطاقات البديلة الصادرة لشهادة.

لاحظ أن بناء جملة واجهة برمجة تطبيقات البحث لسينسيس قد تغير في عام 2021 وأن بعض عمليات البحث في الأدلة التعليمية المذكورة أعلاه لن تعمل. على سبيل المثال، بدلًا من "parsed.names :" استخدم ببساطة ":names" في بناء الجملة الجديد.

بُنيت العديد من الأدوات حول سجلات شفافية الشهادة، وعلى سبيل المثال حاول تعداد النطاقات الفرعية باستخدام [ماس دي إن إس (MassDNS) ](https://github.com/blechschmidt/massdns#reconnaissance-by-brute-forcing-subdomains) (انظر تعليمات استخدام scripts/ct.py على صفحة READMe).

تُقدم سينسيس مقالات إضافية القراءة حول التقنيات المتقدمة لتتبع ممثلي التهديد ومطاردتهم باستخدام منصتها في  [التتبع المتقدم للبنية التحتية Advanced Persistent Infrastructure Tracking](https://censys.com/advanced-persistent-infrastructure-tracking/)التي تستمر في البقاء


## الممارسة

اختر اسم نطاق عشوائي، وتأكد من عدم استضافته خلف خدمة توزيع المحتوى/الوكيل العكسي مثل كلاود فلير (يمكنك اكتشافه من خلال البحث السريع عنه باستخدام أداة مثل dig واستخدام خيار NS للبحث عن خوادم الأسماء). باستخدام فئات الأدوات المذكورة أعلاه، تحقق من المجال وحاول شرح:

- مكان تسجيل النطاق وفي حال كان متاحًا، فمن قام بتسجيله؟
- ما هو عنوان بروتوكول إنترنت؟
- من يدير عنوان بروتوكول الإنترنت هذا؟
- أين يقع هذا الخادم؟
- (إذا كان بإمكان الممارسين الوصول إلى شودان أو سينسيس) ما هي الخدمات التي يتم تشغيلها على هذا الخادم؟
- ما النطاقات الأخرى المستضافة على عنوان بروتوكول الإنترنت ذاته؟
- هل يمكنك العثور على أي نطاقات فرعية لهذا المجال؟

## اختبار مهارة

اجلس مع نظير أو مُرشِد لديه خبرة كبيرة في الفحص غير النشط ضد الخوادم على الإنترنت، ثم:

- أكمل غرفة  على تراي هاك مي (TryHackMe)[الاستطلاع غير النشط passive reconnaissance room](https://tryhackme.com/room/passiverecon).
- نفّذ تمارين التدريب المذكورة أعلاه، ومن الناحية المثالية على مجال مختلف واستعرض عمليتك ونتائجك مع نظير أو مُرشِد، اطلب منه مراجعة عملك وتقديم ملاحظات حول كل من العملية والنتائج. قد يكون من الجيد مناقشة كيفية العثور على النطاقات الفرعية التي تعمل على هذا المجال على وجه التحديد ومناقشة دقة عمليات بحث قاعدة بيانات جيو آي بي المتعلقة بتلك المجالات. ويمكن أيضًا أن تجلس مع النظير أو المُرشِد للمرور على بعض إعدادات dig المتقدمة وإعداد أتمتة أساسية معًا على سبيل المثال كي تطلب من dig تحميل قائمة بالنطاقات من ملف نصي وتقديم معلومات عنها.
- ذا كان لديك رسالة تصيد احتيالي فعلية (أو بدلًا من ذلك احصل على نطاق تصيد احتيالي من [فيش تانك (PhishTank](https://phishtank.org/)) وحللها ولاحظ أن موقع الويب يجمع النطاقات بدلًا من الرسائل)، ثم أجر الفحص غير النشط الموضح في تمرين الممارسة بحذر شديد أثناء التشاور مع نظير أو مُرشِد ثم وثّق النتائج التي توصلت إليها وعمليتك. اطلب منه مراجعة عملك وتقديم ملاحظات حول كل من العملية والنتائج.




## موارد التعلّم

{{% resource title="ما هي عنوان موقع الويب؟" description="نظرة عامة موجزة على عناوين مواقع الويب، وكيفية إنشائها، والميزات الإضافية (نصوص الربط وما شابه ذلك) التي قد تكون لديها" languages="الإسبانية والإنجليزية والروسية والصينية والعربية والفرنسية" cost="مجانًا" url="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL" %}}

{{% resource title="مقدمة إلى نظام أسماء المجالات" description="نظرة عامة أساسية حول كيفية عمل نظام أسماء النطاقات" languages="فيديو باللغة الإنجليزية مع نص باللغة العربية والبهاسا الإندونيسية والألمانية والإسبانية والفرنسية والإيطالية والبرتغالية والفيتنامية والتركية والروسية والتايلاندية واليابانية والكورية والصينية والتايوانية" cost="مجانًا" url="https://aws.amazon.com/route53/what-is-dns/" %}}

{{% resource title="نظرة عامة على أنواع سجلات نظام أسماء النطاقات" description="تتضمن أنواع السجلات الأكثر شيوعًا وبعضها الأقل شيوعًا" languages="الإنجليزية والألمانية والإسبانية والفرنسية والإيطالية واليابانية والكورية والبرتغالية والتايوانية والماندرين" cost="مجانًا" url="https://www.cloudflare.com/learning/dns/dns-records/" %}}

{{% resource title="dig  استخدام أمر" description="الوصف : كيفية الاستعلام عن معلومات حول عناوين بروتوكول الإنترنت" languages="الإنجليزية" cost="مجانًا" url="https://phoenixnap.com/kb/linux-dig-command-examples" %}}

{{% resource title="doggo  أمر" description="بديل لأمر يتمتع بوظائف متشابهة للغاية ولكن مخرجات مرتبة بتنسيق مختلف dig" languages="الإنجليزية" cost="مجانًا" url="https://github.com/mr-karan/doggo" %}}
{{% resource title="أمر في لينوكس مع أمثلة host" description="الوصف : دليل حول كيفية استخدام أمر المضيف في لينوكس وهو أداة أخرى شائعة الاستخدام لتحليل الخوادم وأنواع البنية التحتية الأخرى" languages="الإنجليزية" cost="مجانًا" url="https://www.geeksforgeeks.org/host-command-in-linux-with-examples/" %}}

{{% resource title="المزيد من الاستكشاف لنظام أسماء النطاقات" description="أدوات مختلفة لأتمتة البحث عن الخوادم ذات الصلة" languages="الإنجليزية" cost="مجانًا" url="https://securitytrails.com/blog/dnsrecon-tool" %}}

{{% resource title="المزيد من الاستكشاف لنظام أسماء النطاقات" description="أدوات مختلفة لأتمتة البحث عن الخوادم ذات الصلة" languages="الإنجليزية" cost="مجانًا" url="https://www.kali.org/tools/fierce/" %}}

{{% resource title="المزيد من الاستكشاف لنظام أسماء النطاقات" description="أدوات مختلفة لأتمتة البحث عن الخوادم ذات الصلة" languages="الإنجليزية" cost="مجانًا" url="https://salsa.debian.org/pkg-security-team/fierce" %}}

{{% resource title="(geoIP) قاعدة بيانات جيو آي ب" description="البحث عن الموقع الفعلي (المحتمل) للخادم بواسطة عنوان بروتوكول إنترنت" languages="الإنجليزية" cost="مجانًا بكميات محدودة" url="https://www.maxmind.com/en/geoip-demo" %}}

{{% resource title="(whois/RDAP) هو إز / السجل الأمريكي لأرقام الإنترنت" description="تعرض معلومات الملكية لنطاق أو عنوان بروتوكول إنترنت" languages="الإنجليزية" cost="مجانًا" url="https://who.is/" %}}

{{% resource title="(whois/RDAP) هو إز / السجل الأمريكي لأرقام الإنترنت" description="تعرض معلومات الملكية لنطاق أو عنوان بروتوكول إنترنت" languages="الإنجليزية" cost="مجانًا" url="https://search.arin.net/rdap/" %}}

{{% resource title="(whois/RDAP) هو إز / السجل الأمريكي لأرقام الإنترنت" description="تعرض معلومات الملكية لنطاق أو عنوان بروتوكول إنترنت" languages="الإنجليزية" cost="مجانًا" url="https://lookup.icann.org/en" %}}

{{% resource title="كيفية استخدام هو إز وما هو؟" description="ملخص سريع لماهية قاعدة بيانات هو إز وحدودها المحتملة" languages="الإنجليزية" cost="مجانًا" url="https://www.domain.com/blog/what-is-whois-and-how-is-it-used/" %}}

{{% resource title="الدليل الأمثل لقاعدة بيانات هو إز" description="يقدم نظرة على ما يمكن (وما لا يمكن) استخدام هو إز لأجله" languages="الإنجليزية" cost="مجانًا" url="https://domainnamestat.com/blog/the-ultimate-guide-to-the-whois-database" %}}

{{% resource title="ما هو عنوان بروتوكول إنترنت من الإصدار الرابع؟" description="هناك نوعان من عناوين بروتوكول الإنترنت، بروتوكول الإنترنت الإصدار 4 والإصدار 6، ويُقدم هذا الدليل مقدمة عن الإصدار 4" languages="الإنجليزية" cost="مجانًا" url="https://bluecatnetworks.com/glossary/what-is-ipv4/" %}}

{{% resource title="الاختلافات بين بروتوكول الإنترنت الإصدار 4 والإصدار 6" description="يحدد الاختلافات الرئيسية بين نوعي عناوين بروتوكول الإنترنت" languages="الإنجليزية" cost="مجانًا" url="https://www.geeksforgeeks.org/differences-between-ipv4-and-ipv6/" %}}

{{% resource title="فهم عناوين بروتوكول الإنترنت" description="الوصف : مقدمة سريعة لماهية عناوين بروتوكول الإنترنت، وأنواعها المختلفة" languages="الإنجليزية" cost="مجانًا" url="https://www.enterprisenetworkingplanet.com/standards-protocols/understanding-ip-addresses/" %}}

{{% resource title="إذن ما هي بالضبط أرقام المنافذ وكيف تعمل؟" description="الوصف : مقدمة سريعة إلى أرقام المنافذ تتضمن قائمة ببعض الأرقام الرئيسية" languages="الإنجليزية" cost="مجانًا" url="https://www.techtarget.com/searchnetworking/definition/port-number" %}}

{{% resource title="تعداد النطاق الفرعي: الدليل الأمثل" description="الوصف : دليل يحتوي على عدد من التقنيات حول تعداد (التعرّف على) المجالات الفرعية التي يضمها مجال معين. تجدر الإشارة إلى أنه لن تعمل جميع التقنيات على جميع المجالات/الخوادم" languages="الإنجليزية" cost="مجانًا" url="https://0xffsec.com/handbook/information-gathering/subdomain-enumeration/" %}}

{{% resource title="خدمات استخبارات التهديدات مع سجل نظام أسماء النطاقات" description="تقوم هذه الخدمات بمسح نظام أسماء النطاقات وإضافة السجلات وبالتالي يمكن للمحللين الذين يستخدمونها معرفة ما إذا كانت بعض مواقع الويب أو العناوين قد تم نقلها أو تغييرها" languages="الإنجليزية" cost="مجانًا مع ميزات مدفوعة" url="https://securitytrails.com/" %}}

{{% resource title="خدمات استخبارات التهديدات مع سجل نظام أسماء النطاقات" description="تقوم هذه الخدمات بمسح نظام أسماء النطاقات وإضافة السجلات وبالتالي يمكن للمحللين الذين يستخدمونها معرفة ما إذا كانت بعض مواقع الويب أو العناوين قد تم نقلها أو تغييرها" languages="الإنجليزية" cost="مجانًا مع ميزات مدفوعة" url="https://ti.defender.microsoft.com/" %}}

{{% resource title="(Alienvault OTX) إيلين فولت أو تي إكس" description="الوصف : خدمة تجمع المعلومات والمؤشرات المتعلقة بالتهديدات التي يطرحها المجتمع" languages="الإنجليزية" cost="مجانًا" url="https://otx.alienvault.com/" %}}

{{% resource title="(Mandiant Advantage)  مانديانت أدفنتيج" description="الوصف : خدمة أخرى للتحليل الذكي للتهديدات، تملكه حاليًا شركة غوغل" languages="الإنجليزية" cost="تتوفر بعض الميزات في الدرجة المجانية" url="https://www.mandiant.com/multi-vendor-security-platform-free-access" %}}

{{% resource title="(Shodan) العنوان : شودان" description="يعرض معلومات حول الخدمات التي تعمل على خادم بواسطة عنوان بروتوكول إنترنت، ويمكنه أيضًا البحث عن جميع الخوادم التي تعمل على شرائط خدمة معينة" languages="الإنجليزية" cost="تتوفر بعض الميزات في الدرجة المجانية" url="https://en.wikipedia.org/wiki/Banner_grabbing" %}}

{{% resource title="(Shodan) العنوان : شودان" description="يعرض معلومات حول الخدمات التي تعمل على خادم بواسطة عنوان بروتوكول إنترنت، ويمكنه أيضًا البحث عن جميع الخوادم التي تعمل على شرائط خدمة معينة" languages="الإنجليزية" cost="تتوفر بعض الميزات في الدرجة المجانية" url="https://www.shodan.io/" %}}

{{% resource title="(Shodan) العنوان : شودان" description="يعرض معلومات حول الخدمات التي تعمل على خادم بواسطة عنوان بروتوكول إنترنت، ويمكنه أيضًا البحث عن جميع الخوادم التي تعمل على شرائط خدمة معينة" languages="الإنجليزية" cost="تتوفر بعض الميزات في الدرجة المجانية" url="https://help.shodan.io/" %}}

{{% resource title="(Censys Search) سينسيس سيرش" description="أداة يمكنها مراقبة المنافذ المفتوحة وتشغيل الخدمات وشهادات بروتوكول أمان طبقة النقل والمزيد لعنوان بروتوكول إنترنت معين" languages="الإنجليزية" cost="مجانًا" url="https://search.censys.io/" %}}

{{% resource title="(DNS Dumpster)  دي إن إس دمبستر" description="أداة تستخدم للبحث عن أسطح الهجمات المحتملة للخدمات المكشوفة على الإنترنت" languages="الإنجليزية" cost="مجانًا" url="https://dnsdumpster.com/" %}}

{{% resource title="(MX ToolBox) دي إن إس تشكر" description="مجموعة أدوات متعددة لعمليات بحث نظام أسماء المجالات وبروتوكول الإنترنت وتسمح بعمليات بحث سريعة مختلفة على سجلات النطاق/نظام أسماء المجالات وبروتوكول الإنترنت والبريد الإلكتروني" languages="الإنجليزية" cost="مجانًا" url="https://mxtoolbox.com/" %}}

{{% resource title="(DNS Checker) إم إكس تول بوكس" description="مجموعة أدوات متعددة لعمليات بحث نظام أسماء المجالات وبروتوكول الإنترنت وتسمح بعمليات بحث سريعة مختلفة على سجلات النطاق/نظام أسماء المجالات وبروتوكول الإنترنت والبريد الإلكتروني" languages="الإنجليزية" cost="مجانًا" url="https://dnschecker.org/" %}}

{{% resource title="كيفية عمل شفافية الشهادات" description="مقدمة سريعة لماهية شفافية الشهادة والمشكلات التي تعالجها وكيفية عملها" languages="الإنجليزية" cost="مجانًا" url="https://certificate.transparency.dev/howctworks/" %}}

{{% resource title="هدية استخبارات المصادر المفتوحة التي تستمر بالعطاء" description="- دليل للمحللين حول كيفية استخدام أدوات مثل شودان للبحث عن الشهادات والحصول على بيانات جيدة على خوادم الويب التي يحققون فيها" languages="الإنجليزية" cost="مجانًا" url="https://www.osintcurio.us/2019/03/12/certificates-the-osint-gift-that-keeps-on-giving/" %}}

{{% resource title="هدية استخبارات المصادر المفتوحة التي تستمر بالعطاء" description="- دليل للمحللين حول كيفية استخدام أدوات مثل شودان للبحث عن الشهادات والحصول على بيانات جيدة على خوادم الويب التي يحققون فيها" languages="الإنجليزية" cost="مجانًا" url="https://www.youtube.com/watch?v=XHltHamQVoA" %}}

{{% resource title="(crt.sh) موقع سي آر تي دوت إس إش" description="محرك بحث يُركز بشكل خاص على البحث المتعلق بالشهادات" languages="الإنجليزية" cost="مجانًا" url="https://crt.sh/" %}}

{{% resource title="(MassDNS)  ماس دي إن إس" description="أداة يمكن استخدامها لإجراء عمليات بحث بالقوة العمياء للنطاق الفرعي" languages="الإنجليزية" cost="مجانًا" url="https://github.com/blechschmidt/massdns#reconnaissance-by-brute-forcing-subdomains" %}}

{{% resource title="(Advanced Persistent Infrastructure Tracking) - التتبع المتقدم للبنية التحتية التي تستمر في البقاء" description="دليل حول الطرق المختلفة التي يمكن استخدامها لتتبع البنية التحتية للمهاجمين، والذي يبحث أيضًا في عمليات البحث المتعلقة بالشهادات" languages="الإنجليزية" cost="مجانًا" url="https://censys.com/advanced-persistent-infrastructure-tracking/" %}}

<div dir=rtl>
<h1> Git</h1>

<h2>«کنترل نسخه» چیست و چرا باید بدان پرداخت؟</h2>

کنترل نسخه سیستمی است که تغییرات را در فایل یا دسته‌ای از فایل‌ها ذخیره می‌کند و به شما این امکان را می‌دهد که در آینده به نسخه و نگارش خاصی برگردید. برای مثال‌های این کتاب شما از سورس کد نرم‌افزار به عنوان فایل‌هایی که نسخه آنها کنترل می‌شود استفاده می‌کنید. اگرچه در واقع می‌توانید تقریباً از هر فایلی استفاده کنید.

اگر شما یک گرافیست یا طراح وب هستید و می‌خواهید نسخه‌های متفاوت از عکس‌ها و قالب‌های خود داشته باشید (که احتمالاً می‌خواهید)، یک سیستم کنترل نسخه (Version Control System (VCS)) انتخاب خردمندانه‌ای است. یک VCS به شما این امکان را می‌دهد که فایل‌های انتخابی یا کل پروژه را به یک حالت قبلی خاص برگردانید، روند تغییرات را بررسی کنید، ببینید چه کسی آخرین‌بار تغییری ایجاد کرده که احتمالاً مشکل آفرین شده، چه کسی، چه وقت مشکلی را اعلام کرده و…​ استفاده از یک VCS همچنین به این معناست که اگر شما در حین کار چیزی را خراب کردید و یا فایل‌هایی از دست رفت، به سادگی می توانید کارهای انجام شده را بازیابی نمایید. همچنین مقداری سربار به فایل‌های پروژه‌تان افزوده می‌شود.

تفاوت اصلی بین گیت و هر VCS دیگری (ساب‌ورژن و دوستان) در نحوهٔ نگرش گیت به داده‌هایش است. از منظر مفهومی، بیشتر دیگر سیستم‌ها اطلاعات را به عنوان لیستی از تغییرات اعمال شده روی یک فایل پایه ذخیره می‌کنند. این دسته از سیستم‌ها (CVS، ساب‌ورژن، Perforce، Bazaar، و غیره) به اطلاعاتی که ذخیره می‌کنند به عنوان مجموعه‌ای از فایل‌ها و تغییراتی که در طی زمان به آنها اعمال شده می‌نگرند (به طور کل این رفتار کنترل نسخه دلتا-پایه نامیده می‌شود).

گیت به داده یا ذخیره‌کردن آن به این نحو نمی‌نگرد. در عوض، گیت به داده‌هایش بیشتر به مانند یک سری از اسنپ‌شات‌هایی از یک فایل‌سیستم مینیاتوری می‌نگرد. با گیت، هر بار که کامیت (Commit/واگذاری) — یا وضعیت پروژه را ذخیره — می‌کنید، گیت یک تصویر از تمام شمایل فایل‌های شما در آن لحظه می‌گیرد و یک رفرنس را به آن اسنپ‌شات در خود ذخیره می‌کند. برای بهینه بودن، اگر فایل‌ها تغییری نکرده بودند، گیت دیگر آن فایل را ذخیره نمی‌کند و فقط یک لینک به نسخه قبلی عیناً مشابه آن فایل که قبلاً ذخیره کرده بود را جایگزین می‌کند. گیت به داده‌هایش بیشتر به مثل **جریانی از اسنپ‌شات‌ها** می‌نگرد.

این نقطه تمایز مهمی بین گیت و تقریباً تمام دیگر VCSهاست؛ باعث این است که گیت غالب دیدگاه‌های کنترل نسخه را که بیشتر سیستم‌ها از نسل‌های قبل کپی کرده بودند را بازبینی کند. همین اصل گیت را بیشتر یک فایل‌سیستم کوچک با ابزارهای افزودهٔ خارق‌العاده قدرتمند می‌کند تا یک VCS خشک و خالی. اکثر عملیات‌ها در گیت فقط به فایل‌های محلی و منابع نیاز دارند تا کار کنند — عموماً اطلاعاتی از کامپیوتر دیگری روی شبکه شما احتیاج نیست. اگر به یک CVCS دیگر عادت دارید که بیشتر عملیات‌ها آن تأخیر مازاد شبکه را دارند، این جنبه از گیت باعث می‌شود که فکر کنید خدایان سرعت گیت را با قدرت‌های ماورا طبیعی تجهیز کردند. چراکه شما تمام تاریخچه پروژه را همین جا روی هارد ‌دیسک خود دارید، اکثر عملیات‌ها تقریباً درجا انجام می‌شوند.

هر چیزی در گیت قبل از اینکه ذخیره شود چک‌سام می‌شود و سپس متعاقباً با آن چک‌سام فراخوانی می‌شود. این بدان معناست که غیرممکن است که محتوای فایل یا پوشه‌ای را بدون اینکه گیت متوجه شود ویرایش کنید. این کاکرد درون گیت و در پایین‌ترین مرتبه‌ها ساختار یافته و با تاروپود فلسفه‌اش همراه است. ممکن نیست که شما اطلاعات را حین انتقال یا بر اثر خرابی از دست بدهید بدون اینکه گیت آنرا تشخیص دهد.

وقتی که کاری در گیت می‌کنید، تقریباً همه آن افزودن به اطلاعات درون پایگاه‌داده گیت است. به بیان دیگر، انجام کاری که سیستم نتواند آن را بازگردانی کند یا اجبار آن به پاک‌سازی کامل اطلاعات به هر نحو بسیار دشوار است. اما در هر VCS دیگر، شما می‌توانید تغییراتی که هنوز کامیت نکرده‌اید بهم بریزید یا از دست بدهید، اما بعد از اینکه یک اسنپ‌شات به گیت کامیت کردید، از دست دادن آن بسیار مشکل است، بخصوص اگر به طور منظم پایگاه‌داده‌تان را به مخزنی دیگر پوش( Push/هل دادن ) می‌کنید.
</div>
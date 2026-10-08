## git help

ده الامر اللي برجعله لما انسي امر معين بيتكتب ازاي او ال options بتاعته ايه
بدل ما اطلع من ال terminal وادور علي جوجل، ال git نفسه فيه ال documentation كاملة

مثال
انا عايز اشوف command معين زي ال git rebase
```text
git help rebase
```
ده بيفتحلي الشرح الكامل بتاع ال rebase بكل ال options والامثلة
وعشان اخرج منه بدوس q

طب لو مش عايز اقرا كل ده وعايز ملخص سريع؟
```text
git rebase -h
```
ده بيطلعلي ال options في كام سطر جوه ال terminal علي طول

طب لو مش فاكر اسم الامر اصلا؟
```text
git help -a
```
ده بيعرضلي كل اوامر ال git الموجودة

<p>
  <img src="../images/help-1.png" width="29%" />
  <img src="../images/help-2.png" width="29%" />
  <img src="../images/help-3.png" width="29%" />
</p>

## git Clean


ده الامر اللي بيمسحلي  untracked files 
يعني الملفات اللي موجودة في الفولدر بس ال git لسه مش متابعها (معملتلهاش git add قبل كدا)

مثال
انا شغال علي ال order feature وكنت بجرب حاجات، فعملت ملفات مؤقتة زي test.js و debug.log وفولدر temp
خلصت تجربة ومش عايز اي حاجة منهم، وعايز ارجع المشروع نضيف زي ما كان

اول حاجة بشوف هو هيمسح ايه من غير ما يمسح فعلا
```text
git clean -n
```
ده بيعرضلي الملفات اللي هتتمسح بس

لو تمام ومتأكد
```text
git clean -f
```
ده بيمسح الملفات فعلا

طب والفولدرات؟
ال git clean لوحده مش بيمسح فولدرات، لازم ازود -d
```text
git clean -fd
```

طب لو عايز امسح كمان الملفات اللي في ال .gitignore زي node_modules او bin و obj؟
```text
git clean -fdx
```

خلي بالك
الملفات اللي بتتمسح ب git clean مش بتروح ال trash ومش بترجع تاني، عشان كدا لازم اجرب ب -n الاول

صورتين بيوضحوا الملفات اللي هتتمسح ب git clean -n وبعدين المسح الفعلي ب git clean -fd

<p>
  <img src="../images/clean_before.png" width="49%" />
  <img src="../images/clean_after.png" width="49%" />
</p>


## git grep

ده الامر اللي بدور بيه علي كلمة جوه كل ملفات المشروع
وهو بيدور في الملفات اللي ال git متابعها بس، عشان كدا سريع

مثال
انا عايز اغير اسم ال function اللي اسمها createOrder، وقبل ما اغيرها عايز اعرف هي مستخدمة فين
```text
git grep "createOrder"
```
 ده بيطلعلي اسم كل ملف فيه الكلمة ولو عايز رقم السطر بزود -n ولو مش فاكر هي capital ولا small؟ -i

<p>
  <img src="../images/grep.png" width="70%" />
</p>



## git blame

ده الامر اللي بيعرفني كل سطر في الملف مين اللي كتبه وامتي وفي انهي commit

مثال
لقيت سطر في orders.js عامل bug ومش فاهم هو اتكتب ليه
عايز اعرف مين اللي كتبه عشان اسأله
```text
git blame orders.js
```
ده بيطلعلي قدام كل سطر ال commit hash واسم اللي كتبه والتاريخ

طب لو الملف كبير وعايز سطور معينة بس؟
```text
git blame -L 10,20 orders.js
```
ده بيعرضلي من سطر 10 لسطر 20 بس

<p>
  <img src="../images/blame.png" width="70%" />
</p>



## git bisect

الامر دا بيشبه لحد كبير جدا ال binary search tree بيعمل بحث على commit معين كان سبب في حدوث المشكله بعده وعشان يحدد ده  بأقل عدد ممكن من الاختبارات.

مثال

تخيل إنك شغال على مشروع وعندك Feature اسمها Orders.

يوم السبت Orders كانت شغالة تمام ويوم الاثنين اكتشفت إن الـ Orders مش شغالة خلال الفترة دي تم عمل 50 Commit.
دلوقتي إنت عارف إن فيه Commit من الـ 50 دول هو اللي سبب المشكلة

السؤال: هتعرف أنهي Commit سبب المشكلة إزاي؟

ممكن تفتح الـ 50 Commit وتراجعهم واحد واحد، بس ده هياخد وقت كبير.

هنا بييجي دور git bisect  من خلال بعض الاوامر

git bisect start

انا من هنا بقول للgit عايز ابدأ البحث 

git bisect bad

هنا بقوله ان دا الcommit  اللي فيه المشكله 

git bisect good a1b2c3d

هنا بقوله ان دا الcommit دا كان شغال كويس 

git bisect reset

هنا بنهي العمليه كلها وارجع تاني للمكان اللي كنت واقف فيه بعد ما عرف ت المشكله في الcommit 


## git shortlog

ده الامر اللي بيلخصلي ال commits ويجمعها باسم كل واحد في الفريق

مثال
عايز اعرف كل واحد في الفريق عمل كام commit في المشروع
```text
git shortlog -sn
```
ده بيطلعلي اسم كل واحد وقدامه عدد ال commits بتاعته، مترتبين من الاكتر للاقل

<p>
  <img src="../images/shortlog.png" width="70%" />
</p>


## git prune

ده الامر اللي بيمسح ال objects اللي مبقاش في حاجة بتوصلها جوه ال .git
يعني commits مبقتش تبع اي branch وفضلت واخدة مساحة علي الفاضي ولكن في الغالب مش بشغله بايدي، لان git gc بيشغله لوحده وهو بينضف ال repo

مثال
عملت branch للتجربة وعملت عليه commits كتير وبعدين مسحته
ال commits دي لسه موجودة جوه ال .git ومحدش بيستخدمها من خلال الcommands دي بعرف الاول ايه اللي مش محتاجهه وبعد كدا اممسح للتأكيد 
```text
git prune -n #For view Before Delete
git prune    #For delete after Confirm
```

## git worktree

ده الامر اللي بيخليني افتح اكتر من branch في نفس الوقت، كل واحد في فولدر لوحده، من غير ما اعمل clone تاني

مثال
انا في نص شغل ال order feature ومش جاهز اعمل commit، وفجأة جالي bug مستعجل علي ال main
بدل ما اعمل stash واسيب شغلي
```text
git worktree add ../project-hotfix -b hotfix/payment main
```
ده بيعملي فولدر جديد فيه branch جديد من ال main، اصلح فيه ال bug وشغلي الاصلي زي ما هو

اشوف ال worktrees اللي عندي
```text
git worktree list
```
ولما اخلص امسحه
```text
git worktree remove ../project-hotfix
```

<p>
  <img src="../images/worktree.png" width="70%" />
</p>

طبايه الفرق بين switch - worktree

بيعمل ايه git switch

بيغير ال Branch اللي شغال عليه في نفس الفولدر

أما git worktree

بيديك فولدر إضافي تشتغل فيه علىBranch تاني من غير ما تسيب شغلك الأصلي.


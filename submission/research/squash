هيا عملية اقدر من خلالها اعمل دمج لبعض الcommits اللي انا عملتها واخليها كلها تحت commit واحد ودا بيخلي ال git history منظم بشكل افضل 
بس لو جينا نبص علي الsquash هل هو  امر موجود داخل git
لا طبعا 
هيا عمليه بتتنفذ من خلال اوامر تانيه 
مثال 
انا دلوقتي شغال علي order feature 
اول حاجه عملتها اني عملت create order وبعدها عملت commit 
بعد كدا عملت get orders # another Commit 
FIlter Orders 
Sort orders 
وهكذا لحد ما خلصت الfeature كلها وعايز اجمعع كل  اللي انا عملته دا في commit واحد 
Implement Order Feature
اسهل طريقة تكون باستخدام 
git rebase -i HEAD~4
دا بيجيبلي اخر اربعه 
<p>
  <img src="images/before.png" width="49%" />
  <img src="images/after_rebase.png" width="49%" />
</p>
صورتين بيوضوحوا اني كان عندي اربع Commits وتم عملية الدمج لي One Commit 

# LearnCSharp

نکته : IQueryAble یک   GenericList است برای کارکردن با منابع داده که قابلیت Lazy Load را دارد و از Interface IEnumerable ارث بری میکند . IEnumerable  می تواند به تمام فرزندان خود تغییر قیافه دهد یعنی می تواند به List  یا IQuerable یا IOrderQuerable و ... تبدیل شود و به این قاعده Polymorphism گفته میشود (چند ریختی )


<> یکی از مشخصه های Generic List ها است


            List<string> Names = new List<string>();
            Names.Add("Sara");
            Names.Add("Sahar");
            Names.Add("Shayan");
            Names.Add("Shamim");
            Names.Add("Shima");
            Names.Add("Zohre");
            Names.Add("Nastaran");

           // var result = Names.Where(c => c.ToLower().Contains("s")).ToList();
           // var result1 = (from a in Names select a).ToList();
            var result2 = from a in Names select a;
            Names.Add("Sheida");
            foreach (var item in result2)
            {
                Console.WriteLine(item);
            }
            
            Console.ReadKey();
            
            
            همانطور که میدانیم در #C ، کامپایلر کدها را خط به خط اجرا میکند(منظور از خط کدی است که به ; ختم بشود) . پس طبق این قانون، قاعدتا Sheida در خروجی نمی بایست نمایش داده شود. اما اگر خط بالا را اجرا کنید خروجی به صورت زیر خواهد بود
            
            به این خاصیت Lazy Load گفته میشود یعنی خط 
 var result2 = from a in Names select a;
تا زمان اجرا که در کد foreach است فراخوانی نمیشود پس لذا Sheida نیز در خروجی نمایش داده می شود .  و result2 تبدیل به یک Queryable میشود. برای اینکه از sheida در خروجی نمایش داده نشود می بایست از دستور ()toList استفاده کنیم

var result = Names.Where(c => c.ToLower().Contains("s")).ToList();
نکته : توصیه اکید میشود زمانی که میخواهید یک لیست در خروجی نشان دهید بهتر است از خاصیت LazyLoad استفاده کنید که این کار باعث افزایش Performance برنامه میشود . بدلیل اینکه تا لحظه آخر اطلاعات را واکشی نمیکند

مخصوصا اگر کنترلی را میخواهید چک کنید

[1]: https://github.com/mohrmz/OnionArchitecture/blob/main/1.png  "Onion Architecture Layers"
[2]: https://github.com/mohrmz/OnionArchitecture/blob/main/2.png  "Application projects structure"
[3]: https://github.com/mohrmz/OnionArchitecture/blob/main/3.png  "One to One User-UserProfile relationship"
[4]: https://github.com/mohrmz/OnionArchitecture/blob/main/4.png  "User listing"
[5]: https://github.com/mohrmz/OnionArchitecture/blob/main/5.png  "Add User screen"
[6]: https://github.com/mohrmz/OnionArchitecture/blob/main/6.png  "Edit User"
[7]: https://github.com/mohrmz/OnionArchitecture/blob/main/7.png  "Delete User"

<div dir="rtl">
  
# Onion Architecture یا معماری پیاز

در این مخزن کلیه های مفاهیم مرتبط با معماری پیاز توضیح داده می شود و در نهایت با asp.net Core تمامی مفاهیم با کد بیان می شوند تا به صورت کامل با این معماری و مفاهیم آن آشنا شوید و بتوانید از این معماری قدرتمند در برنامه های خود بهره ببرید.
سرفصل های مورد پوشش : 

+ [معرفی](#header1)
+ [Tight Coupling](#header2)
+ [Loose Coupling](#header3)
+ [مزایای معماری Onion](#header4)
+ [چرا باید از معماری onion استفاده کنیم؟](#header5)
+ [لایه های معماری onion](#header6)
+ [ساختار برنامه ها در معماری onion](#header7)
+ [پیاده سازی معماری پیاز](#header8)



___

<div id="header1">
  
# معرفی

</div>

معماری OnionArchitecture در سال 2018 توسط JeffreyPalermo ابداع شد. این معماری روشی مناسب جهت تولید برنامه هایی با قابلیت تست و نگه داری و اطمینان در زیر ساخت های برنامه مانند بانک ها و سرویس ها ارائه می دهد.هدف نهایی این معماری مقابله و رفع مشکلات و چالش های معماری های 3 لایه و n لایه و ارائه راه حل هایی برای مشکلات معمول مانند جفت شدگی یا coupling و جداسازی دغدغه ها یا separation of concerns است. در حال حاضر دو نوع جفت شدگی یا Coupling داریم : tight coupling و loose coupling

<div id="header2">

# Tight Coupling

</div>
  

وقتی یک کلاس دارای وابستگی شدید است گفته می شود که آن کلاس دارای جفت شدگی محکم یا Tight Coupling است.
یک شی جفت شده محکم به یک شی دیگر وابسته است به گونه ای که تغییر در یک کلاس لازمه تغییر در اشیا دیگر را دارد. این مورد برای برنامه های کوچک مشکلی ایجاد نمی کند اما این تغییرات برای برنامه های حرفه ای سخت است.

<div id="header3">
  
# Loose Coupling

</div>

این به این معنا است که دو شی غیر وابسته هستند و یک شی می تواند از یک شی دیگر استفاده کند بدون وابستگی به آن. هدف نهایی این نوع طراحی کم کردن روابط بین اشیا و کامپوننت ها در یک سیستم و کاهش خطر اینکه تغییر در یک شی لازمه تغییرات در اشیا دیگر را داشته باشد.

<div id="header4">
  
# مزایای معماری Onion

</div>

مزایای زیادی برای آن عنوان شده است که شامل : 
1. ارائه نگه داری مناسب به گونه ای که کل کد به لایه ها و مرکز وابسته باشند.
2. .ارائه روشی مناسب برای تست به گونه ای که بتوان برای لایه های گوناگون تست هایی بدون تاثیر بر ماژول های دیگر ایجاد کرد
3. ساخت برنامه ای با جفت شدگی شل به گونه ای که لایه های خارجی برنامه همیشه از طریق رابط ها یا interface ها با لایه های داخلی ارتباط برقرار کنند.
4. .هر گونه القاء واقعی باید در برنامه باید در زمان اجرا ارائه شود
5. موجودیت های دامنه جز اصلی و هسته ای هستند که به لایه های دیتابیس و UI دسترسی دارند.
6. لایه های داخلی به لایه های خارجی وابستگی ندارند و هر کدی که احتمال تغییر دارد باید در لایه خارجی قرار بگیرد.

<div id="header5">
  
# چرا باید از معماری onion استفاده کنیم؟

</div>

تاکنون معماری های سنتی گوناگونی مانند 3 لایه و n لایه معرفی شده اند که هر کدام مزایا و معایب خود را دارند.تمامی این معماری های سنتی یک سری مشکلات پایه ای دارند مانند جفت شدگی محکم یا tight coupling و جداسازی دغدغه ها یا seperation of concern. معماری mvc عموما در معماری برنامه های وب مورد استفاده قرار می گیرد که مشکل جداسازی وابستگی  ها را حل می کند به گونه ای که لایه ارتباطی کاربر و تجاری و دیتا از هم تفکیک می کند. View برای طراحی رابط کاربری ، Model داده ها فراهم شده از لایه تجاری را بین View و Controller انتقال میدهد.
controller مورد استفاده قرار می گیرد تا درخواست های وب را با action method ها مدیریت کند و ویو مناسب را برگرداند.
این معماری مشکل جداسازی دغدغه ها به خوبی انجام می دهد در حالی که controller همجنان برای دسترسی به دیتابیس مورد استفاده قرار می گیرد.MVC ذاتا مشکل separation of concern را حل می کند اما همچنان مشکل جفت شدگی دارد.اما معماری onion هر دو مشکل جداسازی دغدغه ها و جفت شدگی سخت را حل می کند . خلاصه فلسفه این معماری نگه داری منطق تجاری و دیتا و مدل در مرکز برنامه و ارسال وابستگی ها به خارج از آن ها و تا حد ممکن ارسال جفت شدگی ها به مرکز.

<div id="header6">
  
# لایه های معماری onion

</div>

این معماری واسبتگی شدیدی به اصل Dependency Inversion دارد. رابط کاربری با لایه تجاری از طریق رابط ها interface ها ارتباط برقرار می کند.
این معماری شامل 4 لایه است .
1. Domain Entites
2. Repository
3. Service
4. UI(Web/Unit Test)

![Onion Architecture Layers][1]

این لایه ها به سمت مرکز حرکت می کنند . بخش داخلی Domain Entities است که اشیای تجاری و رفتاری را ارائه می دهد.این لایه ها می توانند متفاوت باشند اما domain Entities همیشه در مرکز است و لایه های دیگر رفتار های یک شی را بیان می کنند.

## 1.Domain Entities Layer

در مرکز معماری قرار دارد. کلیه ی اشیا برنامه را نگه داری می کند.اگر برنامه با orm هایی مانند Entity framework توسعه داده شده باشد بنابرین این لایه می تواند شامل POCO کلاس ها در طراحی Code First یا Edmx در طراحی Database First با entity ها یا موجودیت ها باشد.این موجودیت ها هیچ وابستگی ندارند.

## 2. Repository Layer 

این لایه با هدف ایجاد یک لایه انتزاعی بین موجودیت های لایه دامنه و منطق لایه تجاری در یک برنامه ایجاد می شود. این لایه یک الگوی دسترسی به دیتا دارد که تلاش می کند که جفت شدگی کمتری در دسترسی به دیتا ایجاد کند.در این لایه یک Generic Repository ایجاد می شود که منبع داده ای را برای داده ها جستجو می کند  و داده ها را با موجودیت های تجاری ارتباط می دهد و همواره تغییرات را میان موجودیت های تجاری و منبع داده حفظ می کند.

## 3. Service Layer

این لایه رابط ها یا interface ها برای ارتباط بین لایه کاربری و repository را شامل می شود.این لایه منطق تجاری برای یک موجودیت را نگه داری می کند و به همین خاطر به آن  لایه منطق تجاری نیز گفته می شود.

## 4. UI Layer

این لایه خارجی ترین لایه است. این لایه همان Web Application , Web API یا Unit Test است. این لایه اصل وارونه سازی وابستگی ها را پیاده سازی می کند بنابرین برنامه هایی با جفت شدگی شل ایجاد می کند و ارتباط آن با لایه های داخلی تنها با رابط ها یا Interface ها است.

<div id="header7">
  
# ساختار برنامه ها در معماری onion

</div>

جهت پیاده سازی معماری onion از Asp.net Core استفاه شده است و عملیات CRUD را بر روی موجودیت ها نشان می دهد.

![Application projects structure][2]

در این پروژه 3 کتابخانه کلاس و یک برنامه وب وجود دارد که ارتباط هر کدام با معماری پیاز را توضیح می دهیم.

## 1. OA.Data

یک کتابخانه کلاس است که شامل کلاس های POCO و نشان دهنده ی لایه دامنه موجودیت ها یا Domain Entities معماری پیاز است.این کلاس ها در حقیقت برای ساخت جداول دیتابیس استفاده می شوند و بخش مرکزی برنامه است.

## 2. OA.Repo

کتابخانه کلاس دوم شامل یک Generic Repository کلاس و پیاده سازی رابط ها یا interface ها و کلاس DbContext است. Entity FrameWork با الگوی Code First برای دسترسی به داده ها یک کلاس context از Dbcontext ارث بری میکند.

## 3.OA.Service

کتابخانه کلاس سوم نگه دارنده منطق تجاری و رابط ها است.این رابط ها ارتباط بین لایه رابط کاربری و منطق دسترسی دیتا را برقرار می کنند.از آنجایی که از طریق رابط ها ارتباط برقرار می کنند برنامه هایی با جفت شدگی شل ایجاد می کنند. این پروژه نشان دهنده لایه تجاری در معماری پیاز است.

## 4. OA.Web

این پروژه Asp.net Core است که برای ساخت تست های واحد یا Web Api ها مورد استفاده قرار می گیرد.خارجی ترین لایه است  که برای تعامل کاربر با برنامه استفاده می شود و با استفاده از اصل  وارونه سازی وابستگی ها برنامه هایی با جفت شدگی شل ایجاد می کند و معادل لایه UI در معماری پیاز است.

<div id="header8">

# پیاده سازی معماری پیاز

</div>

برای پیاده سازی معماری پیاز این 4 پروژه را ایجاد کنید که نشان دهنده 4 لایه معماری پیاز هستند.

# Domain Entities Layer

Domain Entities بخش مرکزی و در اصل هسته معماری پیاز است.بنابرین پروژه OA.Data را ایجاد می کنیم تا این لایه را پیاده سازی کنیم. این پروژه برای نگه داری کلاس های POCO است.در این لایه 3 موجودیت و یک کلاس پایه به نامBaseEntity تعریف شده است و پراپرتی های آن را ارث بری می کنند.

</div>

```Csharp

using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Threading.Tasks;  
  
namespace OA.Data  
{  
    public class BaseEntity  
    {  
        public Int64 Id { get; set; }  
        public DateTime AddedDate { get; set; }  
        public DateTime ModifiedDate { get; set; }  
        public string IPAddress { get; set; }  
    }  
}  

```

<div dir="rtl">
  
همچنین شامل دو موجودیت دیگه به نام User و UserProfile است که هر دو از BaseEntity  ارث بری می کنند.

</div>


![One to One User-UserProfile relationship][3]

```Csharp

namespace OA.Data  
{  
    public class User:BaseEntity  
    {  
        public string UserName { get; set; }  
        public string Email { get; set; }  
        public string Password { get; set; }  
        public virtual UserProfile UserProfile { get; set; }  
    }  
}  

```

```Csharp

using Microsoft.EntityFrameworkCore.Metadata.Builders;  
  
namespace OA.Data  
{  
    public class UserMap  
    {  
        public UserMap(EntityTypeBuilder<User> entityBuilder)  
        {  
            entityBuilder.HasKey(t => t.Id);  
            entityBuilder.Property(t => t.Email).IsRequired();  
            entityBuilder.Property(t => t.Password).IsRequired();  
            entityBuilder.Property(t => t.Email).IsRequired();  
            entityBuilder.HasOne(t => t.UserProfile).WithOne(u => u.User).HasForeignKey<UserProfile>(x => x.Id);  
        }  
    }  
}  

```

```Csharp

namespace OA.Data  
{  
    public class UserProfile:BaseEntity  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public string Address { get; set; }  
        public virtual User User { get; set; }  
    }  
}  

```


```Csharp

using Microsoft.EntityFrameworkCore.Metadata.Builders;  
  
namespace OA.Data  
{  
    public class UserProfileMap  
    {  
        public UserProfileMap(EntityTypeBuilder<UserProfile> entityBuilder)  
        {  
            entityBuilder.HasKey(t => t.Id);  
            entityBuilder.Property(t => t.FirstName).IsRequired();  
            entityBuilder.Property(t => t.LastName).IsRequired();  
            entityBuilder.Property(t => t.Address);    
        }  
    }  
}  

```

<div dir="rtl">
  
  # لایه Repository
  
  حالا لایه دوم از معماری پیاز را ایجاد می کنیم که همان لایه Repository است.برای ساخت این لایه ما یک کتابخانه کلاس به نام OA.Repo ایجاد می کنیم که مخرن و داده و کلاس های context را نگه داری می کند.
  
  پروژه OA.Repo شامل DataContext است. ADO.NET Entity Framework Code First برای دسترسی به داده به یک کلاس context که از DBCOntext ارث بری می کند نیاز دارد بنابرین کلاس ApplicationContext را ایجاد می کنیم
  
  در این کلاس متد OnModelCreating() را باز نویسی می کنیم . این متد زمان نمونه سازی اولیه کلاس context فراخوانی می شود 
  
    
</div>
  
  ```Csharp
  
  using Microsoft.EntityFrameworkCore;  
using OA.Data;  
  
namespace OA.Repo  
{  
    public class ApplicationContext : DbContext  
    {  
        public ApplicationContext(DbContextOptions<ApplicationContext> options) : base(options)  
        {  
        }  
        protected override void OnModelCreating(ModelBuilder modelBuilder)  
        {  
            base.OnModelCreating(modelBuilder);  
            new UserMap(modelBuilder.Entity<User>());  
            new UserProfileMap(modelBuilder.Entity<UserProfile>());  
        }  
    }  
} 


sing OA.Data;  
using System.Collections.Generic;  
  
namespace OA.Repo  
{  
    public interface IRepository<T> where T : BaseEntity  
    {  
        IEnumerable<T> GetAll();  
        T Get(long id);  
        void Insert(T entity);  
        void Update(T entity);  
        void Delete(T entity);  
        void Remove(T entity);  
        void SaveChanges();  
    }  
}  


using Microsoft.EntityFrameworkCore;  
using OA.Data;  
using System;  
using System.Collections.Generic;  
using System.Linq;  
  
namespace OA.Repo  
{  
    public class Repository<T> : IRepository<T> where T : BaseEntity  
    {  
        private readonly ApplicationContext context;  
        private DbSet<T> entities;  
        string errorMessage = string.Empty;  
  
        public Repository(ApplicationContext context)  
        {  
            this.context = context;  
            entities = context.Set<T>();  
        }  
        public IEnumerable<T> GetAll()  
        {  
            return entities.AsEnumerable();  
        }  
  
        public T Get(long id)  
        {  
            return entities.SingleOrDefault(s => s.Id == id);  
        }  
        public void Insert(T entity)  
        {  
            if (entity == null)  
            {  
                throw new ArgumentNullException("entity");  
            }  
            entities.Add(entity);  
            context.SaveChanges();  
        }  
  
        public void Update(T entity)  
        {  
            if (entity == null)  
            {  
                throw new ArgumentNullException("entity");  
            }  
            context.SaveChanges();  
        }  
  
        public void Delete(T entity)  
        {  
            if (entity == null)  
            {  
                throw new ArgumentNullException("entity");  
            }  
            entities.Remove(entity);  
            context.SaveChanges();  
        }  
        public void Remove(T entity)  
        {  
            if (entity == null)  
            {  
                throw new ArgumentNullException("entity");  
            }  
            entities.Remove(entity);              
        }  
  
        public void SaveChanges()  
        {  
            context.SaveChanges();  
        }  
    }  
}  


  ```


<div dir="rtl">
  
  # لایه Service
  
  سومین لایه که همان لایه سرویس است و پروژه دیگری به نام OA.Service ایجاد می کنیم که شامل interface و پیاده سازی آن ها و رابطی است بین لایه UI و Repository تا جفت شدگی را کاهش دهد 
  
 </div>

```Csharp

using OA.Data;  
using System.Collections.Generic;  
  
namespace OA.Service  
{  
    public  interface IUserService  
    {  
        IEnumerable<User> GetUsers();  
        User GetUser(long id);  
        void InsertUser(User user);  
        void UpdateUser(User user);  
        void DeleteUser(long id);  
    }  
}  

using OA.Data;  
using OA.Repo;  
using System.Collections.Generic;  
  
namespace OA.Service  
{  
    public class UserService:IUserService  
    {  
        private IRepository<User> userRepository;  
        private IRepository<UserProfile> userProfileRepository;  
  
        public UserService(IRepository<User> userRepository, IRepository<UserProfile> userProfileRepository)  
        {  
            this.userRepository = userRepository;  
            this.userProfileRepository = userProfileRepository;  
        }  
  
        public IEnumerable<User> GetUsers()  
        {  
            return userRepository.GetAll();  
        }  
  
        public User GetUser(long id)  
        {  
            return userRepository.Get(id);  
        }  
  
        public void InsertUser(User user)  
        {  
            userRepository.Insert(user);  
        }  
        public void UpdateUser(User user)  
        {  
            userRepository.Update(user);  
        }  
  
        public void DeleteUser(long id)  
        {              
            UserProfile userProfile = userProfileRepository.Get(id);  
            userProfileRepository.Remove(userProfile);  
            User user = GetUser(id);  
            userRepository.Remove(user);  
            userRepository.SaveChanges();  
        }  
    }  
}  

using OA.Data;  
  
namespace OA.Service  
{  
    public interface IUserProfileService  
    {  
        UserProfile GetUserProfile(long id);  
    }  
}  

using OA.Data;  
using OA.Repo;  
  
namespace OA.Service  
{  
    public class UserProfileService: IUserProfileService  
    {  
        private IRepository<UserProfile> userProfileRepository;  
  
        public UserProfileService(IRepository<UserProfile> userProfileRepository)  
        {             
            this.userProfileRepository = userProfileRepository;  
        }  
  
        public UserProfile GetUserProfile(long id)  
        {  
            return userProfileRepository.Get(id);  
        }  
    }  
}  

```



لینک اصلی محتوا [Onion Architecture](https://www.c-sharpcorner.com/article/onion-architecture-in-asp-net-core-mvc/)

</div>

# CodeSummary_LiveProject
Tech Academy C# Live Project Code Summary
<h1>Introduction</h1>
For the final two weeks of my time at the Tech Academy, I worked on a team with my fellow students to help develop a new content management system(CMS) for a local theatre/acting company's website. This project was built with ASP .NET MVC and Entity Framework using C#. This interactive MVC web application allows the managing of content for users who are not techincally savy and want to easily manage what displays on their website. For this project we utilized an Agile work environment in Azure DevOps and SCRUM processes, which  involved daily standups and weekly code retrospectives during the two week sprint. 
<h3>Table of Contents</h3>
* Designing the About page<br>
* Creating entity Model and CRUD pages<br>
* Styling CRUD Pages<br>
* Conclusion<br>
<h1>Designing the About page</h1>
For this story, I was assigned the task of designing the About page for the Vertigo Theatre web application. I utilized Bootstrap cards to display the pictures and names of the Ensemble for a clean look. I also utilized varying Bootstrap column sizes to ensure proper format for different screen sizes. During this project it was imperitive to adhere to the defined naming convention for custom CSS classes and to also not override any Bootstrap classes.




```C#
<div class="aboutPage-Mission">
  <h1 class="aboutPage-h1">Mission Statement</h1>
  <p>We seek to engage audiences through compelling, ensemble-driven productions<br /> with a focus on developing new works.</p>
</div>

<div>
  <h1 class="aboutPage-h1">Ensemble</h1>
  <div class="card-deck">
    <div class="card aboutPage-Card">
      <img class="card-img-top aboutPage-Card-Img"  src="@Url.Content("~/Content/images/Cast_Img_1.jpg")" alt="Kaia Maarja Hillier">
      <div class="card-body aboutPage-Card-Bdy">
        <p class="card-text aboutPage-Card-Text">Kaia<br /> Maarja Hillier</p>
      </div>
    </div>
    <div class="card aboutPage-Card">
      <img class="card-img-top aboutPage-Card-Img" src="@Url.Content("~/Content/images/Cast_Img_7.jpg")" alt="Tom Mounsey">
      <div class="card-body aboutPage-Card-Bdy ">
        <p class="card-text aboutPage-Card-Text">Tom <br />Mounsey</p>
      </div>
    </div>
    <div class="card aboutPage-Card">
      <img class="card-img-top aboutPage-Card-Img" src="@Url.Content("~/Content/images/Cast_Img_3.jpg")" alt="Heath Hyun Houghton">
      <div class="card-body aboutPage-Card-Bdy">
        <p class="card-text aboutPage-Card-Text">Heath<br /> Hyun Houghton</p>
      </div>
    </div>
    <div class="card aboutPage-Card">
      <img class="card-img-top aboutPage-Card-Img" src="@Url.Content("~/Content/images/Cast_Img_4.jpg")" alt="Jacquelle Davis">
      <div class="card-body aboutPage-Card-Bdy">
        <p class="card-text aboutPage-Card-Text">Jaquelle <br />Davis</p>
      </div>
    </div>
    <div class="card aboutPage-Card">
      <img class="card-img-top aboutPage-Card-Img" src="@Url.Content("~/Content/images/Cast_Img_6.jpg")" alt="Victoria Alvarez-Chacon">
      <div class="card-body aboutPage-Card-Bdy">
        <p class="card-text aboutPage-Card-Text">Victoria<br /> Alvarez-Chacon</p>
      </div>
    </div>
  </div>
</div>



<div class="aboutPage-Board">
  <h1 class="aboutPage-h1">Board</h1>
  <p>
    Jamie Floyd (President)<br /> Scott Stephens <br />Marcia Reyes <br />Lena-Liis Kiesel
  </p>
</div>

<div class="aboutPage-History ">
  <h1 class="aboutPage-h1">Company History</h1>
  <p>
    In 1997, Theatre Vertigo was founded by Paul Floding, Nanette Pettit and Jeff Meyers.  Since then, Theatre Vertigo has performed in numerous spaces including The Russell Street Theater, The Electric Company, Theater!Theatre!, and their current home, The Shoebox Theater.<br />

    From 2003 to 2014, Theatre Vertigo produced Anonymous Theatre as a summer fundraiser in collaboration with The Anonymous Theatre Company.  Other past collaborations include defunkt theatre, Stark Raving Theater, and Tears of Joy Theatre.<br />

    Theatre Vertigo has worked on world premieres including Faust.Us by Joseph Fisher, 99 Ways to Fuck a Swan by Kim Rosenstock, and The End of Sex by Craig Jessen.
    <br />
    In 2016, Theatre Vertigo produced its first officially commissioned work from a playwright, I Want To Destroy You, by Rob Handel.
  </p>
</div>
```



<h3>Defined Color Theme For Project</h3>



```CSS
 CSS color variables 
:root { /* Color palette for css 
    --main-bg-color: #DB1A11;  Red 
    --main-secondary-color: #F04D44;  Red, a shade lighter 
    --secondary-color: #D6972A;  Yellow gold 
    --light-color: #FFFBFB;  White 
    --dark-color: #000000;  Black 
    --subscriber-main: #9D7C39;  Dark Gold 
}*/
```




```CSS
/*Adding CSS for Theatre Vertigo About page*/
.aboutPage-Card-Img {
    width: auto;
    max-width: 100%;
    height: 75%;
    object-fit: cover;
}
.aboutPage-Card-Img:hover {
    background-color: var(--dark-color);
    opacity: .8;
    transition: .15s;
}
.aboutPage-Card:hover {
    border-color: var(--secondary-color);
    border-style: double;
}
.aboutPage-Card-Bdy {
    background-color: var(--dark-color);
}
.aboutPage-Card-Text {
    text-align: center;
    color: var(--light-color);
}
.aboutPage-History {
    text-align: left;
    color: var(--light-color);
    padding: 40px;
}
.aboutPage-Board {
    text-align:center;
    color: var(--light-color);
    padding: 40px;
}
.aboutPage-Mission {
    text-align: center;
    color: var(--light-color);
    padding: 40px;

}
.aboutPage-h1 {
    color: var(--main-bg-color);
    text-align: center;
    padding: 15px;
    text-decoration: underline;
    font-weight: bold;
    text-decoration-color: var(--secondary-color);
}
```







<h1>Creating entity Model and CRUD pages</h1>
For the next story I was assigned the task of creating an entity model of a Cast Member with defined properties and value types. I used a code first approach-- creating my model in code before actually creating the model. I was also tasked with implementing a Position enum for the Main Role property. I also commented out the Photo property with Byte[] array value type before building model and updating database as it was going to be used in a later story. 




```C#
namespace TheatreCMS3.Areas.Production.Models
{
    public enum PositionEnum
    {
        Actor,
        Director,
        StageManager,
        Technician,
        Other        
    }
    public class CastMember
    {
        [Key]
        public int CastMemberId { get; set; }
        public string Name { get; set; }
        public int? YearJoined { get; set; }
        public PositionEnum MainRole { get; set; }
        public string Bio { get; set; }
        //public byte[] Photo { get; set; }
        public bool CurrentMember { get; set; }
        public string Character { get; set; }
        public int? CastYearLeft { get; set; }
        public int? DebutYear { get; set; }
    }
}
```
Scaffolding the CRUD pages via Controller
Here I used the power of Entity Framework to scaffold my Cast Member controller and create CRUD functionality.




```C#
namespace TheatreCMS3.Areas.Production.Controllers
{
    public class CastMembersController : Controller
    {
        private ApplicationDbContext db = new ApplicationDbContext();

        // GET: Production/CastMembers
        public ActionResult Index()
        {
            return View(db.CastMembers.ToList());
        }

        // GET: Production/CastMembers/Details/5
        public ActionResult Details(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            CastMember castMember = db.CastMembers.Find(id);
            if (castMember == null)
            {
                return HttpNotFound();
            }
            return View(castMember);
        }

        // GET: Production/CastMembers/Create
        public ActionResult Create()
        {
            return View();
        }

        // POST: Production/CastMembers/Create
        // To protect from overposting attacks, enable the specific properties you want to bind to, for 
        // more details see https://go.microsoft.com/fwlink/?LinkId=317598.
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Create([Bind(Include = "CastMemberId,Name,YearJoined,MainRole,Bio,CurrentMember,Character,CastYearLeft,DebutYear")] CastMember castMember)
        {
            if (ModelState.IsValid)
            {
                db.CastMembers.Add(castMember);
                db.SaveChanges();
                return RedirectToAction("Index");
            }

            return View(castMember);
        }

        // GET: Production/CastMembers/Edit/5
        public ActionResult Edit(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            CastMember castMember = db.CastMembers.Find(id);
            if (castMember == null)
            {
                return HttpNotFound();
            }
            return View(castMember);
        }

        // POST: Production/CastMembers/Edit/5
        // To protect from overposting attacks, enable the specific properties you want to bind to, for 
        // more details see https://go.microsoft.com/fwlink/?LinkId=317598.
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Edit([Bind(Include = "CastMemberId,Name,YearJoined,MainRole,Bio,CurrentMember,Character,CastYearLeft,DebutYear")] CastMember castMember)
        {
            if (ModelState.IsValid)
            {
                db.Entry(castMember).State = EntityState.Modified;
                db.SaveChanges();
                return RedirectToAction("Index");
            }
            return View(castMember);
        }

        // GET: Production/CastMembers/Delete/5
        public ActionResult Delete(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            CastMember castMember = db.CastMembers.Find(id);
            if (castMember == null)
            {
                return HttpNotFound();
            }
            return View(castMember);
        }

        // POST: Production/CastMembers/Delete/5
        [HttpPost, ActionName("Delete")]
        [ValidateAntiForgeryToken]
        public ActionResult DeleteConfirmed(int id)
        {
            CastMember castMember = db.CastMembers.Find(id);
            db.CastMembers.Remove(castMember);
            db.SaveChanges();
            return RedirectToAction("Index");
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
}
```


<h1>Styling Crud Pages</h1>
I was assigned the task of styling the recently created CRUD pages for the Cast Member model. 



```C#
@model TheatreCMS3.Areas.Production.Models.CastMember

@{
    ViewBag.Title = "Create";
}

<h1 class="cast_member-create--h1">Create Cast Member</h1>

<div class="cast_member-create--form_container col-12 col-sm-12 col-md-8 col-lg-6">
@using (Html.BeginForm()) 
{
    @Html.AntiForgeryToken()
    
    <div class="form-horizontal cast_member-create--form">
        <h4 class="cast_member-create--h4">Add New Cast Member</h4>
        <hr />
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })
        <div class="form-group">
            @Html.LabelFor(model => model.Name, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.EditorFor(model => model.Name, new { htmlAttributes = new { @class = "form-control cast_member-create--form_group", placeholder= "Enter Full Name" } })
                @Html.ValidationMessageFor(model => model.Name, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group">
            @Html.LabelFor(model => model.YearJoined, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.EditorFor(model => model.YearJoined, new { htmlAttributes = new { @class = "form-control cast_member-create--form_group", placeholder="Enter Year Joined" } })
                @Html.ValidationMessageFor(model => model.YearJoined, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group">
            @Html.LabelFor(model => model.MainRole, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.EnumDropDownListFor(model => model.MainRole, htmlAttributes: new { @class = "form-control cast_member-create--form_group" })
                @Html.ValidationMessageFor(model => model.MainRole, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group">
            @Html.LabelFor(model => model.Bio, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.TextAreaFor(model => model.Bio, new { @class = "form-control cast_member-create--bio_form_group", placeholder = "Enter short bio" })
                @Html.ValidationMessageFor(model => model.Bio, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group cast_member-create--current_member">
            @Html.LabelFor(model => model.CurrentMember, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                <div class="check-box">
                    @Html.EditorFor(model => model.CurrentMember)
                    @Html.ValidationMessageFor(model => model.CurrentMember, "", new { @class = "text-danger" })
                </div>
            </div>
        </div>

        <div class="form-group">
            @Html.LabelFor(model => model.Character, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.EditorFor(model => model.Character, new { htmlAttributes = new { @class = "form-control cast_member-create--form_group", placeholder = "Enter Character Name" } })
                @Html.ValidationMessageFor(model => model.Character, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group">
            @Html.LabelFor(model => model.CastYearLeft, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.EditorFor(model => model.CastYearLeft, new { htmlAttributes = new { @class = "form-control cast_member-create--form_group", placeholder = "Enter Year Left" } })
                @Html.ValidationMessageFor(model => model.CastYearLeft, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group">
            @Html.LabelFor(model => model.DebutYear, htmlAttributes: new { @class = "control-label col-md-8" })
            <div class="col-md-12">
                @Html.EditorFor(model => model.DebutYear, new { htmlAttributes = new { @class = "form-control cast_member-create--form_group", placeholder = "Enter Debut Year" } })
                @Html.ValidationMessageFor(model => model.DebutYear, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="row justify-content-around">
          <div class="form-group cast_member-create--submit_btn">
              <input type="submit" value="Create" class="btn btn-default" />
          </div>
              @Html.ActionLink("Back to List", "Index", null, new { @class = "btn btn-default cast_member-create--back_btn " })
        </div>
    </div>
    
}
</div>


@section Scripts {
    @Scripts.Render("~/bundles/jqueryval")
}
```



```C#
.cast_member-create--h1 {
    text-align: center;
    color: var(--light-color);
    padding: 30px;
}
.cast_member-create--h4 {
    text-align: center;
    color: var(--dark-color);
    padding: 30px;
}

.cast_member-create--form_container {
    text-align: center;
    border: solid 20px;
    border-radius: 25px;
    border-color: var(--main-bg-color);
    background-color: var(--light-color);
    margin-left: auto;
    margin-right: auto;
}
.cast_member-create--form {
    text-align: left;
}
.cast_member-create--current_member {
    text-align: center;
    padding: 20px;
}
.cast_member-create--submit_btn {
    text-align: center;
    background-color: var(--main-bg-color);
    border-radius: 10px;
    width: auto;
    margin-top: 50px;
    padding: 10px;
    
}
.cast_member-create--submit_btn:hover {
    opacity: .8;
}
.check-box {
    text-align: center;
}
.cast_member-create--back_btn {
    margin-top: 50px;
    text-align: center;
    background-color: var(--secondary-color);
    border-radius: 10px;
    padding: 10px;
    width: auto;
    margin-bottom: 15px;
}
.cast_member-create--back_btn:hover {
    opacity: .8;
}
.cast_member-create--form_group {
    background-color: lightgrey;
    border: 2px solid var(--dark-color);
    outline: none;
    width: 100%;
    text-align: left;
    margin: auto;
    margin: auto;
}
.cast_member-create--bio_form_group, textarea {
    background-color: lightgrey;
    border: 2px solid var(--dark-color);
    outline: none;
    width: 100%;
    margin-left: auto;
    margin-right: auto;
}
.cast_member-create--form_group:focus, textarea:focus {
    border: 2px solid var(--secondary-color);
    box-shadow: 0 0 3px var(--secondary-color);
    color: var(--main-secondary-color);
    background-color: rgba(204, 238, 255, .9);
}
.cast_member-create--bio_form_group:focus, textarea:focus {
    border: 2px solid var(--secondary-color);
    box-shadow: 0 0 3px var(--secondary-color);
    color: var(--main-secondary-color);
    background-color: rgba(204, 238, 255, .9);
}
```


<h1>Conclusion</h1>
This live project was an invaluable opportunity to really test myself and get a glimpse of what an Agile work environment looks like. I gained experience with ASP .NET MVC, creating a code first model web application and subsequent views with CRUD functionality via the controller. I learned more about utilizing bootstrap in my project to ensure proper resposiveness to different screen sizes(ie mobile vs laptop). I also learned the importance of naming conventions when working on a large group project. Working with a group of developers over the  course of project and being able to have daily standups in which we discussed the previous days work, roadblocks/breakthroughs, current workflow and general questions was a great way to communicate and learn from my fellow students. Overall, I really relished the real world experience that this Live Project provided me and look forward to applying what I have learned in the future. 

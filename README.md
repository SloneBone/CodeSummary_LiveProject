# CodeSummary_LiveProject
Tech Academy C# Live Project Code Summary
<h1>Introduction</h1>
For the final two weeks of my time at the Tech Academy, I worked on a team with my fellow students to help develop a new content management system(CMS) for a local theatre/acting company's website. This project was built with ASP .NET MVC and Entity Framework using C#. This interactive MVC web application allows the managing of content for users who are not techincally savy and want to easily manage what displays on their website. For this project we utilized an Agile work environment in Azure DevOps and SCRUM processes, which  involved daily standups and weekly code retrospectives during the two week sprint. 
Table of Contents
1. Designing the About page
2. Creating entity Model and CRUD pages
3. Styling CRUD Pages
<h1>Designing the About page</h1>
For this story, I was assigned the task of designing the About page for the Vertigo Theatre web application. I utilized Bootstrap cards to display the pictures and names of the Ensemble for a clean look. I also utilized varying Bootstrap column sizes to ensure proper format for different screen sizes. 




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








<h1>Creating entity Model and CRUD pages</h1>





<h1>Styling Crud Pages</h1>






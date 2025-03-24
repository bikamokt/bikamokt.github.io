
# 20 ASP.NET Snippets for Frontend Development Using Razor and ASP.NET MVC/Views

---

### 1. Display Current Date in Razor View
```razor
<p>Today's Date: @DateTime.Now.ToString("MMMM dd, yyyy")</p>
###2. Simple Form in Razor with Model Binding
razor
Copy
Edit
@model MyApp.Models.UserModel

<form asp-action="SaveUser" method="post">
    <label>Name:</label>
    <input type="text" asp-for="Name" class="form-control" />
    <span asp-validation-for="Name" class="text-danger"></span>

    <button type="submit" class="btn btn-primary">Submit</button>
</form>
###3. Render a Partial View
razor
Copy
Edit
@Html.Partial("_UserDetails", Model)
or

razor
Copy
Edit
@await Html.PartialAsync("_UserDetails", Model)
###4. Iterate Over a List in Razor
razor
Copy
Edit
@foreach (var user in Model.Users)
{
    <p>@user.Name - @user.Email</p>
}
###5. Conditional Rendering in Razor
razor
Copy
Edit
@if (User.Identity.IsAuthenticated)
{
    <p>Welcome, @User.Identity.Name</p>
}
else
{
    <a href="/Account/Login">Login</a>
}
###6. Using ViewBag to Pass Data
razor
Copy
Edit
<h1>@ViewBag.Title</h1>
<p>@ViewBag.Message</p>
###7. Using ViewData to Pass Data
razor
Copy
Edit
<h1>@ViewData["PageTitle"]</h1>
<p>@ViewData["Description"]</p>
###8. Strongly Typed View with Model Data
razor
Copy
Edit
@model MyApp.Models.Product

<h2>Product Details</h2>
<p>Name: @Model.Name</p>
<p>Price: $@Model.Price</p>
###9. Tag Helper for Image in Razor
razor
Copy
Edit
<img asp-append-version="true" src="~/images/logo.png" alt="Logo" />
###10. ASP.NET Core Input Validation
razor
Copy
Edit
<input type="email" asp-for="Email" class="form-control" />
<span asp-validation-for="Email" class="text-danger"></span>
###11. Create a Drop-down List in Razor
razor
Copy
Edit
@Html.DropDownListFor(m => m.SelectedCategory, 
    new SelectList(Model.Categories, "Id", "Name"), 
    "Select Category", 
    new { @class = "form-control" })
###12. Render a Component Dynamically
razor
Copy
Edit
<vc:recent-products></vc:recent-products>
###13. AJAX Call in Razor View
html
Copy
Edit
<button id="loadData">Load Data</button>
<div id="result"></div>

<script>
    document.getElementById("loadData").addEventListener("click", function () {
        fetch('/Home/GetData')
            .then(response => response.text())
            .then(data => document.getElementById("result").innerHTML = data);
    });
</script>
###14. Using TempData to Pass Data Between Actions
razor
Copy
Edit
<p>@TempData["Message"]</p>
###15. Display Validation Messages in Razor
razor
Copy
Edit
@Html.ValidationSummary(true, "", new { @class = "text-danger" })
###16. Render JSON Object in Razor
razor
Copy
Edit
@using Newtonsoft.Json

<script>
    var modelData = @Html.Raw(JsonConvert.SerializeObject(Model));
    console.log(modelData);
</script>
###17. Razor Syntax for Setting CSS Class Dynamically
razor
Copy
Edit
<p class="@(Model.IsActive ? "text-success" : "text-danger")">
    @(Model.IsActive ? "Active" : "Inactive")
</p>
###18. Display User Claims in Razor
razor
Copy
Edit
@using System.Security.Claims

@{
    var user = Context.User;
    var userId = user.FindFirst(ClaimTypes.NameIdentifier)?.Value;
    var userEmail = user.FindFirst(ClaimTypes.Email)?.Value;
}

<p>User ID: @userId</p>
<p>Email: @userEmail</p>
###19. Prevent CSRF in Forms
razor
Copy
Edit
<form asp-action="Submit" method="post">
    @Html.AntiForgeryToken()
    <button type="submit">Submit</button>
</form>
###20. Create a Table Dynamically
razor
Copy
Edit
<table class="table">
    <thead>
        <tr>
            <th>Name</th>
            <th>Email</th>
        </tr>
    </thead>
    <tbody>
        @foreach (var user in Model.Users)
        {
            <tr>
                <td>@user.Name</td>
                <td>@user.Email</td>
            </tr>
        }
    </tbody>
</table>
These snippets provide a great starting point for frontend development using Razor and ASP.NET MVC/Views. They cover a range of common tasks such as rendering views, form handling, validation, and data binding.

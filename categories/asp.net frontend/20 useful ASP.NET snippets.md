# ASP.NET Razor Snippet Collection

This document provides a collection of useful ASP.NET Razor snippets for front-end development. Each snippet is linked to its corresponding section for easy navigation.

## Table of Contents

1.  [Basic Layout Structure](#basic-layout-structure)
2.  [Rendering Partial Views](#rendering-partial-views)
3.  [Displaying Data in a Table](#displaying-data-in-a-table)
4.  [Creating a Form with Input Fields](#creating-a-form-with-input-fields)
5.  [Dropdown List (Select)](#dropdown-list-select)
6.  [Radio Buttons](#radio-buttons)
7.  [Checkboxes](#checkboxes)
8.  [Displaying Images](#displaying-images)
9.  [Conditional Rendering](#conditional-rendering)
10. [Looping Through a List](#looping-through-a-list)
11. [Displaying Validation Messages](#displaying-validation-messages)
12. [Using `@Html.ActionLink` for Navigation](#htmlactionlink-for-navigation)
13. [Generating URLs with `@Url.Action`](#urdaction-generating-urls)
14. [Working with Sections](#working-with-sections)
15. [Using `@Html.AntiForgeryToken`](#htmlantiforgerytoken)
16. [Displaying Date and Time](#displaying-date-and-time)
17. [Creating a Simple Modal](#creating-a-simple-modal)
18. [Implementing a Navigation Menu](#implementing-a-navigation-menu)
19. [Dynamic CSS Classes](#dynamic-css-classes)
20. [Displaying Raw HTML](#displaying-raw-html)
21. [Using `@Html.DisplayFor` and `@Html.EditorFor`](#htmldisplayforeditorfor)

## Snippets

### 1. Basic Layout Structure <a id="basic-layout-structure"></a>

```
<!DOCTYPE html>
<html>
<head>
    <title>@ViewBag.Title</title>
    <link rel="stylesheet" href="~/css/site.css" />
</head>
<body>
    <header>
        </header>

    <main>
        @RenderBody()
    </main>

    <footer>
        </footer>

    <script src="~/js/site.js"></script>
</body>
</html>

### 2. Rendering Partial Views <a id="rendering-partial-views"></a>

```
@await Html.PartialAsync("_PartialViewName")

###  3. Displaying Data in a Table <a id="displaying-data-in-a-table"></a>

```
<table>
    <thead>
        <tr>
            <th>Column 1</th>
            <th>Column 2</th>
        </tr>
    </thead>
    <tbody>
        @foreach (var item in Model)
        {
            <tr>
                <td>@item.Property1</td>
                <td>@item.Property2</td>
            </tr>
        }
    </tbody>
</table>

### 4. Creating a Form with Input Fields <a id="creating-a-form-with-input-fields"></a>

```
<form method="post" action="/YourController/YourAction">
    <label for="inputField">Input:</label>
    <input type="text" id="inputField" name="inputField" />
    <button type="submit">Submit</button>
</form>

### 5. Dropdown List (Select) <a id="dropdown-list-select"></a>

```
<select name="selectField">
    @foreach (var item in ViewBag.SelectList)
    {
        <option value="@item.Value">@item.Text</option>
    }
</select>

### 6. Radio Buttons <a id="radio-buttons"></a>

```
@foreach (var item in ViewBag.RadioList)
{
    <input type="radio" id="@item.Value" name="radioGroup" value="@item.Value" />
    <label for="@item.Value">@item.Text</label><br />
}

### 7. Checkboxes <a id="checkboxes"></a>
```

@foreach (var item in ViewBag.CheckboxList)
{
    <input type="checkbox" id="@item.Value" name="checkboxGroup" value="@item.Value" />
    <label for="@item.Value">@item.Text</label><br />
}

###  8. Displaying Images <a id="displaying-images"></a>
```

<img src="~/images/yourImage.jpg" alt="Your Image" />

### 9. Conditional Rendering <a id="conditional-rendering"></a>
```

@if (Model.Condition)
{
    <p>Condition is true.</p>
}
else
{
    <p>Condition is false.</p>
}

### 10. Looping Through a List <a id="looping-through-a-list"></a>
```
<ul>
    @foreach (var item in Model.Items)
    {
        <li>@item.Name</li>
    }
</ul>

### 11. Displaying Validation Messages <a id="displaying-validation-messages"></a>
```
@Html.ValidationSummary(true, "", new { @class = "text-danger" })
@Html.ValidationMessageFor(model => model.Property, "", new { @class = "text-danger" })

### 12. Using @Html.ActionLink for Navigation <a id="htmlactionlink-for-navigation"></a>
```

@Html.ActionLink("Link Text", "ActionName", "ControllerName", new { id = Model.Id }, null)

### 13. Generating URLs with @Url.Action <a id="urdaction-generating-urls"></a>
```

<a href="@Url.Action("ActionName", "ControllerName", new { id = Model.Id })">Link Text</a>

### 14. Working with Sections <a id="working-with-sections"></a>
```

@section Scripts {
    <script src="~/js/yourScript.js"></script>
}

### 15. Using @Html.AntiForgeryToken <a id="htmlantiforgerytoken"></a>

```
<form method="post" action="/YourController/YourAction">
    @Html.AntiForgeryToken()
    </form>


### 16. Displaying Date and Time <a id="displaying-date-and-time"></a>
```
@Model.DateTimeProperty.ToString("MM/dd/yyyy HH:mm")

### 17. Creating a Simple Modal <a id="creating-a-simple-modal"></a>
```
<div id="myModal" class="modal">
    <div class="modal-content">
        <span class="close">&times;</span>
        <p>Modal Content</p>
    </div>
</div>

### 18. Implementing a Navigation Menu <a id="implementing-a-navigation-menu"></a>
```
<nav>
    <ul>
        <li><a href="@Url.Action("Index", "Home")">Home</a></li>
        <li><a href="@Url.Action("About", "Home")">About</a></li>
        <li><a href="@Url.Action("Contact", "Home")">Contact</a></li>
    </ul>
</nav>

### 19. Dynamic CSS Classes <a id="dynamic-css-classes"></a>
```

<div class="@(Model.IsActive ? "active" : "inactive")">
    </div>

### 20. Displaying Raw HTML <a id="displaying-raw-html"></a>
```

@Html.Raw(Model.HtmlContent)

### 21. Using @Html.DisplayFor and @Html.EditorFor <a id="htmldisplayforeditorfor"></a>
```

@Html.DisplayFor(model => model.Property)
@Html.EditorFor(model => model.Property)

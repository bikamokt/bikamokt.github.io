# 21 Top ASP.NET Razor Snippets for Front-End Design

This page provides a collection of essential ASP.NET Razor snippets designed to enhance your front-end development workflow. These snippets cover common UI patterns, form elements, and dynamic content rendering, helping you build beautiful and efficient web pages.

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
13. [Generating URLs with `@Url.Action`](#generating-urls-with-urdaction)
14. [Working with Sections](#working-with-sections)
15. [Using `@Html.AntiForgeryToken`](#htmlantiforgerytoken)
16. [Displaying Date and Time](#displaying-date-and-time)
17. [Creating a Simple Modal](#creating-a-simple-modal)
18. [Implementing a Navigation Menu](#implementing-a-navigation-menu)
19. [Dynamic CSS Classes](#dynamic-css-classes)
20. [Displaying Raw HTML](#displaying-raw-html)
21. [Using `@Html.DisplayFor` and `@Html.EditorFor`](#htmldisplayfor-and-htmleditorfor)

## Snippets

### 1. Basic Layout Structure

```razor
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

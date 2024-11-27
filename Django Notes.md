# Django Notes

## Intro

Django is a fine-grained tool, allowing developers to control almost every aspect of the web-site they are developing. The down side of this control is that the learning curve can be significant.

A brief overview of how the Django pieces fit together follow.

### Processing Basics
When a user visits a website such as example.com, Django starts the processing at the outer urls.py and tries to match the path "" and, if it finds a match, it does as defined there. That match typically passes processing to myapp/urls.py and tries to match a path there. If it matches a path, it typically will refer to a function defined in views.py. 

That function will do any necessary processing and then call for an html page to be displayed. For the initial or root page, such as example.com/, the page that is called is index.html. The processing performed by the called function can be simple or extensive and the html page that is called can be simple or complex. Combined, the function in views.py is the controller and the html page is the view of the MVC triad.

The html pages are typically kept in the templates folder for the app (not the outer folder). For namespacing purposes, a folder under the templates folder is named for the app. For exampled, if the app is named "fergus", it will hold a templates folder which in turn has a folder named ferus. In otherwords, /myproject/fergus/template/fergus. When an html page (template) is called, it is called as fergus/<page.html> that is found inside the template folder.

## Django Templates

The html pages are referred to templates for two reasons: 

*   they can be assembled out of "building blocks" 
*   they can process commands and variables. 

### Templates as Building blocks

A common convention is that a "base" html page is created that holds the elements that will appear in every html page in the app, such as style sheets, headers, navigation bars, or page layouts. This base page is then incorporated into the other html pages of thse app by using the {% extends <myapp>/base.html %} command. 

Being able to just bring in large portions of boilerplate reduces the amount of work required of developers and reduces the number of errors. It also ensures that the latest version of changes are incorporated into all of the pages.

The base pages can contain named blocks, such as {% block content %}  {% endblock %}. The pages that extend the base pages can just add the material that belongs inside the named blocks, again reducing the amount of work required of the developers.

### Variables and Commands

The function that calls an html page can insert variables into the "context" that is passed to the page that is rendered by the function. These variables from its context can then be displayed in the html page. For example, the function in views.py could calculate the sales tax on a purchase and the pass the purchase total and sales tax into the html page. The html page would then display these passed in amounts using the {{ purchase_total }} and {{ sales_tax }}. 

Note that variables are surrounded by double curly-braces. The variable name is, by convention, separated from the double curly-braces by a space.

The context can be populated as a dictionary as shown below:

---
    context = {'id': id, 
               'location': location,
               'loc':loc,
               . . . 
               . . . 
               'date': date,
               'type':'Daily Avgs'}
---

The context is then included when the page is rendered as follows:

---
    return render(request, "avgs/display_daily.html", context)
---

Django provides three commands for templates: the if command, the with command, and the for command. Commands are surrounded by {% %} markers and delimited with begin and end statements. An example of the if and with commands follow:

---
    {% if age > 18 %}
        {% with patient as p %}
        <my html here>
        {% endwith %}
    {% else %}
        {% with patient.parent as p %}
        <my html here>
        {% endwith %}
    {% endif %}
---

The first line is the 'if' portion where the test is performed. Midway in the code block is the else statement that divides the actions that will be performed when the if statement is true from the actions that are performed if the if statement is not true. In this example, age is a variable that was passed in. The 'with' portion is used to redefine a complex item as something simpler. The 'with' - 'endwith' define the scope of the with.

The 'for loop' command is typically used with variable length lists on the html page. An example is shown below:

---
    {% for athlete in athlete_list %} 
        <li>{{ athlete.name }}</li> 
    {% endfor %} 
    </ul> 
---

In this example, the athelete_list is passed into the html page and then looped thru, with each item in the athelete_list displayed as list items inside the unordered list markers.


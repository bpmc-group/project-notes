= Django Notes

== Intro

Django is a fine-grained tool, allowing developers to control almost every aspect of the web-site they are developing. The down side of this control is that the learning curve can be significant.

A brief overview of how the Django pieces fit together follow.

When a user visits the website, example.com, Django starts the processing at the outer urls.py and tries to match the path "" and, if it finds a math, does as defined there. That match typically passes processing to myapp/urls.py and tries to match a path there. If it matches a path, it typically will refer to a function defined in views.py. 

That function will do any necessary processing and then call an html page. For the initial or root page, such as example.com/, the page that is called is index.html. The processing performed by the called function can be simple or extensive and the html page that is called can be simple or complex. Combined, the function is the controller and the html page is the view of the MVC triad.

The html pages are typically kept in the templates folder for the app (not the outer folder). For namespacing purposes, a folder under the templates folder is named for the app. For exampled, if the app is named fergus, it will hold a templates folder which in turn has a folder named ferus. In otherwords, /myproject/fergus/template/fergus. When an html page (template) is called, it is called as fergus/<page.html> that is found inside the template folder.

The html pages are referred to templates for two reasons: they can be assembled out of "building blocks" and they can process commands and variables. A common convention is that a "base" html page is created that holds the elements that will appear in every html page in the app, such as style sheets or 
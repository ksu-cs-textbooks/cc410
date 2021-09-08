---
title: "Video"
pre: "3. "
weight: 30
hidden: true
---

## Java

0. Run project once to see what it does. Explore code and show JSON loader and Movie class.
1. Go to [start.spring.io](http://start.spring.io) and get a `build.gradle` file from there. Use it to update the one in the starter project.
2. Create `movies.web` package.
3. Create `Web.java` in `movies` and `MoviesController.java` in `movies.web`.
4. Copy code from `WebApplication.java` file in Spring Initializr to `Web.java` and adjust
5. Set main class in `build.gradle` to `movies.Web`
6. Create controller in `MoviesController.java` and configure home page.
7. Create `resources` folder in the `src/main` directory. Add a `static` and `templates` folder inside.
8. Create an `index.html` file inside of the `templates` directory.
9. Run project and see how it looks. `gradle bootRun`
   1. Configure the .codio file to add a new tab at the top. Port 8080!
10. Create layout file `layout.html` as a basic layout. 
11. Update `index.html` to use layout.
12. Test!
13. Add `greeting` paths to Controller & create `greeting` template.
14. Test!
15. Update `index.html` route to list movies in a UL. Test!
16. Update `index.html` to have more HTML and data.
17. Update `index.html` to have CSS classes and then add CSS file to Layout. It goes in `static` folder.
18. Add ratings and more CSS.
19. Add Bootstrap stuff.
20. REMIND THEM TO MAKE about page! Play around with Bootstrap stuff!

## Python

0. Run project once to see what it does. Explore code and show JSON loader and Movie class.
1. Add `flask` and `flask-classful` dependencies and install. Remind to use `tox -r` once.
2. Create `movies.web` package.
3. Create `Web.py` in `movies` and `MoviesController.py` in `movies.web`.
4. Build `Web.py` to launch Flask app
5. Set main class in `__main__.py` to `movies.Web` and update `__init__.py` to load the app.
   1. Configure the app using `export FLASK_APP="src"`
6. Create controller in `MoviesController.java` and configure home page.
7. Create a `static` and `templates` folders inside `src/movies` directory.
8. Create an `index.html` file inside of the `templates` directory.
9. Run project and see how it looks. `python3 -m flask run --host=0.0.0.0`
   1. Configure the .codio file to add a new tab at the top. Port 5000!
   2. Install `python-dotenv` and create .flaskenv file
10. Create layout file `layout.html` as a basic layout. 
11. Update `index.html` to use layout.
12. Test!
13. Add `greeting` paths to Controller & create `greeting` template.
14. Test!
15. Update `index.html` route to list movies in a UL. Test!
16. Update `index.html` to have more HTML and data.
17. Update `index.html` to have CSS classes and then add CSS file to Layout. It goes in `static` folder.
18. Add ratings and more CSS.
19. Add Bootstrap stuff.
20. REMIND THEM TO MAKE about page! Play around with Bootstrap stuff!
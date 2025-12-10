+++
url = "/sites/customize-les-pages-derreurs/"
title = "How to customize error pages"
layout = "howto"
hidden = true
tags = [ "http", "site" ]
+++

It is advisable to create custom pages for your error pages (HTTP codes 404, 500, etc.). To do this, it is possible to configure this at different levels.

## Web Server

- [Apache](https://httpd.apache.org/docs/2.4/fr/custom-error.html);
- [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/Options.html).

## Application

Here is a non-exhaustive list for your app:

- [CakePHP](https://book.cakephp.org/3/fr/development/errors.html);
- [Django](https://docs.djangoproject.com/en/dev/topics/http/views/#customizing-error-views);
- [Express.js](https://expressjs.com/fr/guide/error-handling.html);
- [Flask](https://flask.palletsprojects.com/en/stable/errorhandling/#custom-error-pages);
- [Laravel](https://laravel.com/docs/6.x/errors);
- [Macaron](https://go-macaron.com/middlewares/templating#response-status-error-and-redirect);
- [Phoenix](https://hexdocs.pm/phoenix/custom_error_pages.html);
- [Sinatra](http://sinatrarb.com/intro.html): paragraph _Error Handling_ ;
- [Symfony](https://symfony.com/doc/current/controller/error_pages.html).

## Tips

- Track traffic on these pages: if you see a sharp increase in visits to your error pages, you can find the origin of the problem more easily;
- Display links to other pages so that the visitor can continue to navigate;
- Set up a contact form in order to be able to contact you.

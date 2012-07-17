Overview
========

**Loaders** is a collection of loaders and accessors for CodeIgniter's core objects.

After you write enough CodeIgniter applications, writing `$this` and manually
loading stuff gets old. **Loaders** is an easier, globally-accessible way to
access core CodeIgniter objects such as libraries, models, `view`, and `db`.

Originally conceived as a plugin called "Modularity", this has been reborn
as a CodeIgniter 2.0-compatible helper.

Features
========

* Auto-load libraries, models, databases
* Eliminates need to call `get_instance()` when you need to access framework
  objects inside a model, library, helper, or view
* Concise syntax
* Supports multiple database connections
* Requires PHP5 & CodeIgniter 1.5+

Download
========

TBD

Installation
============

Install and load *Loaders* as you would any other CodeIgniter helper.

Usage
=====

Views
-----

The normal way to load and display a view is like so:

```php
$this->load->view('myview', $data);
```

With the View loader, do it this way:

```php
View::show('myview', $data);
```

Or if you want to return a string instead of outputting the view, do this:

```php
$pagetext = View::parse('myview', $data);
```

Libraries
---------

The old way to load libraries was like this:

```php
$this->load->library('mylibrary');
$this->library->do_something();
```

With the library loader, you can just do this:

```php
Library('mylibrary')->do_something(); // the library automatically loads if needed
```

Models
------

To fetch data with a model, we used to do this:

```php
$this->load->model('mydatamodel_model');
$this->mydatamodel_model->do_something();
```

Now, with the model loader, it works like this:

```php
Model('mydatamodel')->do_something(); // the model automatically loads if needed
```

Databases
---------

The old way to run a query on the default database connection:

```php
$this->load->database();
$query = $this->db->query($sql);
```

Using the database loader, it is easier:

```php
$query = Database()->query($sql); // the database automatically loads if needed
```

Maybe you have multiple connections?

```php
$query1 = Database('db1')->query($sql);
$query2 = Database('db2')->query($sql);
```

Global access
-------------

These loaders work anywhere in exactly the same way, including libraries, helpers, and views.

Previously, you had to get an instance of the `$CI` object to work with, which can be a drag:

```php
$CI =& get_instance();
$CI->load->model('mymodel_model');
$CI->mymodel_model->do_something();
```

Now you don't have to call `get_instance()` anymore!

```php
Model('mymodel')->do_something();
```

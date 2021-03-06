Simple-Python-Sitemap
=====================

Simple one page python based Sitemap. Designed for mod_python.

    This sitemap is still in early development and have no css design

## Prerequisities ##

1. Tenjin. - used as template engine. (easy_install Tenjin)

## Installation ##

1. Clone this repo and set your apache using mod_python to index.py
2. Copy setting.py.demo to settings.py - this is your private settings file 
3. run `compass compile` inside`sass` folder
4. visit your new python based Sitemap

### mod_python ###

Add your VirtualHost in apache:

    <VirtualHost *:80>
        ServerName www.example.com
        DocumentRoot "/path/to/sitemap"
        DirectoryIndex index.py
        #ErrorLog "/var/log/sitemap_error_log"
        #CustomLog "/var/log/sitemap_access_log" common

        <Directory "/path/to/sitemap">
            Options -Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            Allow from all
            AddHandler mod_python .py
            PythonHandler mod_python.publisher | .py
            PythonDebug On
        </Directory>
    </VirtualHost>

## Configure ##

Edit your settings.py with your list of websites:

    context = { 
        'title': 'My Sitemap',
        'items': [
            [ 'http://www.example.com', 'Link 1', 'My first website.' ],
            [ 'http://www.example.com', 'Link 2', 'My second website.' ],
            [ 'http://www.example.com', 'Link 3', 'My third website.' ],
            [ 'http://www.example.com', 'Link 4', 'Another website.' ],
            [ 'http://www.example.com', 'Link 5', 'Yet another website.' ],
            [ 'http://www.example.com', 'Link 6', 'My last website.' ]
        ]
    }

#### Head ###
Copy views/_head.pyhtml.example to _head.pyhtml. this will be your head section
and will not be updated in git pull.

#### Thumbnails ####
The Sitemap will search for each item inside the 'thumbs' folder
for filename that match the item url (without the http://).
The thumbnail should be compressed with png extension at 150x100 resolution.

for example: 

the file /thumbs/www.example.com.png - will be the thumbnail for the 'http://www.example.com' item.


## License ##

Licensed with GPL3.

Favicon from http://www.freefavicon.com/


made by [ET][ET]

[ET]: http://www.etcs.me
[git]: git@github.com:ET-CS/Simple-Python-Sitemap.git




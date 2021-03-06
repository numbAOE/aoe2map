# aoe2map
[aoe2map.net](https://aoe2map.net) is a website to share and find Age of Empires II Random Map Scripts.

This is a Django application.

## Changelog

See [https://github.com/SiegeEngineers/aoe2map/releases](https://github.com/SiegeEngineers/aoe2map/releases)

## Development setup

Let's assume you are on linux.

You should have installed: 
 - A recent version of Python 3 (Version 3.6 or above)
 - `virtualenv`
 - `pip3`
 - `git`

You can check your versions like this:

```
$ python3 --version
Python 3.6.5
$ virtualenv --version
15.1.0
$ pip3 --version
pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)
$ git --version
git version 2.17.1
```

Clone this repository into a folder of your choice, 
this will create the `aoe2map` folder with all the relevant files:
```
git clone https://github.com/SiegeEngineers/aoe2map.git
```
Now we set up a virtual python environment inside that folder
```
cd aoe2map
virtualenv -p python3 venv
```
A folder `venv` is created that contains the virtual python environment.

Now we activate that environment:
```
source venv/bin/activate
```
Your command line prompt should now show `(venv) ` at the beginning.

We install the required dependencies into our environment. 
They have been written down into `dependencies.txt`, so we just have to execute:
```
pip install -r dependencies.txt
```

We also want to install the development dependencies from `development.txt`:
```
pip install -r development.txt
```

Before we can start the application, we have to add configuration files. 
We copy the templates in the aoe2map _subfolder_, but for development, 
we do not have to edit anything inside.
```
cp aoe2map/deployment.py.template aoe2map/deployment.py
cp aoe2map/imagestorage.py.template aoe2map/imagestorage.py
```


Now we get to work with Django itself. We initialize the database:
```
./manage.py migrate
```

… add a superuser:
```
./manage.py createsuperuser --username admin --email admin@example.org
```

… and can run the development server:

```
./manage.py runserver
```

It should say something like:
```
Performing system checks...

System check identified no issues (0 silenced).
September 10, 2018 - 19:03:25
Django version 2.1, using settings 'aoe2map.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

Open your browser and go to `http://localhost:8000` and you should see an 
empty aoe2map.net instance where you can login with the superuser we created earlier.

Further useful information:

 - The admin interface is then available at `http://localhost:8000/admin`
 - In the default development configuration, all emails the system would send
 get logged to the console instead
 - The development server reloads automatically when files change
 - I use PyCharm for development

## License
aoe2map.net  
Copyright © 2018-2019 hszemi

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

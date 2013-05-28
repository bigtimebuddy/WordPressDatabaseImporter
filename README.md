WordPress Database Importer
===========================

WordPress Database Importer is a bash script which easily imports a WordPress database (from a dumped MySQL file) from one domain to another. It replaces all instances of the domain in the database as well as changes the table prefix. This script was designed to be integrated into an automated deployment process. 

Import Example
--------------

Lets move our WordPress site from http://dev.example.com to http://example.com.

1. Do a mysqldump of your existing WordPress site http://dev.example.com to a SQL file:

	`mysqldump -u wp_user -p pass1234 dev_example_com > dev_example_com.sql`

2. If you don't want to be prompted to input each setting, create a configuration file which represents settings for the target WordPress build. Save this as example_com.conf

	```bash
	SITE_URL=example.com
	MYSQL_USER=wp_user
	MYSQL_PASS=pass1234
	MYSQL_DB=example_com
	MYSQL_HOST=localhost
	PATH_TO_MYSQL=mysql
	WP_PREFIX=wp_
	```

3. Run WordPress Database Importer script, passing the SQL file as the first argument and the configuration file as the second.

	`./WordPressDatabaseImporter dev_example_com.sql example_com.conf`

4. If everything goes well, output should look something like this:
	
	```
	Copying the SQL file...
	Replacing domain occurrences...
	Replacing the table prefix...
	Importing to MySQL...
	Cleaning up...
	Done!
	```	

Software License
----------------

The MIT License (MIT)

Copyright (c) 2013 Matt Moore

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
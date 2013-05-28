WordPress Database Importer
===========================

WordPress Database Importer is a shell script which easily imports a WordPress database (from a dumped MySQL file) from one domain to another. This is meant to be integrated into a deployment process. 

Example
-------

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
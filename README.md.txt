



https://github.com/OSBI/foodmart-data



http://easy-bi.org/blog/saiku-lanalytique-accessible/

Aller dans saiku-server/tomcat/webapps/saiku/WEB-INF/classes/saiku-datasources/ pour défnir la connexion

En cas d’utilisation de JDBC, ajouter le driver dans le répertoire  saiku-server/tomcat/webapps/saiku/WEB-INF/lib/


https://sourceforge.net/projects/mondrian/files/schema%20workbench/

https://www.youtube.com/watch?v=pgufnLCknN8


Change password and user
http://annahadnagy.com/how-to-remove-login-in-standalone-saiku/

saiku-server\tomcat\webapps\ROOT\js\saiku


3. Configure Saiku to use Cubeschema and databases:
	3.1 - Stop Tomcat, 
	3.2 - Then copy the JDBC Jar to the tomcat/lib folder.
	3.3 - Copy schema (XML format) file to tomcat/webapps/saiku/web-inf/classes/saiku-datasources/

	In tomcat/webapps/saiku/web-inf/classes/saiku-datasources/ 
		Directory to create a profile sales.txt and write the following (each cube corresponds to a configuration file, the name is unlimited, but only one can be configured, cannot be shared.) (In a file, configure two, and the back will overwrite the previous one.) 

		Create a new cube and create a new datasources configuration description. Only a description file is configured to be displayed in the Saiku. ）:

#declaration of Sauce Dallas Sales cube for Sakiu
#———————————————
Type=olap
Name=foodmart
Driver=mondrian.olap4j.mondrianolap4jdriver
Location=jdbc:mondrian:jdbc=jdbc:postgresql://localhost:5432/foodmart; Catalog=res:saiku-datasources/foodmart-schema.xml; org.postgresql.Driver;
Username=foodmart
Password=foodmart

# Configuration Description:
# TYPE=OLAP specifies an OLAP engine. No non-OLAP attribute values have been seen.
# Name: Give your data source a name.
# Driver: Specifies the Mondrian driver (the driver that transforms the two-dimensional relational table into a multidimensional table). No other attribute values have been seen.
# Location: This attribute is composed of several parts, separated by semicolons.

# Jdbc:mondrian:jdbc=jdbc:postgresql://localhost/1_tutorialsaiku:
# Specifies that the database corresponds to the JDBC URL, the previous section does not need to change, just need to modify the host and the corresponding database name. The host here is localhost, the corresponding database is 1_tutorialsaiku

# Catalog=res:saiku-datasources/sales_mondrian_schema.xml
# Specifies the Mondrian schema file. RES indicates the path to the file, starting from the Saiku WebApp directory;

# Jdbcdrivers=org.postgresql.Driver
# Indicates that the Java class file is driven as a database connection.


https://mondrian.pentaho.com/documentation/schema.php
https://github.com/pentaho/mondrian/tree/master/demo
demo/FoodMart.xml
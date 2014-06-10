MNBB
====

Mariners NMEA Black Box


Mariners NMEA Black Box is an open source project that introduces a concept to marine navigation that is not common on personal pleasure craft, even with modern mobile apps. The majority of applications available will enable you to connect to a NMEA network via wifi but will only show you the current instrument data. There are a few devices on the market that will record your vessel instrument data and allow you to view reports or compare this information to make better decisions or watch trends with wind, temperature, barometric pressure or whatever you are interested in learning. 

One of the biggest misconceptions about marine navigation devices is that consumer electronics that are not specifically designed for the "harsh marine environment" and while this may be true in some circumstances, is incorrect in regards to the devices we have come to depend on for every day use. A product has emerged into the market that has enabled computers to be low energy, compact and highly versatile. The product is called a Raspberry Pi and is essentially a fully functional computer that draws less than one amp of 12 volt power and can run various programs and provide simple applications using modern day technology. 

This project makes use of a Raspberry Pi and a wifi or wired local network that provides NMEA instrument data through the network to be captured and viewed whenever you would like. Connecting any of your electronics with a built-in web browser to the network then enables you to access the information just like you would normally by "surfing" the local internet. 

For Developers

The open source project makes use of Node.js as the application platform, a MySQL database that collects the NMEA data and normalizes it into insert rows and finally a normal front-end web application that queries the database and receives JSON formatted results for the front-end to consume. The project is module based, which means you can introdue a new module into the project which will query the database with your custom results and display the data in a richly formatted UI developed with your own custom JavaScript, CSS and HTML. 

Modules

NMEA parsing: NMEA provides a delimited sentence that can be parsed into normalized data. Each database table uses a date-time key to join each table needed for your particular module. As part of the module development, you can introduce your own custom sentence parser for a NMEA standard sentence. As the sentence is received, the key signature will ensure that that particular sentence is inserted as often as is dictated by the module. Constraints are set to disallow more than a small subset of data from being stored to prevent data overload.

Database Inserts: Each NMEA sentence will have it's own dedicated table which can be joined using a specific date-time stamp as provided for the primary key. If you design a NMEA sentence parser, you will have to follow the same insert constraints to prevent primary keys from becoming incompatible across table joins. The constraint is yet to be defined.

Custom Queries: As part of your module, you will write your own set of custom queries that will deliver a subset of data in JSON format that you can use for displaying in your custom user interface. This is the core of the application and the method in which data will be compared.

Front-End Application: This is where the entire architecture will allow non-technical mariners to use the application. Using Node's web server capabilities a user will simply connect to the application using HTTP and navigate to the home screen to view the modules that are installed into their Raspberry Pi application. 
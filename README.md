# Journey to Database

## Preface

### Database Design Process

    Conceptual Design: (DBMS and hardware Independent)
        * Database analysis and requirement->Activity: Determine end user views, output and transaction requirements
        * Entity relationship modeling and normalization-> Activity: Define entities, attributes, domains, and relationship; 2. Draw ER diagrams; normalize entity attributes
        * Data model verification->Activity: Identify ER modules and validate insert, update, and delte rules; 2. validate reports, queries, views, integrity, access, and security
        * Distribute database design-> Activity: Define the fragmentation and allocation strategy

    DBMS Selection
        Selct the DBMS-> Activity: Determine DBMS and data model to use

    Physical Design (DBMS Dependent):
        * Map conceptual model to logical model components-> Activity: Define tables, columns, relationships, and constraints

        * Validate logical model using normalization-> Normalized set of tables

        * Validate logical modeling integrity constraints-> Ensure entity and referential integrity; define column constraints

        * Validate logical model against user requirements-> Ensure the model supports user requirements

    Physical Design (Hardware dependent)
        * Define data storage organization -> Define tables, indexes, and views' physical organization

        * Define integrity and security measures-> Define users, security groups, roles and access controls

        * Determine performance measures -> Define database and query execution parameters

### Data Modeling Checklist

    BUSINESS RULES
        * Properly document and verify all business rules with the end users
        * Ensure that all business rules are written precisely, clearly, and simply. The business rules must help identify entities, attributes, relationships, and constraints
        * Identify the source of all business rules, and ensure that each business rule ise justified, dated, and signed off by an approving authority
    
    DATA MODELING
    * Naming Conventions: All names should be limited in length (database-dependent size)
        Entity Name:
            * Should be nouns that are familiar to business and should be short and meaningful
            * Should document abbreviations, synonyms and aliases for each entity
            * Should be unique within the model
            * For composite entities, may include a combination of abbreviated names of the entities linked through the composite entity

        Attribute names:
            * Should be unique within the entity
            * Should use the entity abbreviation as a prefix
            * Should be descriptive of the characteristic
            * Should use suffixes such as _ID, _NUM, or _CODE for the PK attribute
            * Should not be a reserved word
            * Should not contain spaces or special characters such as @, !, or &

        Relationship Names:
            * Should be active or passive verbs that clearly indicate the nature of the relationship

    Entities:
        * Each entity should represent a single subject
        * Each entity should represent a set of distinguishable entity instances
        * All entities should be in 3NF or higher. Any entities below 3NF should be justified
        * The graularity of the entity instance should be clearly defined
        * The PK is clearly defined and supports the selected data granularity

    Attributes:
        * Should be simple and single-valued (atomic data)
        * Should document default values, constraints, synonyms, and aliases
        * Derived attributes should be clearly identified and include source(s)
        * Should not be redundant unless they are justified for transaction accuracy

    Relationships:
        * Should clearly identify relationship participants
        * Should clearly define participation, connectivity, and document cardinality
    
    ER Model:
        * Should be validated against expected processes; inserts, updates, and deletes
        * Should evaluate where, when and how to maintain a history
        * Should not contain redundant relationships except as required (see attribute)
        * Should minimize data redundancy to ensure single-place updates
        * Should conform to the minimal data rule: "All that is needed is there and all that is there is needed"

* Big data and NoSQL
* Database design
* "create without design"
* operational databases, data warehouse concepts, structures, and procesures
* Database design, with appendices B and C
* transaction management and concurrency control
* distributed database management systems
* business intelligence and data warehouses (chapter 13)
* data connectivity and web technoglies (chapter 15)
* database administration and security
* development and future of databases and data models
* relational database model
* critical normalization issues that affect database efficiency and effectiveness
* database performance tuning and query optimization (chapter 11)
* Distrubted database management system (chapter 12), data distribution, replication, and allocation
* Business intelligence and data warehouse (chapter 13), characteristics of databases that are used in decision support and online analytical processing, inclujding coverage of data visualization and data analytics
* Big Data and NoSQL (Chapter 14), explores the challenges of leveraging nonrelational databases to use vast global stores of unstructured data
* Database connectivity and web technologies(Chatper 15), covers the basic database connectivity issues in a web-based data world
* conflicting design goal: design elegance, information requirements, and operational speed.
* Appendix P, Working with MongoDB
* Appendix Q, working with Neo4j
* Appendix N, Creating a new database using Oracle 12c

# CHAPTER 1: Database System
* Difference between data and information: Data consists of raw facts. The word raw indicates that the facts have not yet been processed to reveal their meaning. Information is the result of processing raw data to reveal its meaning. Data processing can be as simple as organizing data to reveal patterns or as complex as making forecasts or drawing inferences using statistical modeling. To reveal meaning, information requires context. Information can be used as the foundation for decision making. For example, the data summary for the faculty can provide accrediting bodies with insights that are useful in determining whether to renew accreditation for the university
* Keep in mind that raw data must be properly formatted for storage, processing, and presentation.
* **Knowledge**: the body of information and facts about a specific subject. Knowledge implies familirity, awareness, and understanding of information as it applies to an environment.
* **Data management** is a discipline that focuses on teh proper generation, storage, and retrieval of data
* **Database** is a shared, integrated computer structure that stores a collection of end user data--that is, raw facts of interest to the end user; **metadata**, or data about data, through which the end-user data is integrated and managed
* The metadata describes the data characteristics and the set of relationships that links the data found within the database. For example, the metadata component stores information such as the name of each data element, the type of values(numeric, dates, or text) stored on each data element, and whether the data element can be left empty. The metadata provides information that complments and expands the value and use of the data. In short, metadata presents a more complete picture of the data in the database.
* **A database management system (DBMS)** is a collection of programs that manages the database structure and controls access to the data stored in the database. In a sense, a database resembles a very well-organized electronic filing cabinet in which powerful software (the DBMS) helps manage the cabinet's contents.

### Role and Advantages of the DBMS
* The DBMS serves as the intermediary between the user and the database. The database structure itself is stored as a collection of files, and the only way to access the data in those files is through the DBMS
* The DBMS presents the end user (or application program) with a single, integrated view of the data in the database. The DBMS receives all application requests and translates them into the commplex operations required to fulfill those requests. The DBMS hides much of the database's internal complexity from the application programs and users
* having a DBMS between the end user's applications and the database offers some important advantages. First, **the DBMS enables the data in the database to be shared among multiple applications or users**. Second, **the DBMS integrates the many different users' views of the data into a single all-encompassing data repository**
* A DBMS provides these advantages: 

        1. **improved data sharing**. The DBMS helps create an environment in which end users have better access to more and better-managed data. Such access makes it possible for end users to respond quickly to changes in their environment. 
        2. **Improved data security**. The more user access the data, the greater the risks of data security breaches. Corporations invest considerable amounts of time, effort, and money to ensure that corporate data is used properly. A DBMS provides a framework for better enforcemtn of data privacy and security policies. 
        3. **Better data integration**: Wider access to well-managed data promotes an integrated view of the organizations' operations and a clearer view of the big picture. It becomes much easier to see how actions in one segment of the company affect other segment. 
        4. **Minimized data inonsistency**: *data inconsistency* exists when different versions of the same data appear in different places. The probability of data inconsistency is greatly reduced in a properly designed database. 
        5. **Improved data access**: The DBMS makes it possible to produce quick answers to ad hoc queries. From a database perspective, a **query** is a specific request issued to the DBMS for data manipulation--for example, to read or update the data. Simply put, a query is a question, and an ad hoc query is a spur of the moment question. The DBMS sends back an answer (called  the query result set) to the application. For example, when dealing with large amounts of sales data, end users might want quick answers to questions (ad hoc queries). Some examples are the following: What was the dollar volume of sales by product during the past six months; what is the sales bonus figure for each of our sales people during the past three months? How many of our customers have credit balances of $3,000 or more? 
        6. **Improved decision making.** Better-managed data and improved data access make it possible to generate better-quality information, or which better decisions are based. 
        The quality of the information generated depends on the quality of the underlying data. **Data quality** is a comprehensive approach to promoting the accuracy, validity, and timeliness of the data. While the DBMS does not guarantee data quality, it provides a framework to facilitate data quality initiative. *Data quality concepts will be covered in more detail in Chapter 16, Database Administration and Security*.
        7. **Increased end-user productivity.** The availability of data, combined with the tools that transform data into usable information, empowers end users to make quick, informed decisions that can make the difference between success and failure in the global economy.

### Types of Databases
* **Single-user database** supports only one user at a time. In other words, if user A is using the database, users B and C must wait until user A is done. A single-user database that runs on a personal computer is called a **desktop database**. In contrast, a **multiuser database** supports multiple users at the same time. When the multiuser database supports a relatively small number of users (usually fewer than 50) or a specific department within an organization, it is called a **workgroup database**. When the database is used by the entire organization and supports many users (more than 50, usually hundreds) across many departments, the database is known as an **enterprise database**.
* Location might also be used to classify the database. For example, a database that supports data located at a single site is called a **centralized database**. A database that supports data distributed across several diffferent sites is called a **distributed database**
* Both centralized and decentralized (distrubted) database require a well-defined infrastructure (hardware, operating systems, network technologies, etc) to implement and operate the database. Typically, the infrastructure is owned and maintained by the organization that creates and operates the database. But in recent years, the use of cloud database has been growing in popularity. A **cloud database** is a database that is created and maintained using cloud data service. These services, provided by third-party vendors, provide defined performance measures (data storage capacity, requried throughput, and availability) for the database, but do not necessarily specify the underlying infrastructure to implement it. The data owners do not have to know, or be concerned about, what hardware or software are being used to support their database. The performance capability can be renegotiated with the cloud provider as the busienss demands on  the database change.
* **General-purpose databases** contain a wide variety of data used in multiple discilines--for example, a census database that contains general demographic data and the lexisNexis and ProQuest databases that contain newspaper, magazine, and journal articles for a variety of topics. **Discipline-specific databases** contain data focused on specific subject area. The data in this type of database is used mainly for academic or research purposes within a small set of discipline. Examples of discipline-specific databases are financial data stored in databases such as CommpuStat or CRSP, geographic information system datbases that store geospatial and other related data, and medical database that store confidential medical history data.
* The most popular way of classifying database today, however, is based on how they will be used and on the time sensitivity of the information gathered from them. For example, transactions such as product or service sales, payments, and supply purchases reflect critical day-to-day operations. Such transactions must be recorded accurately and immediately. A database that is deisnged primarily to support a commpany's day-to-day operations is classfied as an **operational database**, also known as an **online transaction processing (OLTP) database, transactional database, or production database**. In contrast, an **analytical databse focus primarily on storing historical data and business metrics used exclusively for tactical or strategic decision making. Such analysis typically requires extensive "data messaging" (data manipulation) to produce information on which to based pricing decisions, sales forecasts, market strategies, and so on. Analytical databses allow the end user to perform advanced analysis of business data using sophisticaed tools.
* Typically, analytical databases comprise two main components: a data warehouse and an online analytical processing front end. The **data warehouse** is a specialized database that stores data in a format optimized for decision support. The data warehouse contains historical data obtained from mthe operational databases as well as data from other external sources. **Online analytical processing (OLAP)** is a set of tools that work together to provide an advanced data analysis environment for retrieving, processing, and modeling data from the data warehouse.
* In recent times, this area of database application has grown in importance and usage, to the point that it has evolved into its own discipline: business intelligence. The  term **business intelligence** describes a comprehensive approach to capture and process business data with the purpose of generating information to support business decision making. 

* Databases can also be classified to reflect the degree to which the data is structured. **Unstructured data** is data that exists in its original (raw) state--that is, in the format in which it was collected. Therefore, unstructured data exists in a format that does not lend itsefl to the processing that yields information. **Structured data** is the result of formating unstructured data to facilitate storage, use, and genration of information.
* An **XML database** supports the storage and management of semistructured XML data. 

### Why Database Design is Important
* **Database design** refers to the activities that focus on the design of teh databse structure that will be used to store and manage end-user data. A database that meets all user requirements does not jsut happen; its strcture must be designed carefully. In fact, database design is such a crucial aspect of working with databases that most of this book is dedicated to the development of good database design techniques. Even a good DBMS will perform poorly with a badly designed database.
* **Data**: Raw facts, such as telphone number, a birth date, a customer name, and a year-to-date sales value. Data has little meaning unless it has been organized in some logical manner
* **Field**: A character or group of characters (alphabetic or numeric) that has a specific meaning. A field is used to define and store data
* **record**: A logically connected set of one or mroe fields that dsscribes a person, place, or thing. For example, the fields that constitute a record for a customer might consist of the customer's name, address, phone number, date of birth, credit limit, and unpaid balance
* **File**: A collection of related records. For example, a file might contain data about the students currently enrooled at Gigantic University
* A **data anomaly** develops when not all the required changes in teh redundant data are made successfully
* The term database system refers to an organization of components that define and regulate the collection, storage, management, and use of data within a database environment. From a general management point of view, the database system is composed of the five major parts shown below: hardware, software, people, procedures, and data. **Hardware** refers to all the system's physical devices, including computers, storage devices, printers, network devices, and other devices. **Software**: Besides DBMS, three types of software are needed to make the database system function fully: **operating system software, DBMS software, and application programs and utilities.** Operating system software manages all hardware components and makes it possible for all other software to run on the computer; DBMS software manages the database within the database system; Application programs and utility software are used to access and manipulate data in the DBMS and to manage the computer environment in which data access and manipulation take place. Application programs are most commonly used to access data within the database to generate reports, tabulations, and other information to facilitate decision making. Utilities are the software tools used to help manage the database system's computer components. For example, all the major DBMS vendors now provide graphical user interfaces (GUI) to help create database structures, control database access, and monitor database operations. **People**: The component includes all users of the database system. On the basis of primary job functions, five types of users can be identified in a database system: system administrators, database administrators, database designers, system analysts and programmers, and end users. System administrators oversee the database system's general operations. Database administrators, also known as DBA, manage the DBMS and ensure that the database is functioning properly. Database designers design the database structure. System analysts and programmers design and implement the application programs. They design and create the data entry screens, reports, and procedures through which end users access and manipulate the database's data. End users are the people who use the application programs to run the organization's daily operations. **Procedures**: Procedures are the instructions and rules  that govern the design and use of the database system. Procedures are a critical, although occasionally forgotten, component of the system. Procedures play an important role in a company because they enforce the standards by which business is conducted within the organization and with customers. Procedures also help to ensure the companies have an organized way to monitor and audit the data that enter the database and the information generated from those data. **data**: The word data covers the collection of facts stored in the database. Because data is the raw material from which information is generated, determining which data to enter into the database and how to organize that data is a vital part of the database designer's job.

### DBMS Function:
* Data dictionary management, data storage management, data transformation and presentation, security management, multiuser access control, backup and recovery management, data integrity management, database access lanagues and application programming interfaces, and database communication interfaces.
* Data dictionary management. The DBMS stores definition of the data elements and their relationship (metadata) in a data dictionary. In turn, all programs that access the data in the database work through the DBMS. The DBMS uses the data dictionary to look up the required data component structures and relationships, thus relieving you from having to code such commplex relationships in each program. Additionally, any changes made in a database structure are automatically recorded in the data dictionary, thereby freeing you from having to modify all the programs that access the changed structure. In other words, the DBMS provides data abstraction, and it removes structural and data dependence from the system. 
* Data storage management. the DBMS creates and manages the complex structures required for data storage, thus relieving you from the difficult task of defining and programming the physical data characteristics. A modern DBMS provides storage not only for the data but also for related data entry forms or screen definitions, report definitions, data validation rules, procedural code, structures to handle video and picture formats, and so on. Data storage management is also important for database performance tuning. Performance tuning relates to the activities that make the database perform more efficiently in terms of storage and access speed.
* Data transformation and presentation. The DBMS transforms entered data to conform to required data structures. The DBMS relieves you of the chore of distinguishing between the logical data format and the physical data format
* Security management. The DBMS creates a security system that enforces user security and data privacy. Security rules determine which users can access the database, which data items each user can access, and which data operations (read, add, delete, or modify) the user can perform. This is especailly important in multiuser database systems.
* Multiuser access control. To provide data integrity and data consistency, the DBMS uses sophisticated algorithms to ensure that multiple users can access the database concurrently without compromising its integrity
* Backup and recovery management. The DBMS provides backup and data recovery to ensure data safety and integrity. Current DBMS systems provide special utilities that allow the DBA to perform routine and special backup and restore procedures. Recovery management deals with the recovery of the database after a failure, such as a bad sector in the disk or a power failure. Such capability is critical to preserving the database's integrity.
* Data integrity management. The DBMS promotes and enforces integrity rules, thus minimizing data redundancy and maximizing data consistency. The data relaitonships stored in the data dictionary are used to enforce data integrity. Ensuring data integrity is especially important in transaction-oriented database system.
* Database access languages and application programming interfaces. The DBMS provides data access through a query language. A query language is a nonprocedural language--one that lets the user specify what must be done without having to specify how.
* Database communication interfaces. A current-generation DBMS accepts end-user requests via multiple, different network environments. For example, the DBMS might provide access to the database via the Internet through the use of web browsers such as mozilla Firefox, Google Chrome, Microsoft Edge, and Microsoft Internet Explorer

* Although the database system yields considerable advantages over previous data management approaches, database system do carry significatn disadvantages:
1. Increased costs. Database system require sophisticated hardware and software and highly skilled personnel. The cost of maintaining the hardware, software, and personnel required to operate and manage a database system can be substantial. Training, licensing, and regulation compliance costs are often overlooked when database systems are implemented.
2. management complexity. Database systems interface with many different technologies and have a significant impact on a company's resources and culture. The changes introduced by the adoption of a database system must be properly managed to ensure that they help advance the company's objectives. Because database system hold crucial company data that are accessed from multiple sources, security issues must be assessed constantly
* Maintaining currency. To maximize the efficieny of the database system, you must keep your system current. Therefore, you must perform frequent updates and apply the latest patches and security measures to all components. Because database technology advances rapidly, personnel training costs tend to be significant.
* Vendor dependence. Given the heavy investment in technology and personnel training, companies might be reluctant to change database vendors. As a consequence, vendors are less likely to offer pricing point advantages to existing customers, and those customers might be limited in their choice of database system components
* Frequent upgrade/replacement cycles. DMBS vendors frequently upgrade their products by adding new functionality. Such new features often come bundled in new upgrade versions of the software. Some of these versions require hardware upgrades. Not only do the upgrades themselves cost money but it also costs money to train database users and administrators to properly use and manage the new features.

### Database Career Opportunity
* Database Developer: create and maintain database-based applications-> Skills: Programming, database fundamentals, SQL
* Database Designer: Design and maintain databases->Skills: Systems design, database design, SQL
* Database Administrator: Manage and maintain DBMS and databases-> Database fundamentals, SQL vendor courses
* Database Analyst: Develop databases for decision support reporting-> SQL, query optimization, data warehouses
* Database Architect: Design and immplementation of database environments (conceptual, logical, and physical)-> DBMS fundamendals, data modeling, SQL, hardware knowledge, etc
* Database Consultant: Help companies leverage database technologies to improve busienss processes and achieve specific goals->Database fundamentals, data modeling, database design, SQL, DBMS, hardware, vendor-specific technologies, etc
* Database security officer: Implement security policies for data administration-> DBMS fundamentals, database administration, SQL, data security technologies, etc
* Cloud Computing Data Architect: Design and implement the infrastructure for next-generation cloud database systems-> Internet technologies, cloud storage technologies, data security, performance tuning, large databases, etc
* Data Scientist: Analyze large amounds of varied data to generate insights, relationships, and predictable behabaviour-> Data analysis, statistics, advanced mathematics, SQL, programming, data mining, machine learning, data visualization

# CHAPTER 2: DATA MODELING
* Database design focuses on how the database structure will be used to store and manage end-user data. **Data modeling**, the first step in designing a database, refers to the process of creating a specific data model for a determined problem. A **data model** is a relatively simple representation, usually graphical, of more complex real-world data structures. In general terms, a model is an abstraction of a more complex real-world object or event. **A model's main function is to help you understand the complexities of the real-world environment. Within the database environment, a data model represents data structures and their characteristics, relations, constraints, tansformations, and other constructs with the purpose of supporting a specific problem domain.

### The Importance of Data Models
* Data models can facilitate interaction among the designer, the applications programmer, and the end user. A well-developed data model can even foster improved understanding of the organization for which the database design is developed. **In short, data models are a communication tool**
* When a good database blueprint is available, it does not matter that an applications programmer's view of the data is different from that of the manager or the end user. Conversely, when a good database blueprint is not available, problems are likely to ensue. For instance, an inventory management program and an order entry system may use conflicting product-numbering schemes, thereby costing the company thousands or even millions of dollars.
* keep in mind that a house blueprint is an abstraction; you can't live in the blueprint. Similarly, the data model is an abstraction; you can not draw the required data out of the data model

### Data Model Basic Building Blocks
* The basic building blocks of all data models are entities, attributes, relationships, and constraints. An **entity** is a person, place, thing, or event about which data will be collected or stored. n entity represents a particular type of object in the real world, which means an entity is "distinguishable"--that is, each entity occurence is unique and distinct. For eample, a CUSTOMER entity would have many distinguisable customer occurence, such as John Smith, Pedro Dinamita, and Tom Strickland. Entities may be physical objects, such as customers or products, but entities may also be abstractions, such as flight routes or musical concerts
* An **attribute** is a characteristic of an entity
* A **relationship** describes an association among entities. one to one, one to many, many to many.
* A **constraint** is a restriction placed on the data. Example: An employee's salary must have values that are between 6000 and 350000. A student's GPA must be between 0.00 and 4.00. Each class must have one and only one teacher

### Business Rules
* From a database point of view, the collection of data becomes meaningful only when it reflects properly defined busienss rules. A **business rule** is a brief, precise, and unambiguous description of a policy, procedure, or principle within a specific organization. In a sense, business rules are misnamed: they apply to any organization, large or small--a business, a government unit, a religious group, or a research laboratory--that stores and uses data to generate information
* Business rules **derived from a detailed description of an organization's operations help to create and enforce actions within that organization's environment**. Business rules must be rendered in writing and updated to reflect any change in the organization's operational environment.
* Properly written busienss rules are used to define entities, attributes, relationships, and constraints. Any time you see relationship statements such as "an agent can serve many customers, and each customer can be served by only one agent", business rules are at work.

### Discovering Busienss Rules
* The main sources of business rules are comapny managers, policy makers, department managers, and written documentation such as company's procedures, standards, and operations manuals. A faster and more direct source of business rules is direct interviews with end users
* The process of identifying and coumenting business rules is essential to database design for several reasons: 1. It helps to standardize the company's view of data; 2. It can be a communiation tool between users and designers; 3. It allows the designer to understand the nature, role, and scope of the data; 4. It allows the designer to understand busienss processes; 5. It allows the designer to develop appropriate relationship participation rules and constraints and to create an accurate data model

### Translating Business Rules into Data Model Components
* As a general rule, a noun in a busienss rule will translate into an entity in the model, and a vert (active or passive) that associates the nouns will translate into a relationship among the entities

### Naming Conventions
SKIM

* A **data manipulation language (DML)** defines the environment ini which data can be managed and is used to work with the data in the database
* A schema **data definition language (DDL) enables the database administrator to define the schema components.

*From an end-user perspective, any SQL-based relational database application involves three parts: a user interface, a set of tables stored in the database, and the SQL "engine". **The end-user interface**: Basically, the interface allows the end user to interact with the data (by automatically generating SQL code). Each interface is a product of the software vendor's idea of meaningful interaction with the data. **A collection of tables stored in the database**: In a relational database, all data is perceived to be stored in tables. The tables simply "present" the data to the end user in a way that is easy to understand. Each table is independent. Rows in different tables are related by common values in common attributes. **SQL engine**: Largely hidden from the end user, the SQL engine executes all queries, or data requests. Keep in mind that the SQl engine is part of the DBMS software. The end user uses SQL to create table structures and to perform data access and table maintenance. The SQL engine processes all user requests--largely behind the scenes and without the end user's knowledge

SKIM

# CHAPTER 3: THE RELATIONAL DATABASE MODEL
* Each table must have a primary key. In general terms, the primary key is an attribute or combination of attributes that uniquely identifies any given row.
* a **foreign key** is the primary key of one table that has been placed into another table to create a common attribute
* Foreign keys are used to ensure referential integrity, the condition in which every reference to an entity instance by another entity instance is valid.
* a **secondary key** is defined as a key that is used strictly for data retrieval purposes.
* Index: an ordered array of index key values and row ID values (pointers). Indexes are generally used to speed up and facilitate data retrieval.

### Integrity Rules
* Relational database integrity rules are very important to good database design. Relational database management systems (RDBMSs) enforce integrity rules automatically, but it is much safer to make sure your application design conforms to the entity and referential integrity rules mentioned in this chapter. Those rules are summarized below:

        ENTITY INTEGRITY
        * Requirement: All primary key entries are unique, and no part of a primary key may be null
        * Purpose: Each row will have a unique identity, and foreign key values can properly reference primary key values
        * Example, No invoice can have a duplicate number, nor can it be null; in short, all invoices are uniquely identified by their invoice number.

        REFERENTIAL INTEGRITY
        * Requirement: A foreign key may have either a null entry, as long as it is not a part of its table's primary key, or an entry that matches the primary key value in a table to which it is related (every non-null foreign key value must reference an existing primary key value)
        * Purpose: It is possible for an attribute not to have a corresponding value, but it will be impossible to have an invalid entry; the enforcement of the referential integrity rule makes it impossible to delete a row in one table whose primary key has mandatory matching foreign key values in another table
        * Example: A customer might not yet have an assigned sales representative (number), but it will be impossible to have an invalid sales representative (number)

* EXAMPLE: Entity integrity: The CUSTOMER table's primary key is CUS_CODE. The CUSTOMER primary key column has no null entriies, and all entries are unique. Similarly, the AGENT table's primary key is AGENT_CODE, and this primary key column is also free of null entries. Referential integrity. The CUSTOMER table contains a foreign key, AGENT_CODE, that links entries in the CUSTOMER table to the AGENT table. The CUS_CODE row identified by the (primary key) number 10013 contains a null entry it its AGENT_CODE foreign key because Paul F. Olowski does not yet have a sales representative assigned to him. The remaining AGENT_CODE entries in the CUSTOMER table all match the AGENT_CODE entries in the AGENT table.

### Relational Algebra
* The data in relational tables is of limited value unless the data can be manipulated to generate useful information. This section describes the basic data manipulation capabiities of the relational model. Relational algebra defines the theoretical way of manipulating table contents using relational operators. In Chapter 7, Introduction to SQL, and Chapter 8, Advanced SQL, you will learn how SQL commands can be used to accomplish relational algebra operations.

### Relational Set Operators
* The relational operators have the property of closure; that is, the use of relational algebra operators on existing relations (tables) produces new relations. Numerous operators have been defined. Some operators are fundamental, while others are convenient but can be derived using the fundamental operators. In this section, the focus will be on the SELECT (or RESTRICT), PROJECT, UNION, INTERSECT, DIFFERENCE, PRODUCT, JOIN, and DIVIDE operators

* **SELECT**, also known as RESTRICT, is referred to as a unary operator because it only uses one table as input. It yields values for all rows found in the table that satisfy a given condition. SELECT can be used to list all the rows, or it can yield only rows that match a specific criterion. In other words, SELECT yields a horizontal subset of a table. **SELECT will not limit the attributes returned so all attributes of the table will be include in the result**

* PROJECT SKIM

END OF CHAPTER

# CHAPTER 4: Entity Relationship (ER) Modeling

### Attribute
* A *required attribute* is an attribute that must have a value.
* Attributes have a **domain**. A domain is the set of possible values for a given attribute. For example, the domain for a grade point average (GPA) attribute is written (0,4) because the lowest possible GPA value is 0 and the highest possible value is 4. The domain for a gender attribute consists of only two possibilities: M or F
* A *composite attribute*, not to be confused with a composite key, is an attribute that can be further subdivided to yield additional attributes. For example, ADDRESS can be subdivided into street, city, state, and zip code. Similarly, the attribute PHONE_NUMBER can be subdivided into area code and exchagne number. A *simple attribute* isd an attribute that can not be subdivided. For example, age, sex, and marital status would be classified as simple attributes.
* In the Chen ERM, multivalued attributes are **shown by a double line connecting the attribute to the entity.**
* Identifier
* **Implementing Multivalued Attributes** Although the conceptual model can handle M:N relationships and multivalued attributes, you should not implement them in the RDBMS. Remember from Chapter 3 that in the relational table, each column and row intersection represents a single data value. So, if multivalued attributes exist, the designer must decide on one of two possible courses of action:
1. Within the original entity, create several new attributes, one for each component of the original multivalued attribute. For example, the CAR entity's attribute CAR_COLOR can be split to create the new attributes CAR_TOPCOLOR, CAR_BODYCOLOR, and CAR_TRIMCOLOR, which are then assigned to the CAR entity.
* Although this solution seems to work, its adoption can lead to major structural problems in the table. It is only acceptable if every instance will have the same number of value for the multivalued attribute, and no instance will ever have more values. However, even in this case, **it is a gamble that new changes in the environment will never create a situation where an instance would have more values than before.** For example, if additional color components--such as logo color--are added for some cars, the table structure must be modified to accommodate the new color section. In that case, cars that do not have such color sections generate nulls for the nonexistent components, or their color entries for those sections are entered as N/A to indicate "not applicable" (The solution above is to split a multivalued attribute into new attributes, but imagine the problems this type of solution would cause if it were applied to an employee entity that contains employee degrees and certifications. If some employees have 10 degrees and certifications while most have fewere or none, the number of degree/certification attributes would be 10, and most of those attribute values would be null for most employees). In short, although you have seen solution I applied, it is not always acceptable.
2. Create a new entity composed of the original multivalued attribute's components. This new entity allows the designer to define color for different sections of the car. Then, this new CAR_COLOR entity is related to the original CAR entity in a 1:M relationship
* Using the approach above, you even get a fringe benefit: you can now assign as many colors as necessary without having to change the table strcutre. This is the preferred awy to deal with multivalued attributes. Creating a new entity in a 1:M relationship with the original enttiy yields several benefits: it is a more flexible, expandble solution, and it is compatible with the relational model!

* **Derived attribute** SKIM

#### Relationship
* Relationship is an association between two entities

* The term **connectivity** is used to describe the relationship classification.
* **Cardinality** expresses the minimum and maximum number of entity occurrences associated with one occurrence of the related entity. In the ERD, cardinality is indicated by placing the appropriate numbers beside the entities, using the format (x,y). The first value represents the minimum number of associated entities, while the second value represents the maximum number of associated entities.

##### Existence Dependence
* An entity is said to be existence-dependent if it can exist in the database only when it is associated with another related entity occurence. **In implementation terms, an entity is existence-dependent if it has a mandatory foreign key--that is, a foreign key attribute can not be null.** For example, if an employee wants to claim one or more dependents for tax-withholding purposes, the relationship "EMPLOYEE claims DEPENDENT" would be appropriate. In that case, the DEPENDENT entity is clearly existence-dependent on the EMPLOYEE entity because it is impossible for the dependent to exist apart fromm the EMPOYEE in the database.
* If an entity can exist apart from all of its related entities, then it is **existence-independent**, and it is referred to as a **strong entity** or **regular entity**. For example, suppose that the XYZ Corporation uses parts to produce its products. Furthermore, suppose that some of those parts are prdouced in-house and other parts are bought from vendors. In that scenerio, it is quite possible for a PART to exist independently from a VENDOR in the relationship "PART is supplied by VENDOR" because at least some of the part are not supplied by a vendor. Therefore, PART is existence-independent from VENDOR.

##### Relationship Strength
* The concept of relationship strength is based on how the primary key of a related entity is defined. To implement a relationship, the primary key of one entity (the parent entity, normally on the "one" side of the one-to-many relationship) appears as a foreign key in the related entity (the child entity, mostly the entity on the "many" side of the one-to-many relationship). Sometimes, the foreign key also is a primary key component in the related entity. For example, the CAR entity primary key (CAR_VIN) appears as both a primary key component and a foreign key in the CAR_COLOR entity. 

* **Weak (Non-Identitfying) Relationship** A weak relationship, also known as a non-identifying relationship, **exist if the primary key of the related entity does not contain a primary key of the parent entity**. By default, relationships are established by having the primary key of the parent entity appear as a foreign key on the relationship entity (also known as the child entity). For example, suppose the 1:M relationship between COURSE and CLASS is defined as:

        COURSE(CRS_CODE, DEPT_CODE, CRS_DESCRIPTION, CRS_CREDIT)

        CLASS (CLASS_CODE, CRS_CODE, CLASS_SECTION, CLASS_TIME, ROOM_CODE, PROF_NUM)

* In this example, the CLASS primary key did not inherit a primary key compoentn from the COURSE entity. In this case, a weak relationship exists between COURSE and CLASS because CRS_CODE (the primary key of the parent entity) is only foreign key in the CLASS entity.

* **Strong (Identifying) Relationships** A strong (identifying) relationship exists when the primary key of the related entity contains a primary key component of the parent entity. For example, suppose the 1:M relationship between COURSE and CLASS is defined as:

        COURSE (CRS_CODE, DEPT_CODE, CRS_DESCRIPTION, CRS_CREDIT)

        CLASS (CRS_CODE, CLASS_SECTION, CLASS_TIME, ROOM_CODE, PROF_NUM)

* In this case, the CLASS entity primary key is composed of CRS_CODE and CLASS_SECTION. Therefore, a strong relationship exists between COURSE and CLASS because CRS_CODE (the primary key of the parent entity) is a primary key component in the CLASS entity. In other words, the CLASS primary key did inherit a primary key component from the COURSE entity (Note that the CRS_CODE in CLASS is also the FK to the COURSE entity).
* The Crow's Foot notation depicts the strong (identifying) relationship with a solid line between the entities.


#### Weak Entities
* In contrast to the strong or regular entity mentioned, a **weak entity** is one that meets two conditions:
1. The entity is existence-dependent; it can not exist without the entity with which it has a relationship
2. The entity has a primary key that is partially or totally derived from the parent entity in the relatinoship.
* For example, a company insurance polilcy insures an employee and any dependents. For the purpose of describing an insurance policy, an EMPLOYEE might or might not have a DEPENDENT, but the DEPENDENT must be associated with an EMPLOYEE. Moreover, the DEPENDENT can not exist without the EMPLOYEE; that is, a person can not get insurance coverage as a dependent unless the person is a dependent of an employee. DEPENDENT is the weak entity in the relationship "EMPLOYEE has DEPENDENT". 
* Note that the Chen notation identifies the weak entity by using a double-walled entity rectangle. The Crow's Foot notation generated by Visio Professional uses the relationship line and the PK/FK designation to indicate whether the related entity is weak. A strong (identifying) relationship indicates that the related entity is weak. Such a relationship means that both conditions have been met for the weak entity definition--the related entity is existence dependent, and the PK of the related entity contains a PK component of the parent entity.
* Remember that the weak entity inherits part of its primary key from its strong counterpart. For example, at least, part of the DEPENDENT entity's key was inherited from the EMPLOYEE entity:

        EMPLOYEE (EMP_NUM, EMP_LNAME, EMP_FNAME, EMP_INITIAL, EMP_DOB, EMP_HIREDATE)

        DEPENDENT (EMP_NUM, DEP_NUM,DEP_FNAME, DEP_DOB)

* The implementation of the relationship between the weak entity (DEPENDENT) and its parent or strong counterpart (EMPLOYEE). Note that DEPENDENT's primary key is composed of two attributes, EMP_NUM and DEP_NUM, and that EMP_NUM was inherited from EMPLOYEE.

* Keep in mind that the database designer usually determines whether an entity can be described as weak based on the business rules. An examination might cause you to conclude that CLASS is a weak entity to COURSE. After all, it seems clear that a CLASS can not exist without a COURSE, so there is existence dependence. For example, a student can not enroll in the Accounting I class ACCT-211, Section 3 (CLASS_CODE 10014), unless there is an ACCT-211 course. **However, note that the CLASS table's primary key is CLASS_CODE, which is not derived from the COURSE parent entity.** That is, CLASS may be represented by:

        CLASS (CLASS_CODE, CRS_CODE, CLASS_SECTION, CLASS_TIME, ROOM_CODE, PROF_NUM)

* The second weak entity requirement has not been met, therefore, by defintion, the CLASS entity may not be classified as weak. On the other hand, if the CLASS entity's primary key had been defined as a composite key composed of the combination CRS_code and CLASS_SECTION, CLASS coould be represented by:

        CLASS (CRS_CODE, CLASS_SECTION, CLASS_TIME, ROOM_CODE, PROF_NUM)

* In that case, the CLASS primary key is partial derived from COURSE because CRS_CODE is the COURSE table's primary key. Given this decision, CLASS is a weak entity by definition. 

##### Relationship Participation
* Participation in an entity relationship is either optional or mandatory. 
* **Optional participation** means that one entity occurrence does not require a corresponding entity occurrence in a particular relationship. For example, in the "COURSE generates CLASS" relationship, you noted that at least some courses do not generate a class. In other words, an entity occurrence (row) in the COURSE table does not necessarily require the existence of a corresponding entity occurence in the CLASS table. Therefore, **the CLASS entity is considered to be optional to the COURSE entity** MY: it just means the cardinality is 0


* The Chen notation identifies the weak entity by using a double-walled entity rectangle.

* Remember that the burden of establishing the relatinoship is always placed on the entity that contains the foreign key. In most cases, that entity is on the "many" side of the relationship

## Developing an ER Diagram
* Building an ERD usually involves the following activities:

        * Create a detailed narrative of  the organization's description of operations
        * Identify the business rules based on the description of operations
        * Identify the main entities and relationships from the business rules
        * Develop the initial ERD
        * Identify the attributes and primary keys that adequately describe the entities
        * Revise and review the ERD

* During the review process, additional objectives, attributes, and relationships probably will be uncovered. Therefore, the basic ERM will be modified to incorporate the newly discovered ER commponents. Subsequently, another round of reviews might yield additional components or clarification of the existing diagram. **The process is repeated until the end users and designers agree that the ERD is a fair representation of the organization's activites and functions.**
* **During the design process, the database designer does not depend simply on interview to help define entities, attributes, and relationships. A surprising amount of information can be gathered by examining the business forms and reports that an organization uses in its daily operations.

* It is again appropriate to evalute the reason for maintaining the 1:1 relationship between PROFESSOR and SCHOOL in "PROFESSOR is dean of SCHOOL" relationship. It is worth repeating that the existence of 1:1 relationships often indicates a misidentification of attributes as entity. In this case, the 1:1 relationship could easily be eliminated by storing the dean's attributes in the SCHOOL entity. This solution would also make it easier to answer the queries "Who is the dean?" and "What are the dean's credentials?" The downside of this solution is that it requires the duplication of data that is already stored in the PROFESSOR table, **thus setting the stage for anomalies**. However, because each school is run by a single dean, the problem of data duplication is rather minor. The selection of one approach over another often depends on information requirements, transaction speed, and the database designer's professional judgment. **In short, do not use 1:1 relationship lightly, and make sure that each 1:1 relationship within the database design is defensible.

## 4.3 Database Design Challenges: Conflicting Goals
* Database designers must often make design compromises that are triggered by conflicting goals, such as adherence to design standards (design elegance), processing speed, and information requirements
* *Design standards*. The database design must conform to design standards. Such standard guide you in developing logical structures that minimize data redundancies, thereby minimizing the likelihood that destructive data anomalies will occur. You have also learned how standards prescribe avoid nulls to the greatest extend possible. In fact, you have learned that design standards govern the presentation of all compoents within the database design. In short, design standards allow you to work with well-defined components and to evalute the interaction of those components with some precision. Without design standards, it is nearly impossible to formulate a proper design process, to evaluate an existing design, or to trace the likely logical impact of changes in design.
* *Processing speed*. In many organizations, particularly those that generate large numbers of transactions, high processing speeds are often a top priority in database design. High processing speed means minimal access time, which may be achieved by minimizing the number and complexity of logically desirable relationships. For example, a "perfect" design might use a 1:1 relationship to avoid nulls, while a design that emphasizes higher transaction speed might combine the two tables to avoid the use of an additional relationship, using dummy entries to avoid the nulls. If the focus is on data-retrieval speed, you might also be forced to include derived attributes in the design.
* Information requirement. The quest for timely information might be the focus of database design. Complex information requirements may dictate data transformation, and they may expand the number of entities and attributes within the design. Therefore, the database may have to sacrifice some of its "clean" design structure and high transaction speed to ensure maximum information generation. For example, suppose that a detailed sales report must be generate periodically. The sales report includes all invoice subtotals, taxes, and totals, even the invoice lines include subtotals. If the sales report include hundreds of thousands (or even millions) of invoices, computing the total, taxes, and subtotals is likely to take some time. If those computation had been made and the results had been stored as derived attributes in the INVOICE and LINE tables at the time of the transaction, the real-time transaction speed might have declined

# Chapter 5: Advanced Data modeling
* entity supertypes, subtypes, and entity clustering
* primary key identification and placement
* flexibility
* specialization hierarchies. Although Microsoft Viso 2010 and earlier versions handled these constructs neatly, newere versions of Visio starting with Microsoft Visio 2013 removed support for many database modeling activities, including specializatino hierarchies.

* The extended entity relationship model (EERM), sometimes referred to as the enhanced entity relationship model, is the result of adding more semantic constructs to the original ER model.
* main EER model constructs--entity supertypes, entity subtypes, and entity clustering

## 5-1a Entity Supertypes and Subtypes
* The growing of employees into various types provides two important benefits: it avoids unnecessary nulls in attributes when some employees have characteristics that are not shared by other employees; it enables a particular employee type to participate in relationships that are unique to that employee type.
* To illustrate those benefits, you will explore the case of an aviation busienss that employs pilots, mechanics, secretaries, accountants, database managers, and many other types of employees. SKIP
* An **entity supertype** is a gernic entity type that is related to one or more entity subtypes. **The entity supertype contains common characteristics, and the entity subtypes each contain their own unique characteristics.

* Two criteria help the designer determine when to use subtypes and supertypes: 1. There must be different, identifiable kinds or types of the entity in the user's environment; 2. The different kinds or types of instances should each have one or more attributes that are unique to that kind or type of instance.
* CLERK would not be an acceptable subtype of EMPLOYEE because it only satisfies one of the criteria--it is an identifiable kind of employee--but none of the attributes are unique to just clerks.

## 5-1b Specialization Hierarchy
* Entity supertypes and subtypes are organized in a specialization hierarchy, which depicts the arrangement of higher-level entity supertypes and lower-level entity subtypes
* The relationship depicted within the specialization hierachy are sometimes described **in terms of "is-a" relationships**
* A specialization hierachy provides the means to: 1. support attribute inheritance; 2. Define a special supertype attribute known as the subtype discriminator; 3. Define disjoint or overlapping constraints and complete or partial constraints; 

## 5-1c Inheritance
* One important inheritance characteristics is that all entity subtypes inherit their primary key attribute from their supertype
* At the implementation level, the supertype and its subtype depicted in the specialization hierarchy maintain 1:1 relationship. For example, the specialization hierachy lets you replace the undesirable EMPLOYEE table structure with two tables--one representing the supertype EMPLOYEE and the other representing the subtype PILOT.

## 5-1d Subtype Discriminator
* A **subtype discriminator** is the attribute in the supertype entity that determines to which subtype the supertype occurence is related
* It is common practice to show the subtype discriminator and its value for each subtype in the ERD. However, not all ER modeling tools follow that practice. For example, Microsoft Visio shows the subtype discriminator but not its value. 
* Note that the default comparison condition for the subtype discriminator attribute is the equality comparison. However, in some situations the subtype discriminator is not necessarily based on an equality comparison. For example, based on business requirements, you might create two new pilot subtypes: pilot-in-command (PIC)-qualified and copilot-qualified only. A PIC-qualified pilot must have more than 1500 PIC flight hours. In this case, the subtype discriminator would be "Flight_Hours", and the criteria would be >1500 or <=1500 respectively.

## 5-1e Disjoint and Overlapping Constraints
* An entity supertype can have disjoint or overlapping entity subtypes. In the aviation example, an employee can be a pilot, a mechanic, or an accountant. Assume that one of the business rules dictates that an employee can not belong to more than one subtype at a time; that is, an employee can not be a pilot and a mechanic at the same time. **Disjoint subtypes**, also known as **nonoverlapping subtypes**, are subtypes that contain a unique subset of the supertype entity set; in other words, each entity instance of the supertype can appear in only one of the subtype. For example, an employee (supertype) who is a pilot (subtype) can appear only in the PILOT subtype, not in any of the other subtype. In an ERD, such disjoint subtypes are indicated by the letter d inside the category shape.
* On the other hand, if the business rule specifies that employees can have multiple classifications, the EMPLOYEE supertype may contain overlapping job classification subtypes. **Overlapping subtypes** are subtypes that contain nonunique subsets of the supertype entity set; that is, each entity instance of the supertype may apepar in more than one subtype. For example, in a university environment, a person may be an employee, a student, or both. In turn, an employee may be a professor as well as an administrator.
* It is common practice to show disjoint and overlapping symbols in the ERD. However, not all ER modeling tools follow that practice. For example, by default, **Visio shows only the subtype discriminator (using the Category shape), but not the disjoint and overlapping symbols. The Visio text tool was used to manually add the d and o symbols in the previous figures.**
* As you learned earlier in this section, the implementation of disjoint subtypes is based on the value of the subtype discriminator attribute in the supertype. However, implementing overlapping subtypes requires the use of one discriminator attribute for each subtype. For example, in the case of the Tiny College database design in Chapter 4, a professor can also be an administrator. Therefore, the EMPLOYEE supertype would have the subtype discriminator attributes and values shown below.

    | Professor | Administrator |
    |----|----|
    | Y | N |
    | N | Y |
    | Y | Y |

## 5-1f Completeness Constraint
* The completeness constraint specifies whether each entity supertype occurrence msut also be a member of at least one subtype. The completeness constraint can be partial or total. **Partial completeness** means that not every supertype occurence is a member of a subtype; some supertype occurrences may not be members of any subtype. Total completeness means that every supertype occurrence must be a member of at least one subtype.
* **A single horizontal line under the circle represents a partial completeness constraint; a double horizontal line under the circle represents a total completeness constraint.

        Partial completeness / disjoint constraint: supertype has optional subtypes. subtype discriminator can be null; subtype set are unique

        Total completeness / disjoint constraint: every supertype occurrence is a member of only one subtype; subtype discriminator can not be null; subtype sets are unique

        Partial completeness / overlapping constraint: supertype has optional subtypes; subtype discriminators can be null; subtype sets are not unique

        Total completeness / Overlapping constraint: each supertype occurrence is a member of at least one subtype; subtype discriminators can not be null; subtype sets are not unique

## 5-1g Specialization and Generalization
* You can use various approaches to develop entity supertypes and subtypes. For example, you can first identify a regular entity and then identify all entity subtypes based on their distinguishing characteristics. You can also start by identifying multiple entity types and then later extract the common characteristics of those entities to create a higher-level supertype entity.
* **Specialization** is the top-down process of identifying lower-level, more specific entity subtypes from a higher-level entity supertype. Specialization is based on grouping the unique characteristics and relationships of the subtypes. In the aviation example, you used specialization to identify multiple entity subtypes from the original employee supertype. **Generalization** is the bottom-up process of identifying a higher-level, more generic entity supertype from lower-level entity subtypes. Generalization is based on groupping the common characteristics and relationships of the subtypes. For example, you might identify multiple types of musical instruments: piano, violin, and guitar. Using the generalization approach, you could identify a "string instrument" entity supertype to hold the common characteristic of the multiple subtypes.

## 5-2 Entity Clustering
* Developing an ER diagram entails the discovery of possibly hundreds of entity types and their respective relationships. Generally, the data modeler will develop an initial ERD that contains a few entities. As the design approaches completion, the ERD will contain hundreds of entities and relationships that crowd the diagram to the point of making it unreadable and inefficient as a communication tool. In those cases, you can use entity clusters to minimize the number of entities shown in the ERD.
* An **entity cluster** is a "virtual" entity type used to represent multiple entities and relationships in the ERD. An entity cluster is formed by combining multiple interrelated entities into a single, abstract entity object. An entity cluster is considered "virtual" or " abstract" in the sense that it is not actually an entity in the final ERD. instead, it is a temporary entity used to represent multiple entities and relationships, with the purpose of simplifying the ERD and thus enhancing its readability.
* Note also that the ERD does not show attributes for the entities. When using entity clusters, the key attributes of the combined entities are no longer available. Without the key attributes, primary key inheritance rules change. In turn, the change in the inheritance rules can have undesirable consequences, such as changes in relationships--from identifying to nonidentifying or vice versa--and the loss of foreign key attributes from some entities. **To eliminate those problems, the general rule is to avoid the display of attributes when entity clusters are used.**

## 5-3 Entity Integrity: Selecting Primary Keys

### Guidelines
* First, you should understand the function of a primary key. Its main function si to uniquely identify an entity instance or row within a table. In particular, given a primary key value--that is, the determinant--the relational model can determine the value of all dependent attributes that "describe" the entity. **Note that identifcation and description are separate semantic constructs in the model.** *The function of the primary keys is to guarantee entity integrity, not to "describe" the entity*. 



# Chapter 6: Normalization of Database Tables
* Normalization is a process for evaluating and correcting tables structures to minimize data redundancies, thereby reducing the likelihood of data anomalies
* Normalization works through a series of stages called normal forms. The first three stage are described as first normal form (1NF), second normal form (2NF), and third normal form (3NF). From a structual point of view, 2NF is better than 1NF, and 3NF is better than 2NF. For most purposes in business database design, 3NF is as high as you need to go in the normalization process. However, you will discover that properly designed 3NF structures also meet the requirements of fourth normal form (4NF).
* Althoug normalization is a very important ingredient in database design, you should not assume that the highest level of normalization is always the most desirable. Generally, the higher the normal form, the more relational join operations you need to produce a specified output. Also, more resources are required by the database system to respond to end-user queries. A successful design must also consider end-user demand for fast performance. **Therefore, you will occasionally need to denormalize some portions of a database design to meet performance requirements. The price you pay for increased performance through denormalization is greater data redundancy.**

* First normal form (1NF): Table format, no repeating groups, and PK identified
* Second normal form (2NF): 1NF and no partial dependencies
* Third normal form (3NF): 2NF and no transitive dependencies
* Boyce-Codd normal form (BCNF): Every determinant is a candidate key (sepcial case of 3NF)
* Fourth normal form (4NF): 3NF and no independent multivalued dependencies

## Conversion to First Normal Form
* Step 1: Eliminate the Repeating Groups
* Step 2: Identify the Primary key
* Step 3: Identify all dependencies

## Conversion to Second Normal Form
* Conversion to 2NF occurs only when the 1NF has a commposite primary key. If the 1NF has a single-attribute primary key, then the table is automatically in 2NF. The 1NF-to-2NF conversion is simple
* Step 1: Make new tables to eliminate partial dependencies
* Step 2: Reassign Corresponding dependent attributes
* A table is in 2NF when: 1. it is in 1NF; and 2. It includes no partial dependencies, no attribute is dependent on only a portion of the primary key

## Conversion to Third Normal Form (3NF)
* Step 1: Make new tables to eliminate transitive dependencies
* Step 2: Reassign corresponding dependent attributes
* A table is in 3NF when: 1. It is in 2NF; 2. It contains no transitive dependencies

* It is interesting to note the similarities between resolving 2NF and 3NF problems. To convert a table from 1NF to 2NF, it is necessary to remove the partial dependencies. To convert a table from 2NF to 3Nf, it is necessary to remove the transitive dependencies. No matter whether the "problem" dependency is a partial dependency or a transitive dependency, the solution is the same: create a new table for each problem dependency. The determinant of the problem dependency remains in the original table and is placed as the primary key of the new table. The dependents of the problem dependency are removed from the original table and placed as nonprime attributes in the new table.

* A transitive dependency was defined to exist when one nonprime attribute determined another nonprime attribute.
* In the presence of multiple candidate keys, \
a nonprime attribute as an attribute that is not a part of any candidate key

## 6.4 Improving the Design
* A surrogate key, is an artificial PK introduced by the designer with the purpose of simplifying the assignment of primary keys to tables. Surrogate keys are usually numeric, they are often generated automatically by the DBMS, they are free of semantic context (they have no special meaning), and they are usually hidden from the end users.
* An **atomic attribute** is one that can not be further subdivided. Such an attribute is said to display **atomicity**. Clearly, the use of the EMP_NAME is EMPLOYEE table is not atomic because EMP_NAME can be decomposed into a last name, a first name, and an initial.

page 220

END Chapter 6
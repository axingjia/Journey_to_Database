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
* An **entity supertype** is a gernic entity type that is related to one or more entity subtypes. **The entity supertype contains common characteristics, and the entity subtypes each contain their own unique characteristics.**

* Two criteria help the designer determine when to use subtypes and supertypes: 1. There must be different, identifiable kinds or types of the entity in the user's environment; 2. The different kinds or types of instances should each have one or more attributes that are unique to that kind or type of instance.
* CLERK would not be an acceptable subtype of EMPLOYEE because it only satisfies one of the criteria--it is an identifiable kind of employee--but none of the attributes are unique to just clerks.

## 5-1b Specialization Hierarchy
* [def] special hierarchy: A hierarchy based on the top-down process of identifying lower-level, more specific entity subtypes from a higher-level entity supertype. Specialization is based on grouping unique characteristics and relationships of the subtypes.
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
* Second, primary keys and foreign keys are used to implement relationships among entities. However, the implementation of such relationships is done mostly behind the scenes, hidden from end users. In the real world, end users identify objects based on the characteristics they know about the object. For example, when shopping at a grocery store, you select products by taking them from a display shelf and reading the labels, not by looking at the stock number. It is wise for database applications to mimic the human selection process as much as possible. Therefore, database applications should let the end user choose as much as possible. Therefore, database applications should let the end user choose among multiple descriptive narratives of different objects, using primary key values behind the scenes. Keep those concepts in mind, look at Table 5.3, which summarizes desirable primary key characteristics.

#### 5-3c When to Use Compositive Primary Keys
* In the previous section, you learned about the desirable characteristics of primary keys. For example, you learned that the primary key should use the minimum number of attributes possible. However, that does not mean that composite keys are not permitted in a model. In fact, compostie primary keys are particular useful in two cases:

        * As identifiers of composite entities, in which each primary key combination is allowed only once in the M:N relationship
        * As identifiers of weak entities, in which the weak entity has a strong identifying relationship with the parent entity

* To illustrate the first case, assume that you have a STUDENT entity set and a CLASS entity set. In addition, assume that those two sets are related in an M:n relationship via an ENROLL entity set, in which each student or class combinatino may appear only once in the composite entity
* The commposite primary key automatically provides the benefit of ensuring that there can not be duplicate values--that is, it ensures that the same student can not enroll more than once in the same class.
* In the second case, a weak entity in a strong identifying relationship with a parent entity is normally used to represent one of two situations:

        1. A real-world object that is existence-dependent on another real-world object. Such objects are distinguishable in the real world. A dependent and an employee are two separate people who exist independently of each other. However, such objects can exist in the modal only when they relate to each other in a strong identifying relationship. For example, the relationship between EMPLOYEE and DEPENDENT is one of existence dependency, in which the primary key of dependent entity is a composite key that contains the key of the parent entity.
        2. A real-world object that is represented in the data model as two separate entities in a strong identifying relationship. For example, the real-world invoice object is represented by two entities in a data model: INVOICE and LINE. Clearly, the LINE entity does not exist in the real world as the independent object but as part of an INVOICE.
* In both situations, having a strong identifying relationship ensures that the dependent entity can exist only when it is related to the parent entity. In summary, the selection of a composite primary key for composite and weak entity types provides benefits that enhance the integrity and consistency of the model.

#### 5-3d When to Use Surrogate Primary Keys
* In some instances a primary key doesn't exist in the real world or the existing natural key might not be a suitable primary key. In these cases, it is standard practice to create a surrogate key. A surrogate key is a primary key created by the datbase designer to simplify the identification of entity instance. The surrogate key has no meaning in the user's environment--it exists only to distinguish one entity instance from another (just like any other primary key). One practical advantage of a surrogate key is that because it has no intrinsic meaning, values for it can be generated by the DBMS to ensure that unique values are always provided.



        Table 5.3: DESIRABLE PRIMARY KEY CHARACTERTISCS
        * unique values: The PK must uniquely identify each entity instance. A primary key must be able to guarantee unique values. It can not contain nulls.
        * Nonintelligent: The PK should not have embedded semantic meaning other than to uniquely identify each entity instance. An attribute with embedded semantic meaning is probably better used as a descriptive characteristic of the entity as an identifier. For example, a student ID of 650973 would be preferred over Smith, Martha L, as a primary key identifier.
        * No change over time: If an attribute has semantic meaning, it might be subject to updates, which is why names do not make good primary keys. If Vickie Smith is the primary key, what happens if she changes her name when she gets married? if a primary key is subject to change, the foreign key values must be updated, thus adding to the database work load. Furthermore, changing a primary key value means that you are basically changing the identity of an entity. In short, the PK should be permanent and unchangeable.
        * Preferably single-attribute: A primary key should have the minimum number of attributes possible (irreducible). Single-attribute primary keys are desirable but not required. Single-attribute primary keys simplify the implementation of foreign keys. Having multiple-attribute primary keys can cause primary keys of related entities to grow through the possible addition of many attributes, thus adding to the database workload and making (application) coding more cumbersome
        * Preferably numeric: Unique values can be better managed when they are numeric, because the database can use internal routines to implement a counter-style attribute that automaticall increments values with the addition of each new row. In fact, most database systems include the ability to use special constructs, such as Autonumber in Microsoft Access, sequence in Oracle, and uniqueidentifier in MS SQL Server to support self-incrementing primary key attributes
        * Security-compliant: The selected primary key must not be composed of any attribute(s) that might be considered a security risk or violation. For example, using a Social Security number as a PK in an EMPLOYEE table is not a good idea.




#### 5-4 Design Cases: learning Flexible Database Design
* Data modeling and database design require skills that are acquired through experience. In turn, experience is acquired through practice--regular and frequent repetition, applying the concepts learned to specific and different design problems. This section presents four special design cases that highlight the importance of flexible designs, proper identification of primary keys, and placement of foreign keys.

##### 5-4a Design Case 1: Implementing 1:1 Relationship
* Foreign keys work with primary keys to properly implement relationships in the relational model. The basic rule is very simple: put the primary key of the "one" side (the parent entity) on the "many" side (the dependent entity) as a forign key. However, where do you place the foreign key when you are working with a 1:1 relationship? For example, take the case of a 1:1 relationship between EMPLOYEE and DEPARTMENT based on teh business rule "one EMPLOYEE is the manager of one DEPARTMENT, and one DEPARTMENT is managed by one EMPLOYEE". In that case, there are **two options** for selecting and placing the foreing key:
1. Place a foreign key in both entities. This option is derived from the basic rule you learn in Chapter 4. Place EMP_NUM as a foreign key in DEPARTMENT, and place DEPT_ID as a foreign key in EMPLOYEE. However, this solution is not recommended because it duplicates work, and it could conflict with other existing relationship. (Remember that DEPARTMENT and EMPLOYEE also participate in a 1:M relationship--one department employs many employees)
2. Place a foreign key in one of the entities. In that case, the primary key of one of the two entities appear as a foreign key in the other entity. That is the preferred solution, but a question remains: which primary key should be used as a foreign key? The answer is found in Table 5.5, which shows the rationale for selecting the foreign key in a 1:1 relationship based on the relationship properties in the ERD.

        TABLE 5.5: SELECTION OF FOREIGN KEY IN A 1:1 RELATIONSHIP
        Case I: One side is mandatory and the other side
            Action: place the PK of the entity on the mandatory side in the entity on the optional side as a FK, and make the FK mandatory
        Case II: Both sides are optional
            Action: Select the FK that causes the fewest nulls, or place the FK in the entity in which the (relationship) role is played
        Case III: Both sides are mandatory
            Action: See Case II, or consider revising your model to ensure that the two entities do not belong together in a single entity.

##### 5-4b Design Case 2: Maintaining History of Time-Variant Data
* Company managers generally realize that good decision making is based on the information generated through the data stored in databases. Such data reflects both curent and past events. Company managers use the data stored in databases to answer questions such as "how do the current company profits compared to those of previous years?" and "What are XYZ product's sales trends?" In other words, the data stored in databases reflects not only current data but also historic data.
* Normally, data changes are managed by replacing the existing attribute value with the new value, without regard to the previous value. However, in some situations the history of values for a given attribute must be preserved. From a data-modeling point of view, **time-variant data** refers to data whose values change over time and for which you must keep a history of the data changes. You could argue that all data in a database is subject to change over time and is therefore time variant. However, some attribute values, such as your date of birth or your Social Security number, are not time variant. On the other hand, attributes such as you student GPA or your bank account balanaces are subject to change over time. Sometimes the data changes are externally originated and event driven, such as a product price change. On other occasions, changes are based on well-defined schedules, such as the daily stock quote "open" and "close" values.
* The storage of time-variant data requires changes in the data model; the type of change depends on the nature of the data. Some time-variant data is equivalent to having a multivalued attribute in your entity. To model this type of time-variant data, you msut create a new entity in a 1:M relationship with the original entity. This new entity will contain the new value, the date of the change, and any other attribute that is pertinent to the event being modeled. For example, if you want to track salary histories for each employee, then the EMP_SALARY attribute become multivalued, as shown in Figure 5.9. In this case, for each employee, there will be one or more records in the SALARY_HIST entity, which stores the salary amount and the date when the new salary goes into effect.

        Figure 5.9 Maintaining Salary History
        EMPLOYEE (EMP_NUM (PK), EMP_LNAME,EMP_FNAME,EMP_INITIAL,EMP_E_MAIL,JOB_CODE,EMP_SALARY)
        SALARY_HIST (EMP_NUM(PK,FK1), SALARY_START_DATE(PK), SALARY_AMT)

* Other time-variant data can trun a 1:M relationship in to an M:N relationship. Assume that in addition to employee data, your data model includes data about the different departments in the organization and which employee manages each department. Assuming that each department is managed by only one employee and each employee can manage one department at most, then a 1:1 relationship would exist between EMPLOYEE and DEPARTMENT. This relationship would record the current manager of each department. However, if you want to keep track of the history of all department managers as well as the current manager, you can create the model shown in Figure 5.10.
* **Note that in Figure 5.10, the MGR_HIST entity has a 1:M relationship with EMPLOYEE and a 1:M relationship with DEPARTMENT to reflect the fact that an employee could be the manager of many different departments over time, and a department could have many different employee managers.** Because you are recording time-variant data, you must store the DATE_ASSIGN attribute in the MGR_HIST entity to provide the date that  the employee (EMP_NUM) became the department manager. The primary key of MGR_HIST permits the same employee to be the manager of the same department but on different dates. If that scenario is not the case in your environment--**if, for example, an employee is the manager of a department only once-- you could make DATE_ASSIGN a nonprime attribute in the MGR_HIST entity.**
* Note in Figure 5.10 that "manages" relationship is option in theory and redundant in practice. In any time, you coukld identify the manager of a department by retrieving the most recent DATE_ASSIGN date from MGR_HIST for a given department. On the other hand, the ERD in Figure 5.10 differentiates between current data and historic data. The current manager relationship is implemented by the "manage" relationship between EMPLOYEE and DEPARTMENT. Additionally, the histoic data is managed through EMP_MGR_HIST and DEPT_MGR_HIST. The trade-off with that model is that each time a new manager is assigned to a department, there will be two data modifications: one update in DEPARTMENT entity and one innsert in the MGR_HIST entity.
* The flexibility of the model proposed in Figure 5.10 becomes more apparent when you add the 1:M "one department employs many employees" relationship. In that case, the PK of the "1" side (DEPT_ID) appears in the "many" side (EMPLOYEE) as a foreign key. Now suppose you would like to keep track of the job history for each of the company's employee--you'd probably want to store the department, the job code, the date assigned, and the salary. To accomplish that task, you could modify the model in Figure 5.10 by adding a JOB_HIST entity. Figure 5.11 shows the use of the new JOB_HIST entity to maintain the employee's history

        EMPLOYEE 1:M MGR_HIST
        MGR_HIST M:1 DEPARTMENT

        EMPLOYEE (EMP_NUM(PK), EMP_LNAME, EMP_FNAME, EMP_INITIAL, EMP_E_MAIL, JOB_CODE, EMP_SALARY)
        MGR_HIST (EMP_NUM(PK,FK1), DEPT_ID(PK,FK2), PK)
        DEPARTMENT (DEPT_ID(PK), DEPT_NAME, EMP_NUM(FK), DATE_ASSIGN)
        

        EMPLOYEE 1:M JOB_HIST
        DEPARTMENT 1:M JOB_HIST

        JOB_HIST(EMP_NUM(PK,FK1), DEPT_ID(PK,FK2), DATE_ASSIGN(PK), JOB_CODE, EMP_SALARY)

* Again, it is worth emphasizing that the "manages" and "employs" relationships are theoretically optional and redundant in practice. You can always find out where each employee works by looking at the job history and selecting only the most current data row for each employee. However, as you will discover in Chapter 7, Introduction to SQL, and in Chapter 8, Advanced SQL, **finding where each employee works is not a trivial task.** Therefore, the model represented in Figure 5.11 includes the **admittedly redundant but unquestionably useful "manages" and "employs" relationships to separate current data from historic data.**

#### 5-4c Design Case 3: Fan Traps
* Creating a data model requires proper identification of the data relationships among entities. However, due to miscommunication or incomplete understanding of the business rules or processes, it is not uncommon to misidentify relationship among entities. Under those circumstances, the ERD may contain a design trap. A design trap occurs when a relationship is improperly or incompletely identified and is therefore represented in a way that is not consistent with the real world. **The most common design trap is known as a fan trap.**
* A fan trap occurs when you have one entity in two 1:M relationships to other entities, thus producing an association among the other entities that is not expressed in the model. For example, **assume that the JCB basketball league has many divisions. Each division has many players, and each division has many teams. Given those "incomplete" business rules, you might create an ERD that looks like the one in Figure 5.12.**

        Figure 5.12 INCORRECT ERD WITH FAN TRAP PROBLEM

        DIVISION 1:M TEAM
        DIVISION 1:M PLAYER

        Team (TEAM_ID (PK), TEAM_NAME, DIV_ID(FK1))
        DIVISION (DIV_ID (PK),DIV_NAME)
        PLAYER (PLAYER_ID (PK), PLAYER_NAME,DIV_ID (FK1))


* As you can see in Figure 5.12, DIVISION is in a 1:M relationship with TEAM and in a 1:M relationship with PLAYER. Although that representation is semantically correct, the relationships are not properly identified. For example, **there is no way to identify which players belong to which team.** Figure 5.12 also shows a sample instance relationship representation for the ERD. Note that the relationship lines for the DIVISION instances fan out to the TEAM and PLAYER entity instances--**thus the "fan trap" label.**
* Figure 5.13 shows the correct ERD after the fan trap has been eliminated. Note that, in this case, **DIVISION is in a 1:M relationship with TEAM. In turn, TEAM is in a 1:M relationship with PLAYER.** Figure 5.13 also shows the instance relationship representation after eliminating the fan trap.
* Given the design in Figure 5.13, note how easy it is to see which players play for which team. However, to find out which players play in which division, you first need to see what teams belong to each division, and then you need to find out which players play on each team. **In other words, there is a transitive relationship between DIVISION and PLAYER via the TEAM entity.**

#### 5-4d Design Case 4: Redundant Relationships
* Although redundancy is often good to have in computer environments (multiple backups in multiple places, for example),  redundancy is seldom good in the database environment. (As you learn in Chapter 3, The Relational Database Model, redundancies can cause data anormalies in a database). Redundant relationships occur when there are multiple relatinship paths between related entities. The main concern with redundant relationships is that they remain consistent across the model. However, it is important to note that some designs use redundant relationships as a way to simplify the design.
* An example of redundant relationships was first introduced in Figure 5.10 during the discussion of maintaining a history of time-variant data. However, the use of the redundant "manages" and "employs" relationships was justified by the fact that such relationship dealt with current data rather than historic data. Another more specific example of a redundant relationship is represented in Figure 5.14.
* In Figure 5.14, note the transitive 1:M relationship between DIVISION and PLAYER through the TEAM entity set. Therefore, the relationship that connects DIVISION and PLAYER is redundant, for all practical purposes. In that case, the relationship could be safety deleted without losing any information-generationa capabilities in the model


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

SKIM

#### 6-7 Normalization and Database Design
* The table shown in Figure 6.6 illustrate how normalization procedures can be used to procude good tables from poor ones. You will likely have ample opportunity to put this skill into practice when you begin to work wit hreal-world databases. Normalization should be part of the design process. Therefore, make sure that proposed entities meet the required normal form before the table structures are created. Keep in mind that if you follow the design procedures discussed in Chapters 3 and 4, the likelihood of data anomalies will be small. However, even the best database designers are known to make occasional mistakes that come to light during normalization checks. Also, many of the real-world databases you encounter will have been improperly designed or burdened with anomalies if they were improperly modified over the course of time. That means you might be asked to redeisng and modify existing databases that are, in effect, anomaly traps. Therefore, you should be aware of good design principles and procedures as well as normalization procedures.
* First, an ERD is created through an iterative process. You begin by identifying relevant entities, their attributes, and their relationships. Then you use the results to identify additional entities and attributes. The ERD provides the big picture, or macro view, of an organization's data requirements and operations.
* Second, normalization focuses on the characteristics of specific entities; that is, normalization represents a micro view of the entities within the ERD. Also, as you learned in the previous sections of this chapter, the normalization process might yield additional entities and attributes to be incorporated into the ERD. Therefore, it is difficult to separate normalization from ER modeling; the two techniques are used in an iterative and incremental process.
* To understand the proper role of normalization in the desing process, you should reexmine the operations of the contracting company whose tables were normalized in the preceding sections. Those operations can be summarized by using the following business rules:

        * The company manages many projects
        * Each project requires the services of many employees.
        * An employee may be assigned to several different projects
        * Some employees are not assigned to a project and perform duties not specifically related to a project. Some employees are part of a labor pool, to be shared by all project teams. For example, the company's executive secretary would not be assigned to any one particular project.
        * Each employee has a single primary job classfication, which determines the hourly billing rate.
        * Many employees can have the same job classification. For example, the company employs more than one electical engineer.

* Given that simple description of the company's operations, two entities and their attributes are initially defined:

        * PROJECT (PROJECT_NUM (PK), PROJ_NAME)
        * EMPLOYEE (EMP_NUM (PK), EMP_LNAME, EMP_FNAME, EMP_INITIAL, JOB_DESCRIPTION, JOB_CHG_HOUR)

SKIP

#### 6-8 Denormalization
* It is important to remember that the optimal relational database implementation requires that all tables be at least in 3NF. A good relational DBMS excels at managing normalized relations--that is, relations void of any unnecessary redundancies taht might cause data anomalies. Although the creation of normalized relations is an important database design goal, it is only one of many such goals. Good database design also considers processing (or reporting) requirements and processing speed. The problem with normalization is that as tables are decomposed to conform to normalization requirements, teh number of database table expands. Therefore, in order to generate information, data must be put together from various tables. Joining a large number of tables take additional input/output (I/O) operations and processing logic, thereby reducing system speed. most relational database systems are able to handle joins very efficiently. However, rare and occasional circumstances may allows some degree of denormalization, so processing speed can be increased.
* Keep in mind that the advantage of higher processing speed must be carefully weighed against the disadvantage of data anomalies. On the otehr hand, some anomalies are of only theoretical interest. For example, should people in real-world database environment worry that a ZIP_CODE determines CITY in a CUSTOMER table whose primary key is the customer number? Is it really practical to produce a separate table for 

        ZIP (ZIP_CODE (PK), CITY)

* To eliminate a transitive dependency from the CUSTOMER table? (Perhaps your answer to that questions changes if you are in the business of producing mailing lists). As explained earlier, the problem with denormalized relations and redundant data is that data integrity could be compromised due to the possibility of insert, update, and deletion anomalies. The advice is simple: use common sense during the normalization process.
* Furthermore, the database design process could, in some cases, introduce some small degree of redundant data in teh model, as seen in the previous example. This, in effect, creates "denormalized" relations. Table 6.6 shows some common examples of data redundancy that are generally found in database implementations.
* A more comprehensive example of the need of denormalization due to reporting requirements is the case of a faculty evaluation report in which each row lists the scores obtained during the last four semesters taught.
* Although this report seems simple enough, the problem is that the data isstored in a normalized table in which each row represents a different score for a given faculty member in a given semester.
* The difficulty of transposing multirow data to multicolumn data is compounded by the fact that the last four semesters taught are not necessarily the same for all faculty members. Some might have taken sabbaticals, some might have had research appointments, some might be new faculty with only two semesters on the job, and so on. To generate this report, the two tables in 

SKIP

# Chapter 7: Introduction to SQL
* SQL focuses on data definition (creating tables and index) and data manipulation (adding, modifying, deleting, and retrieving data)
* SQL functions fit into several broad categories:

        * It is a data manipulation language (DML). SQL includes commands to insert, update, delete, and retrieve data within the database table. The data manipulation commands you will learn in this chapter are list in Table #1 below. In this chapter, we will concentrate on the commands to retrieve data in interesting ways.
        * It is a data definition language (DDL). SQL includes commands to create database objects such as tables, indexes, and views, as well as commands to define access rights to those database objects. Some common data definition commands you will learn about in Chapter 8, Advanced SQL, are list in Table #2.
        * It is a transaction control language (TCL). The DML commands in SQL are executed within the context of a **transaction**, which is a logical unit of work composed of one or more SQL statements, as defined by business rules (see Chapter 10, Transaction Management and Concurrency Control). SQL provides commands to control the processing of these statements an indivisible unit of work. These will be discussed in Chapter 8, after you learn about the DML commands that compose a transaction.
        * It is a data control language (DCL). Data control commands are used to control access to data objects, such as giving a one user permission to only view the PRODUCT table, and g iving another use permission to change the data in the PRODUCT table. Common TCL and DCL commands are shown in Table #3.

* SQL is relatively easy to learn. Its basic command set has a vocabulary of fewer than 100 words. Better yet, SQL is a nonprocedural language: you merely command what is to be done; you do not have to worry about how. For example, a single command creates the complex table structures required to store and manipulate data successfully; end users and programmers do not need to know the physical data storage format or the complex activities that take place when a SQL command is executed.
* The American National Standards Institute (ANSI) prescribes a standard SQL. The ANSI SQL standards are also accepted by the International Organization for Standardization (ISO), a consortium composed of national standards bodies of more than 150 countries. Although adherence to the ANSI/ISO SQL standard is usually required in commercial and government contract database specifications, many RDBMS vendors add their own special enhancements. Consequently, it is **seldom possible to move** a SQL-based application from one RDBMS to another without making some changes.


        Table #1
        SQL DATA MANIPULATION COMMANDS

        SELECT: Selects attributes from rows in one or more tables or views
            FROM: Specifies the tables fromm which data should be retrieved
            WHERE: Restricts the selection of rows based on a conditional expression
            GROUP BY: Groups the selected rows based on one or more attributes
            HAVING: Restricts the selectino of grouped rows based on a condition
            ORDER BY: Orders the selected rows based on one or more attributes
        INSERT: Inserts row(s) into a table
        UPDATE: Modifies an attribute's values in one or more table's rows
        DELETE: Deletes one or more rows from a table
        Comparison operators
            =, <, >, <=, >=, <>, !=: Used in conditional expressions
        Logical operators
            AND/OR/NOT: used in conditional expressions
        Special operators: used in conditional expressions
            BETWEEN: Checks whether an attribute value is within a range
            IN: Checks whether an attribute value matches any values any value within a value list
            LIKE: Check whether an attribute value matches a given string pattern
            EXISTS: Check whether a subquery returns any rows
            DISTINCT: Limits values to unique value
        Aggregate functions: Used with SELECT to return mathematical summaries on columns
            COUNT: Returns the number of rows with non-null values for a given column
            MIN: Returns the minimum attribute value found in a given column
            MAX: Returns the maximum attribute value found in a given column
            SUM: Returns the sum of all values for a given column
            AVG: Returns the average of all values for a given column


        Table #2
        SQL DATA Definition COMMMANDS
        CREATE SCHEMA AUTHORIZATION: Creates a database schema
        CREATE TABLE: Creates a new talbe in the user's database schema
            NOT NULL: Ensures that a column will not have null values
            UNIQUE: Ensures that a column will not have duplicate values
            PRIMARY KEY: Defines a primary key for a table
            FOREIGN KEY: Defines a foreign key for a table
            DEFAULT: Defines a default value for a column (when no value is given)
            CHECK: Validates data in an attribute
        CREATTE INDEX: Create an index for a table
        CREATE VIEW: Creates a dynamic subset of rows and columns from one or more tables
        ALTER TABLE: Modifies a table's definition (adds, modifies, or deletes attributes or constraints)
        CREATE TABLE AS: Create a new table based on a query in the user's database schema
        DROP TABLE: Permanently deletes a table (and its data)
        DROP INDEX: Permanently deletes an index
        DROP VIEW: Permanently deletes a view

        OTHER SQL COMMAND
        Transaction Control Language
            COMMIT: Permanently saves data changes
            ROLLBACK: Restores data to its original values
        Data Control Language
            GRANT: Gives a user permission to take a system action or access a data object
            REVOKE: Removes a previously granted permission from a user

SKIM: ALL REMEMBERED till 7-7

### SQL Function
* CONVERT: Convert can be used to perform a wide array of data type conversions as discussed. It can also be used to format date data.

        CONVERT(varchar(length),date_value,fmt_code)
        fmt_code=format used; can be:
        1: MM/DD/YY
        101: MM/DD/YYYY
        2: YY.MM.DD
        102:YY.MM.DD
        3:DD/MM/YY
        103: DD/MM/YYYY
* YEAR: Returns a four-digit year
* MONTH: returns a two-digit month code
* DAY: Returns the number of the day 
* GETDATE(): SQL Server: Return today's date
* DATEADD SQL Server: Add a number of selected time period to a date. Syntax: DATEADD(datepart, number, date) Example: DATEADD(day,90,P_INDATE)
* DATEDIFF SQL Server: Subtracts two dates. DATEDIFF(datepart, startdate,enddate). Example: DATEDIFF(date,P_INDATE, GETDATE())

get to 7-10 beginning


(CL): Got wrong:

        ALTER TABLE Persons
            ADD CONSTRAINT df_City
            DEFAULT 'Sandnes' FOR City;

        Not: 

        ALTER TABLE Persons
            Modify City DEFAULT 'Sandnes'


* (CL): AND has higher precedence than OR

You delete the many side first

you insert the one side first

In Summary, chapter 7 can all be remembered

# Chapter 8: Advanced SQL

* CREATE [UNIQUE] INDEX indexname ON table (column1 [,column2])


        ALTER TABLE tablename 
            {ADD|MODIFY} (columnname datatype [{ADD|MODIFY} columnname datatype])

        ALTER TABLE tablename
            ADD constraint [ADD constraint]

        ALTER TABLE tablename
            DROP {PRIMARY KEY | COLUMN columnname | CONSTRAINT constraintname}

        Example:
        ALTER TABLE PRODUCT
            MODIFY (V_CODE CHAR(5))

        Example:
        ALTER TABLE PRODUCT
            MODIFY (P_PRICE DECIMAL(9,2))

        Example:
        ALTER TABLE PRODUCT
            ADD (P_SALECODE CHAR(1));

        Example:
        ALTER TABLE PART
            ADD PRIMARY KEY (PART_CODE);

        Example:
        ALTER TABLE PART
            ADD FOREIGN KEY (V_CODE) REFERENCES VENDOR;

        Example: 
        ALTER TABLE PART 
            ADD CHECK (PART_PRICE>=0);

        ALTER TABLE VENDOR 
            DROP COLUMN V_ORDER

        INSERT INTO tablename VALUES (value1, value2,...valuen)

        UPDATE tablename
        SET columnname=expression [,columnname=expression]
        [WHERE conditionlist]

* By default MySQl is set for "safe mode" for updates and deletes. This means that users can not update or delete rows from a table unless the UPDATE or DELETE command ihncludes a WHERE clause that provides a value for the primary key. To disable safe mode temporarily, set the SQL_SAFE_UPDATES variable to 0. Safe mode can be re-enabled by setting the variable back to 1. For example, to complete the DELETE command shown above, the following sequence could be used:

        SET SQL_SAFE_UPDATES=0;
        DELETE FROM PRODUCT WHERE P_MIN=5;
        SET SQL_SAFE_UPDATE=1

* To permanently disable safe mode, uncheck the safe mode option in MySQL Workbench under the Edit, Preference window.

### 8-4f Restoring Table Contents
* If you have not yet used the COMMIT command to store the changes permanently in the database, you can restore the database to its previous condition with the ROLLBACK commmand. ROLLBACK undoes any changes since the last COMMIT command and brings all of the data back to the values that existed before the changes were made. To restore the data to its "prechange" condition, type:

        ROLLBACK

* and then press Enter. Use the SELECT statement again to verify that the ROLLBACK restored the data to its original values.
* COMMIT and ROLLBACK work only with data manipulation commands that add, modify, or delete table rows. For example, assume that you perform these actions:

        1. CREATE a table called SALES
        2. INSERT 10 rows in the SALES table
        3. UPDATE two rows in the SALES table
        4. Execute the ROLLBACK command

* **Will the SALES table be removed by the ROLLBACK command? No, the ROLLBACK command will undo only the results of the INSERT and UPDATE commands. All data definition commands (CREATE TABLE) are automatically committed to the data dictionary and can not be rolled back. The COMMIT and ROLLBACK commandas are examined in greater detail in Chapter 10.

#### View
* A relational view has several special characteristics
1. **You can use the name of a view anywhere a table name is expected in a SQL statement**
2. Views are dynamically updated. That is, the view is recreated on demand each time it is invoked. Therefore, if new products are added or deleted to meet the criterion P_PRICE>50.00, **those new products will automatically appear or disappear in the PRICEGT50 view the next time the view is invoked**.
* View provide a level of security in the database because they can restrict users to seeing only specified columns and rows in a table. For example, if you have a commpany with hundreds of employees in several departments, you could give each department administrative assistant a view of certain attributes only for the employees who belong to that assistant's department.
* View may also be used as the basis for report. For example, if you need a report that shows a sumamry of total product cost and quantity-on-hand statistics grouped by vendor, you could create a PROD_STATS view as:

        CREATE VIEW PROD_STATS AS
        SELECT V_CODE...
        FROM PRODUCT 
        GROUP BY V_CODE

### Sequence
* Sequence are an indepedent object in the database. (Sequence are not a data type)
* Sequence have a name
* Sequence can be used anywhere a value is expected
* Sequence are not tied to a table or a column
* Sequence generate a numeric value that can be assigned to any column in any table
* The table attribute to which you assigned a value based on a sequence can be edited and modified


        CREATE SEQUENCE name [START WTIH n] [INCREMENT BY n] [CACHE |NOCHACHE]

        Where
            * name is the name of the sequence
            * n is an integer value that can be positive or negative
            * START WITH secifies the initial sequence value (the default value is 1)
            * INCREMENT BY determines the value by which the sequence is incremented (The default increment value is 1. The sequence increment can be positive or negative to enable you to create ascending or descending sequence)
            * The CACHE or NOCACHE/NO CACHE clause indicates whether the DBMS will preallocate sequence number in memory. Oracle uses NOCACHE as two words. If a cache size is not specified in SQL server, then the DBMS will determine a default cache size that is not guaranteed to be consistent across different databases.

* For example, you could create a sequence to automatically assign values to the customer code each time a new customer is added, and create another sequence to automatically assign values to the invoice number of each time a new invoice is added. The SQL code t oaccomplish thosee tasks is:

        CREATE SEQUENCE CUS_CODE_SEQ START WITH 20010 NOCACHE;
        CREATE SEQUENCE INV_NUMBER_SEQ START WITH 4010 NOCACHE;

You can check all of the sequences you have created by using the following SQL command, as illustrated in Figure 8.10

        SELECT * FROM USER_SEQUENCES;

MY: SKIP sequence because I will barely use it

#### 8-7 Procedural SQL
* Thus far, you have learned to use SQL to read, write, and delete data in the database. For example, you learned to update values in a record, to add records, and to delete records. Unfortunately, SQL does not support the conditional execution of procedures that are typically supported by a programming language using the general format:

        IF <condition>
            THEN <perform procedure>
                ELSE <perform alternate procedure>
        END If

* While Loop:

        DO WHILE
            <perform procedure>
        END DO

#### Trigger
* A trigger is procedural SQL code that is automatically invoked by the RBDMS upon the occurence of a given data manipulation event. It is useful to remember that:

        * A trigger is invoked before or after a data row is inserted, updated, or deleted
        * A trigger is associated with a database table
        * Each database table may have one or more triggers
        * A trigger is executed as part of the transaction that triggered it
        * Triggers can be used to enforce constraints that can not be enforced at the DBMS design and implementation levels
        * Triggers add functionality by automating critical actions and providing appropriate warnings and suggestions for remedial action. In fact, one of the most common uses for triggers is to facilitate the enforcement of referential integrity
        * Trigger can be used to update table values, insert records in tables, and call other stored procedures

* Triggers play a critical role in making the database truly useful; they also add processing power to the RDBMS and to the database system as a whole. Oracle recommends triggers for:

        * Auditing purposes (creating audit logs)
        * Automatic generation of derived column values
        * Enforcement of business or security constraints
        * Creation of replica tables for backup purposes

* Syntax:

        CREATE OR REPLACE TRIGGER trigger_name
        [BEFORE/AFTER] [DELETE/INSERT/UPDATE OF column_name] ON
        table_name
        [FOR EACH ROW]
        [DECLARE]
        [variable_namedata type[:=initial value]]
        BEGIN
        PL/SQL instructions;
        ...
        END;

* As you can see, a trigger definition contains the following parts:

        * The triggering timing: BEFORE or AFTER. This timing indicates when the trigger's PL/SQL code executes--in this case, before or after the triggering statement is completed.
        * The triggering event: The statement taht causes the trigger to execute (INSERT, UPDATE, or DELETE)
            -The triggering level: The two types of triggers are statement-level triggers and row-level triggers. A statement-level trigger is assumed if you omit the FOR EACH ROW keywords. This type of trigger is executed once, before or after the triggering statement is completed. This is the default case.
            -A row-level trigger requires use of the FOR EACH ROW keywords. This type of trigger is executed once for eac hrow affected by the triggering statement (In other words, if you update 10 rows, the trigger executes 10 times)
        * The triggering action: The PL/SQL code enclosed between the BEGIN and END keywords. Each statement inside the PL/SQL code must end with a semicolon (;).

        Example: 
        CREATE OR REPLACE TRIGGER TRG_PRODUCT_REORDER
        AFTER INSERT OR UPDATE OF P_QOH ON PRODUCT
        BEGIN
            UPDATE PRODUCT 
            SET P_REORDER=1
            WHERE P_QOH<=P_MIN
        END

        PS: The triggering action performs an UPDATE of all the rows in the PRODUCT table, even if the triggering statement updates just one row! This can affect the performance of teh database. Imagine what will happen if you have a PRODUCT table with 519,128 rows and you insert just one product. The trigger will update all 519,129 rows, including the rows that do not need an update

        Example 2:
        CREATE OR REPLACE TRIGGER TRG_PRODUCT_REORDER
        BEFORE INSERT OR UPDATE OF P_QOH, P_MIN ON PRODUCT
        FOR EACH ROW
        BEGIN
            IF :NEW.P_QOH <=:NEW.p_MIN THEN
                :NEW.P_REORDER :=1;
            ELSE
                :NEW.P_REORDER :=0;
            END IF;
        END;

* The trigger above is executed before the actual triggering statement is completed. The triggering timing is defined in line 2, BEFORE INSERT OR UPDATE. This clearly indicates that the triggering statement is executed before the INSERT or UPDATE completes, unlike the previous trigger examples.
* The trigger is a row-level trigger instead of a statement-level trigger. The FOR EACH ROW keywords make  the trigger a row-level trigger. Therefore, this trigger executes once for each row affected by the triggering statement
* The trigger action uses the :NEW attribute reference to change the value of the P_REORDER attribute.
* The use of the :NEW attribute references deserves a more detailed explanation. To understand its use, you must first consider a basic computing tenet: all changes are done first in primary memory and then transferred to permanent memory. In other words, the computer can not change anything directly in permanent storage (on disk). It msut first read the data from permanent storage to primary memory, then make the change in primary memory, and finally write the changed data back to permanent memory (on disk)

* Note the following important features of the code:

        * The trigger is automatically invoked for each affect row--in this case, all rows of the PRODUCT table. If you triggering statement would have affected only three rows, not all PRODUCT rows would have the correct P_REORDER value set, which is why the triggering statement was set up as shown.
        * The trigger will run only if you insert a new product row or update P_QOH or P_MIN. If you update any other attribute, the trigger will not run.

* You can also use a trigger to update an attribute in a table other than the one being modified. For example, suppose that you would like to create a trigger that automatically reduce the quantity on hand of a product with every sale. To accomplish that task, you must create a trigger for the LINE table that updates a row in the PRODUCT table.

        CREATE OR REPLACE TRIGGER TRG_LINE_PROD
        AFTER INSERT ON LINE
        FOR EACH ROW
        BEGIN 
            UPDATE PRODUCT
            SET P_QOH=P_QOH - :NEW.LINE_UNITS
            WHERE PRODUCT.P_CODE = :NEW.P_CODE
        END

        Example 2:
        CREATE OR REPLACE TRIGGER TRG_LINE_CUS
        AFTER INSERT ON LINE
        FOR EACH ROW
        DECLARE
            W_CUS CHAR(5);
            W_TOT NUMBER :=0; --to compute total cost
        BEGIN
            --this trigger fires up after an INSERT of a LINE
            -- it will update the CUS_BALANCE in CUSTOMER

            --1) get the CUS_CODE
            SELCT CUS_CODE INTO W_CUS
            FROM INVOICE
            WHERE INVOICE.INV_NUMBER =:NEW.INV_NUMBER;

            -- 2) compute the total of the current line
            W_TOT := :NEW.LINE_PRICE * :NEW.LINE_UNITS;

            -- 3) update the CUS_BALANCE in CUSTOMER
            UPDATE CUSTOMER 
            SET CUS_BALANCE =CUS_BALANCE + W_TOT
            WHERE CUS_CODE =W_CUS

            DBMS_OUTPUT.PUT_LINE ('=== Balance updated for customer: '|| W_CUS);
        END;

* Carefully examine the trigger:

        * The trigger is a row-level trigger that executes after each new LINE row is inserted
        * The DECLARE section in the trigger is used to declare any variables used inside the trigger code
        * You can declare a variable by assining a name, a data type, and (optionally) an initial value, as in the case of the W_TOT variable
        * The first step in the trigger code is to get the customer code (CUS_CODE) from the related INVOICE table. Note that the SELECT statement returns only one attribute (CUS_CODE) from the INVOICE table. Also note that the attribute returns only one value as specified by the use of the WHERE clause, to restrict the query output to a single value.
        * Note the use of the INTO clause within the SELECT statement. You use the INTO clause to assign a value from a SELECT statement to a variable (W_CUS) used within a trigger.
        * The second step in the trigger code computes the total of the line by multiplying :NEW.LINE_UNITS by :NEW.LINE and assigning the result to the W_TOT variable
        * The final step updates the customer balance by using an UPDATE statement and the W_TOT and W_CUS trigger variable

        SYNTAX:
        DROP TRIGGER trigger_name

#### Stored Procedure
* Stored procedure substantially reduce network traffic and increase performance. Because the procedure is stored at the server, there is no transmission of individual SQL statement over the network. The use of stored procedures improves system performance because all transactions are executted locally on the RDBMS, so each SQL statement does not have to travel over the network
* Stored procedures help reduce code duplication by means of code isolation and code sharing (creating unique PL/SQL modules that are called by application programs), thereby minimizing the chance of errors and the cost of application development and maintenance
* Syntax

        CREATE OR REPLACE PROCEDURE procedure_name [(argument[IN/OUT],data-type,...)]
            [IS/AS]
            [variable_namedata type [:=initial_value]]
        BEGIN 
            PL/SQL or SQL statements;
        END;

* Note the following important points about stored procedures and their syntax:

        * argument specifies the parameters that are passed to the stored procedure. A stored procedure could have zero or more arguments or parameters.
        * IN/OUT indicates whether the parameter is for input, output, or both.
        * data-type is one of the procedural SQL data types used in the RDBMS. The data types normally match those used in the RDBMS table creation statement
        * Variables can be declared between the keywords IS and BEGIN. You must specify the variable name, its data type, and (optionally) an initial value.

* Syntax:

        EXEC procedure_name[(parameter_list)];


#### Cursor
SKIP

#### Embedded SQL
SKIP

# Chapter 10: Transaction Management and Concurrency Control
* A transaction is a logical unit of work that must be entirely completed or entirely aborted; no intermediate states are acceptable.
* A consistent database state is one in which all data integrity constraints are satisfied

## Transaction Properties
* Atomicity requires that all operations (SQl requests) of a transaction be completed; if not, the transaction is aborted. If an transaction T1 has four SQL requests, all four requests must be successfully completed; otherwise, the entire transaction is aborted. In other words, a transaction is treated as a single, indivisible, logical unit of work.
* Consistency indicates the permanence of the database's consistent state. A transaction takes a database from one consistent state to another. When a transaction is completed, the database must be in consistent state. If any of the transaction parts violates an integrity constraint, the entire transaction is aborted.
* Isolation means that the data used during the execution of a transaction can not be used by a second transaction until the first one is completed. In other words, if transaction T1 is being executed and is using the data item X, that data item can not be accessed any other transaction (t2...Tn) until T1 ends. This property is particularly useful in multiuser database environments because several users can access and update the database at the same time.
* Durability ensures that once transaction changes are done and committed, they can not be undone or lost, even in the even of a system failure.
* **Serializability** ensures that the schedule for the concurrent execution of the transactions yields consistent results. This property is important in multiuser and distributed databases in which multiple transactions are likely to be executed concurrently. Naturally, if only a single transaction is exeucted, serializability is not an issue.

# Chapter 11: Database Performance Tuning and Query Optimization

## 11-1 Database Performance-Tuning Concepts
* End users expect their queries to return results as quickly as possible. How do you know that the performance of a database is good? Good database performance is hard to evaluate. How do you know if a 1.06-second query response time is good enough? It is easier to identify bad database performance than good database performance--all it take is end-user complaints about slow query results. Unfortunately, the same query might perform well one day and not so well two months later. Regardless of end user perceptions, the goal of database performance is to execute queries as fast as possible. Therefore, database performance must be closely monitored and regularly tuned. **Database performance tuning** refers to a set of activities and procedures designed to reduce the response time of the database system--that is, to ensure an end-user query is processed by the DBMS in the minimum amount of time.
* The time required by a query to return a result set depends on many factors, which tend to be wide-ranging and to vary among environments and among vendors. In general, the performance of a typical DBMS is constrained by three main factors: **CPU processing power, available primary memory (RAM), and input/output (hard disk and network) throuput. 
* naturally, the system will perform best when its hardware and software resources are optimized. However, in the real world, unlimited resources are not the norm; internal and external constraints always exist. Therefore, the system components should be optimized to obtain the best throughput possible with existing (and often limited) resources, which is why database performance tuning is important.
* Fine-tuning the performance of a system requires a holistic approach. That is, all factors must be checked to ensure that each one operates at its optimum level and has sufficient resources to minimize the occurrence of bottlenecks. Because database design is such an important factor in determining t he database system's performance efficiency, it is worth repeating this book's mantra
* **Good database performance starts with good database design**. No amount of fine-tuning will make a poorly designed database perform as well as a well-design database. This is particularly true when redesigning existing databases, where the end user expects unrealistic performance gains from older databases.
* what constitute a good, efficient database design? From the performance-tuning point of view, the database designer must ensure that the design makes use of features in the DBMS that guarantee the integrity and optimal performance of the database. This chapter provides fundamental knowledge that will help you optimize database performance by **selecting the appropriate database server configuration, using indexes, understanding table storage organization and data location, and implementing the most efficient SQL query syntax.**

## 11-1a Performance Tuning: Client and Server
* In general, database performance-tuning activities can be divided into those on the client side and those on the server side.

                * On the client side, the objective is to generate a SQL query that reutnrs the correct answer in the least amount of time, using the minimum amount of resources at the server end. The activities required to achieve that goal are commmonly refered to as **SQL performance tuning**.
                * On the server side, the DBMS environment must be properly configured to respond to clients' requests in the fastest way possible, while making optimum use of existing resources. The activities required to achieve that goal are commonly referred to as **DBMS performance tuning**.

* Keep in mind that DBMS implementations are typically more complex than just a two-tier client/server configuration. The network component plays a critical role in delivering messages between clients and servers; this is especially important in distributed databases. In this chapter however, we assume a fully optimized network, and therefore, our focus is on the database commponents. Even in multi-tier client/server environments that consist of a client front end, application middleware, and database server back end, performance-tuning activities are frequently divided into subtasks to ensure the fastest possible response time between any two component points. The datab ase administrator must work clsoely with the network group to ensure that database traffic flows efficiently in the network infrastructure. This is even more important when you consider that most database system service geographically disperse users.

11-1b DMBS Architecture
* The architecture of a DBMS is represented by the processes and structures (in memory and permanent storage) used to manage a database. Such processes collaborate with one another to perform specific function. Figure 11.1 illustrates the basic DBMS architecture.

                * All data in a database is stored in **data files**. A typical enterprise database is normally composed of several data files. A data file can contain rows fromm a single table, or it can contain rows from many different talbes. A database administrator (DBA) determines the initial size of the data files that make up the database; however, the data files can automatically expand as required in predefined increments known as **extent. For example, if more space is required, the DBA can define that each new extent will be in 10KB or 10MB increments.
                * Data files are generally grouped in file groups or table spaces. A **table space** or **file group** is a logical grouping of several data files that store data with similar characteristics. For example, you might have a system table space where the data dictionary table data is stored, a user data table space to store the user-created tables, an index table space to hold all indexes, and a temporary table space to do temporary sorts, grouping, and so on. Each time you create a new database, the DBMS automatically creates a minimum set of table spaces.
                * The **data cache** or **buffer cache**, is a shared, reserved memory area that stores the most recently accessed data blocks in RAM. the data read from the data files is stored in the data cache after the data has been read or before the data is written to the data files. The data cache also caches system catalog data and the contents of the indexes.
                * The **SQL cache**, or **procedure cache**, is a shared, reserved memory area that stores the most recently executed SQL statements or PL/SQL procedures, including triggers and functions. The SQL cache does not store the SQl written by the end user. Rather, the SQ: cache stores a "processed" version of the SQL that is ready for execution by the DBMS.
                * To work with the data, the DBMS must retrieve the data from permanet storage and place it in RAM. In other words, the data is retrieved from the data files and placed in the data cache.
                * To move data fromm permanent storage (data files) to RAM (data cache), the DBMS issues I/O requests and waits for the replies. An **input/output (I/O) request** is a low-level data access operation  that reads or writes data to and from computer devices, such as memory , hard disks, video, and printers. Note that an I/O disk read operation retrieves an entire physical disk block, generally containing multiple rows, from permanent storage to the data cache, even if you will use only one attribute from only one row. The physical disk block size depends on the oeprating system and could be 4K, 8K, 16K, 32K, 64K, or even larger. Furthermore, depending on the circumstances, a DBMS might issue a single-block read request or a multiblock read request.
                * Working with data in the data cache is many times faster tha nworking with data in the data files becasue the DBMS does not have to wait for the hard disk to retreive the data; no hard disk I/O operations are needed to work within the data cache.
                * Most performance-tuning activities focus on minimizing the number of I/O operations because using I/O operations is many times slower than reading data form the data cache. For example, as of this writing, RAM access times range from 5 to 70 nanoseconds, while magnetic hard disk access time range from 5 to 15 milliseconds and SSD access times range from 35 to 100 microsecond. This means that hard disks are several orders of magnitude slower than RAM.

* Figure 11.1 also illustrates some  typical DBMS processes. Although the number of processes and their names vary from vendor to vendor, the functionality is similar. The following processes are represented in Figure 11.1:

                * Listener. The listener process listens for clients' requests and handles the processing of the SQl requests to other DBMS processes. once a request is received, the listener passes the request to the appropriate user process.
                * User. The DBMS creates a user process to manage each client session. Therefore, when you log on the DBMS, you are assigned a user process. This process handles all requests you submit to the server. There are many user processes--at least one per logged-in client.
                * Scheduler. The scheduler process organizes the concurrent execution of SQL requests. 
                * Lock manager. This process manages all locks placed on database objects, including disk pages.
                * optimizer. The optimizer process analyzes SQL queries and finds the most efficient way to access the data. 

## 11-1c Database Query Optmization Modes

## 11-3 Indexes and Query Optimization
* Indexes are crucial in speeding up data access because they facilitate searching, sorting, and using aggregate functions and even join operations. The improvement in data access speed occurs because an index is an ordered set of values that contains the index key and pointers. The pointers are the row IDs for the actual table rows. Conceptually, a data index is similar to a book index. When you use a book index, you look up a word, which is similar to the index key. The word is accompanied by one or more page numbers where the word is used; these numbers are similar  to pointers.
* An index scan is more efficient than a full table scan because the index data is preordered and the amount of data is usually much smaller. Therefore, when performing searches, it is almost always better for the DBMS to use the index to access a table than to scan all rows in a table sequentially. For example, Figure 11.3 shows the index representation of a CUSTOMER table with 14,786 rows and the index STATE_NDX on the CUS_STATE attribute.
* If there is no index, the DBMS will perform a full-table scan and read all 14,786 customer rows. Assuming that the index STATE_NDX is created (and analyzed), the DBMS will automatically use the index to locate the first customer with a state equal to 'FL' and then proceed to read all subsequent CUSTOMER rows, using the row IDs in the index as a guide. Assuming that only five rows meeting the condition CUS_STATE='FL' there are five accesses to the index and five accesses to the data, for a total of 10 I/O accesses. The DBMS would be saved from reading approximately 14,776 I/O requests for customer rows that do not meet the criteria. That is a lot of CPU cycles!
* If indexes are so important, why not index every column in every table? The simple answer is that it is not practical to do so. Indexing every column in every table overtaxes the DBMS in terms of index maintenance processing, especially if the table has many attributes and rows, or requires many inserts, updates, and deletes.
* One measure that determines the need for an index is the data sparsity of the column you want to index. **Data sparsity** refers to the number of different values a column could have. For example, a STU_SEX column in a STUDENT table can have only two possible values, M or F; therefore, that column is said to have low sparsity. In contrast, the STU_DOB column that stores the student date of birth can have many different date values; therefore, that column is said to have high sparsity.Knowing the sparsity helps you decide whether the use of an index is appropriate. **For example, when you perform a search in a column with low sparsity, you are likely to read a high percentage of the table rows anyways; therefore, index processing might be unncessary work.**

* Most DBMS implement indexes using one of the following data structures:
* **Hash index**: a hash index is based on an ordered list of hash values. A hash algorithm is used to create a hash value from a key column. This value points to an entry in a hash table, which in turn points to the actual location of the data row. This type of index is good for simple and fast lookup operations based on equality conditions-- for example, LNAME='Scott' and FNAME='Shannon'
* **B-tree index**: the B-tree index is an ordered data structure organized as an upside-down tree. The index tree is stored separately from teh data. The lower-level leaves  the B-tree index contain the pointers to the actual data rows. B-tree indexes are "self-balanced", which means that it takes approximately the same amount of time to access any given row in the index. This is the default and most common type of index used in databases. The B-tree index is used mainly in tables in which column values repeat a relatively small number of times.
* **Bitmap index**: A bitmap index uses a bit array (0s and 1s) to represent the existence of a value or condition. These indexes are used mostly in data warehouse applications in tables with a large number of rows in which a small number of column values repeat many times. Bitmap indexes tend to use less space than B-tree indexes because they use bits instead of bytes to store their data.



                FIGURE 11.1 BASIC DBMS ARCHITECTURE

                Client send SQL query to DBMS process running in primary memory (RAM)

                DBMS processes include: listerner, user process, scheduler, lock manager, optimizer, SQL cache, Data cache

                DBMS Processes <-  I/O operations  -> Database data files stored in permanent secondary memory (hard disk)

                

# Chapter 13: Business Intelligence and Data Warehouses
* Business intelligence (BI) is the collection of best practices and software tools developed to support business decision making in this age of globalization, emerging markets, rapid change, and increasing regulation. The complexity and range of information required to support business decisions has increased, and operational database structures were unable to support all of these requirements. Therefore, a new data storage facility, called a **data warehouse**, developed. **The data warehouse extracts its data from operational database as well as from external sources, providing a more comprehensive data pool.
* Additionally, new ways to analyze and present decision support data were developed. **Online analytical processing (OLAP) provides advanced data analysis and visualization tools, including multidimensional data analysis. 

## 13-1 The Need for Data Analysis
* Organizations tend to grow and prosper as they gain a better understanding of their environment. Most managers need to track daily transactions to evaluate how the business is performing. By tapping into the operational database, management can develop an understanding of how the company is performing and evaluate whether the current strategies meet organizational goals. In addition, analyzing the company data can provide insightful information about short-term tactical evaluations and strategic questions, such as: **Are our sales promotions working? What market percentage are we controlling? Are we attracting new customers?** Tactical and strategic decisions are also shaped by constant pressure from external and internal forces, including globalization, the cultural and legal environment, and technology.
* Organizations are always looking for a commpetitive advantage through product development, market positioning, sales promotions, and customer service. Thanks to the Internet, customers are more informed than ever about the product they want and the prices they are willing to pay. Technology advances allow customers to place orders using their smart phones while they commute to work in the morning. Decision makers can no longer wait a couple of days for a report to be generated; they are compelled to make quick decisions if they want to remain competitive. Every day, TV ads offer low-price warranties, instant price matching, and so on. How can companies survive on lower margins and still make a profit? **The key is in having the right data at the right time to support the decision-making process**
* The process takes place at all levels of an organization. For example, transaction-processing systems, based on operational databases, are tailored to serve the information needs of people who deal with **short-term inventory, accounts, payable, and purchasing. Middle-level managers, general managers, vice presidents, and presidents focus on strategic and tactical decision making.** Those managers required summarized information designed to help them make decisions in a complex business environment.
* Company and software vendors addressed these multilevel decision support needs by creating autonomous applications for **particular groups of users, such as those in finance, customer management, human resources, and product support**. Applications were also tailored to different industries such as education, retail, health care, and finance. This approach worked well for some time, but changes in the business world, such as globalization, expanding markets, mergers, and acquisitions, increased regulation, and new technologies, called for **new ways of integrating and managing decision support across levels, sectors, and geographic locations. This more comprehensive and integrated decision support framework within organizations became known as business intelligence.**

## 13-2 Business Intelligence
* Business intelligence is a term that describes a comprehensive, cohensive, and integegrated set of tools and processes used to capture, collect, integrate, store, and analyze data with the purpose of generating and presenting information to support business decision making. This intelligence is based on learning and understanding the facts about the business environment. **BI is a framework that allows a business to transform data into information, information into knowledge, and knowledge into wisdom. BI has the potential to positively affect a company's culture by creating continuous business performance improvement through active decision support at all levels in an organization. This business insight empowers users to make sound decisions based on the accumulated knowledge of the business.
* BI's initial adopters were **high-volume industries such as financial services, insurance, and healthcare companies.** As BI technology evolved, its usage spread to other industries such as telecommunications, retail/merchandising, manufacturing, media, government, and even education. Table 13.1 lists some companies that have implemented BI tools and shows how the tools benefited the companies. 

        TABLE 13.1: SOLVING BUSINESS PROBLEMS AND ADDING VALUE WITH BI TOOLS
        
        Company: Cici's Enterprises Eight-largest pizza chain in the United States; operates 650 pizza restaurantsin 30 states; 
        Problem: Information access was cumbersome and time-consuming; needed to increase accuracy in the creation of marketing budgets; needed an easy, reliable, and efficient way to access daily data
        Benefit: provided accurate, timely budgets in less time; provided analysts with access to data for decision-making purposes; received in-depth view of product performance by store to reduce waste and increase profits

        Company: NASDAQ, Largest U.S electronic stock market trading organization
        Problem: Inability to provide real-time, ad hoc query and standard reporting for executives, business analysts, and other users; excessive storage costs for many terabytes of data
        Benefit: reduced storage costs by moving to a multitier storage solution; implemented new data warehouse center with support for ad hoc query and reporting, and near real-time data access for end users

        Company: Pfizer Global pharmaceutical company
        Problem: needed a way to control costs and adjsut to tougher market conditions, international commpetition, and increasing government regulation; needed better analytical capabilities and flexible decision-making framework
        Benefit: Ability to get and integrate financial data from multiple sources in a reliable way; streamlined, standards-based financial analysis to improve forecasting process; faster and smarter decision making for business strategy formulation

        Company: Swisscom; Switzerland's leading telecommunications provider
        Problem: needed a tool to help employees monitor service-level compliance; had a time-consuming process to generate performance reports; needed a way to integrate data from 200 different systems
        Benefit: Ability to monitor performance using dashboard technology; quick and easy access to real-time performance data; managers have closer and better control over costs

* **Implementing BI in an organization involves capturing not only internal and external business data, but also the metadata, or knowledge about the data. In practice, BI is a complex proposition that requires a deep understanding and alignment of the business process, business data, and informaiton needs of users at all levels in an organization**.
* **BI is not a product by itself, but a framework of concepts, practices, tools, and technologies that help a business better understand its core capabilities, provide snapshots of the company situation, and identify key opportunities to create competitive advantage.** In general, BI provides a framework for

        * Collect and storing operational data
        * Aggregating the operational data into decision support data
        * Analyze decision support data to generate information
        * Presenting such information to the end user to support business decisions
        * Making business decisions, which in turn generate more data that is collected stored, and so on (restarting the process)
        * Monitoring results to evaluate outcomes of the business decisions, which again provides more data to be collected, stored, and so on
        * Predicting future behaviour and outcomes with a high degree of accuracy

* The preceding points represent a system-wide view of the flow of data, processes, and outcommes within the BI framework. **In practice, the first point, collecting, and storing operational data, does not fall into the realm of a BI system per se; rather, it is the function of an operational system. However, the Bi system will use the operational data as input material from which information will be derived. The rest of the processes and outcomes explained in the preceding points are oriented toward generating knowledge, and they are the focus of the BI system.** In the following section, you will learn about the basic BI architecture.

## 13-2a Business Intelligence Architecture
* BI covers **a range of technologies and applications to manage the entire data life cycle from acquisition to storage, transformation, integration, presentation, analysis, monitoring, and archiving.** BI **functionality ranges from simple data gathering and transformation to very complex data analysis and presentation. BI architecture ranges from highly integrated single-vendor systems to loosely integrated, multivendor environments.** However, some common functions are expected in most BI implementations.


        Business intelligence Framework includes:
        - External data
        - Operational data
        - Data visualization
        - Monitoring and alerting
        - Data analytics
        - Query and reporting
        - Data store: data warehouse and data mart
        - Extraction, transformation, and loading
        - people, processes, management, governance

* The general Bi framework depicted in Figure above has six basic commponents that encompass the functionality required on most current generation BI systems. The components are briefly described in Table 13.2

        TABLE 13.2: BASIC BI ARCHITECTURAL COMPONENTS
        - ETL tools: Data extraction, transformation, and loading (ETL) tools collect, filter, integrate, and aggregate internal and external data to be saved into a data store optimized for decision support
        - Data store: The data store is optimized for decision support and is generally represented by a data warehouse or a data mart. The data is stored in structures that are optimized for data analysis and query speed
        - Query and reporting: This component performs data selection and retrieval, and it is used by the data analyst to create queries and access the database and create the required reports
        - Data visualization: this component presents data to the end user in a variety of meaningful and innovative ways. This tool helps the end user select the most appropriate presentation format, such as summary reports, maps, pie or bar graphs, mixed graphs, and static or interactive dashboards.
        - Data monitoring and alerting: This component allows real-time monitoring of business activities. The BI system will present concise information in a single integrated view. This integrated view could include specific metrics about the system performance or activities, such as number of orders placed in the last four hours, number of customer complaints by product by month, and total revenue by region. Alerts can be placed on a given metric; once the value of a metric goes below or above a certain baseline, the system will perform a given action, such as emailing shop floor managers, presenting visual alerts, or starting an application
        Data analytics: This component performs data analysis and data-mining tasks using the data in the data store. This tool advises the user as to which data analysis tool to select and how to build a reliable business data model. Business models are generated by special algorithm that identify and enhance the understanding of business situation and problems.

* Each BI component showsn in Table 13.2 has generated a fast-growing market for specialized tools. Thanks to technological advancements, the components can interact with other componnets to form a truly open architecture. As a matter of fact, you can integrate multiple tools from different vendors into a single BI framework. Table 13.3 shows a sample of common BI tools and vendors 

        TABLE 13.3: SAMPLE OF BUSINESS INTELLIGENCE TOOLS
        
        Tool: Dashboards and business activity monitoring
        Description: Dashboards use web-based technologies to present key business performance indicators or information in a single integrated view, generally using graphics that are clear, concise, and easy to understand
        Sample Vendor: Salesforce, IBM/Cognos, BusinessObjects, Information Builders, iDashboard, Tableau

        Tool: Portals
        Description: Portals provide a unified, single point of entry for informaiton distribution. Portals are a web-based technology that use a web browser to integrate data from multiple sources into a single webpage. Many different types of BI functionality can be accessed through a portal
        Sample vendors: Oracle Portal, Actuate, Microsoft, SAP

        Tool: Data analysis and reproting tools
        Description: These advanced tools are used to query multiple and diverse data sources to create integrated reports
        Sample vendors: microsoft reporting services, microstrategy, SAS WebReportStudio

        Tool: Data-mining tools
        Description: These tools provide advanced statistical analysis to uncover problems and opportunities hidden within busienss data
        Sample vendors: SAP, Teradata, MicroStrategy, MS Analytics Services

        Tool: Data warehouses
        Description: The data warehouse is the foundation of BI infrastructure. Data is captured from the production system and placed in the DW on a near real-time basis. BI provides company-wide integration of data and the capability to respond to business issues in a timely manner
        Sample vendors: Microsoft, Oracle, IBM/Cognos, Teradata

        Tool: OLAP tools: 
        Description: Online analytical processing provides multidimensional data analysis
        Sample vendors: IBM/Cognos, BusinessObjects, Oracle, Microsoft

        Tool: Data visualization
        Description: These tools provide advanced visual analysis and techniques to enhance understanding and create additional insight of business data and its true meaning
        Sample vendors: Dundas, Tableau, QlikView, Actuate, Microsoft powerBI

* As depicted in Figure 13.1, BI integrates people and processes using technology at all levels of the organization. **A sound BI strategy adds value to an organization by providing the right data, in the right format,  to the right people, at the right time. Such value is derived from how end users apply such information in their daily activities, and particularly in their daily business decision making.**
* The focus of traditional information systems was on operational automation and reporting; in contrast, BI tools focus on the strategic and tactical use of information. To achieve this goal, BI recognizes that technology alone is not enough. Therefore, BI uses an arrangement of best management practices to manage data as a corporate asset. One of the most recent developments in this area is the use of master data management techniques. **Master data management(MDM) is a collection of concepts, techniques, and processes for the proper identification, definition, and management of data elements within an organization. MDM's main goal is to provide a comprehensive and consistent definition of all data within an organization. MDM ensures that all company resources (people, procedures, and IT systems) that work with data have uniform and consistent views of the company's data.
* An added benefit of this meticulous approach to data management and decision making is that it provides a framework for business governance. **Governance is a method of process of government. In this case, BI provides a method for controlling and monitoring business health and for consistent decision making. Furthermore, having such governance creates accountability for business decisions. In the present age of business flux, accountability is increasingly important. Had governance been as pivotal to business operations a few years back, crises precipitated by Enron, WorldCom, Arthur Andersen, and the 2008 financial meltdown might have been avoided.
* Monitoring a business's health is crucial to understand where the company is and where it is headed. To do this, BI makes extensive use of a special type of metrics known as key performance indicators. **key performance indicators (KPI)** are quantifiable numeric of scale-based measurements that assess the company's effectiveness or success in reaching its strategic and operational goals. Many different KPIs are used by different industries. Some examples of KPIs are:

        * General. Year-to-year measurements of profit by line of business, same-store sales, product turnovers, product recalls, sales by promotion, and sales by employee
        * Finance. Earning per share, profit margin, revenue per employee, percentage of sales to account receivables, and assets to sales
        * human resources. Applicants to job openings, employee turnoer, and employee longevity
        * Education. Graduation rates, number of incoming freshmen, student retentionrates, publication rates, and teaching evaluation scores

* KPIs are determined after the main strategic, tactical, and operaitonal goals are defined for a business. To tie the KPI to the strategic master plan of an organization, a KPI is compared to a desired goal within a specific time frame. For example, if you are in an academic environment, you might be interested in ways to measure student satisfaction or retention. In this case, a sample goal would be to increase the final exame grades of graudating high school seniors by Fall 2021. Another sample KPI would be to increase the returning student rate from freshman year to sophomore year from 60 percent to 75 percent by 2021. In this case, such performance indicators would be measured and monitored on a year-to-year basis, and plans to achieve such goals would be set in place.
* Although Bi has an unquestionably important role in modern business operations, the manager must initiate the decision support process by asking the appropriate questions. The BI environment exists to support the manager; it does not replace the management function. If the manager fails to ask the appropriate questions, problems will not be identified and solved, and opportunities will be missed. In spite of the very powerful BI presence, the human component is still at the center of busienss technology.
* having a well-implemented Bi environment (people, processes, technology, management, and governance) positions a company to react quickly to changes in the environment. Today's customers are more connected than ever with other customers (current or potential), companies, and organization. In certain industries, social media plays a key role in marketing, brand recognition, and development. A simple tweet could generate millions of dollars in new sales or could cost a company millions of dollars in revenue. Companies monitor social media data to identify trends and quickly react to current or future threats or opportunities.
* The main BI architectural components were illustrated in Figure 13.1 and further explained in Table 13.2 and 13.3. However, the heart of BI system is its advanced information generation and decision support capabilities. A BI system's advanced decision support functions come to life via its intuitive and informational user interface, and particularly its reporting capabilities. A modern BI system provides three distinctive reporting styles:

        * Advance reporting. A BI system presents insightful information about the organizaiton in a variety of presentation formats. Furthermore, the reports provide interactive features that allow the ned user to study the data from multiple point of view--from highly summarized to very detailed data. The report present key actionable information used to support decision making
        * Monitoring and alerting. After a decision has been made, the BI system offers ways to monitor the decision's outcome. The BI system provides the end user with ways to define metrics and other key performance indicators to evalute different aspects of an organization. In addition, exceptions and alerts can be set to warn managers promptly about deviations or problem areas.
        * Advance data analytics. A BI system provides tools to help the end suer discover relationships, patterns, and t rends hidden within the organization data. These tools are used to create two types of data analysis: explanatory and predictive. Explanatory analysis provides ways to discover relationships, trends, and patterns among data, while predictive analysis provides the end user with ways to create models that predict future outcomes.

* Understanding the architectural components of a BI framework is the first step in properly implementing Bi in an organization. A good BI infrastructure promises many benefits to an organization, as outlined in the next section.

## 13-2b Business Intelligence Benefits.
* As you have learned in previous sections, a properly implemented Bi architecture could provide a framework for continous performance improvements and business decision making. Improved decision making is the main goal of BI, but BI provides other benefits:

        * Integrating architecture. Like any other IT project, BI has the potential of becoming the integrating umbrella for a disparate mix of IT system within an organization. This architecture could support all types of company-generated data from operational to executive, as well as diverse hardware such as mainframes, servers, desktops, laptops, and mobile devices.
        * Common user interface for data reporting and analysis. BI front ends can provide up-to-the-minute consolidated information using a common interface for all company users. IT departments no longer have to provide multiple training options for diverse interfaces. End users benefit from similar or common interfaces in different devices that use multiple clever and insightful presentation formats.
        * Common data repository foster single version of company data. In the past, multiple IT systems supported different aspects of an organization's operaitons. Such systems collected and stored data in separate data stores. Keeping the data synchorized and up to date has always been diffcult. BI provides a framework to integrate such data under a common environment and present a single version of the data.
        * Improved organizational performance. BI can provide commpetitive advantages in many different areas, from customer support to manufacturing processes. Such advantages can be reflected in added efficiency, reduced waste, increased sales, reduced employee and customer turnover, and most importantly, an increased bottom line for the business.

* Achieving all these benefits takes a lot of human, financial, and technological resources, not to mention time. BI benefits are not achieved overnight, but are the result of a focused commpany-wdie effort that could take a long time. As a matter of fact, as you will learn in the next section, the BI field has evolved over a long period of time itself..

## 13-2c Business Intelligence Evolution
* Providing useful information to end users has been a priority of IT system since mainframe computing became an integral part of corporations. Business decision support has evolved over many decades. Following computer technology advances, business intelligence started with centralized reporting systems and evolved into today's highly integrated BI environments. Table 13.4 summarized the evolution of BI systems.
* Using Table 13.4 as a guide, you can trace business intelligence from the mainframe environment to t he desktop and then to the more current, cloud-based, mobile Bi environment (Chapter 15, Database Connectivity and Web Technologies, provides a detailed discussion of cloud-based systems)
* The precursor of the modern BI environment was the first-generation decision support system. **A decision support system (DSS)** is an arrangement of computerized tools used to assist managerial decision making. A DSS typically has a much narrower focus and reach than a BI solution. At first, decision support systems were the realm of a few selected managers in an organization. Over time, and with the introduction of the desktop computer, decision support system migrated to more agile platforms, such as midrange computers, high-end servers, commodity servers, appliances, and cloud-based offerings. This evolution effectively changed the reach of decision support systems; BI is no longer limited to a small group of top-level managers with training in statistical modeling. Instead, BI is now available to all users in an organization, from line managers to the shop floor to mobile agents in the field.
* You can also use Table 13.4 to track the evolution fo information dissenmination styles used in business intelligence

        * Starting in the late 1970s, the need for information distribution was filled by centralized reports running on mainframes, minicomputers, or central server environments. Such reports were predefined and took considerable time to process.
        * With the introduction of desktop computers in the 1980s, a new style of information distribution, the spreadsheet, emerged as teh moniant format for decision support systems. In this environment, managers downloaded information from centralized data stores and manipulated the data in desktop spreadsheet.
        * As the user of spreadsheet multiplied, IT departments tried to managed the flow of data in a more formal way using enterprise reporting systems. These systems were developed in the early 1990s and basically integrated all data into an IT umbrella that started with the first-generation DSS. The systems still used spreadsheet-like features with which end users were familiar
        * Once DSS were established, the evolution of business intelligence flourished with teh introductrion of the data warehouse and online analytical processing systems (OLAPs) in the mid-1990s.
        * Rapid changes in information technology and the Internet reolution led to the introduction fo advanced BI systems such as web-based dashboards in the early and mid 2000s and mobile BI later in the decade. With mobile BI, end users access BI reports via native applications that run on a mobile device, such as a smartphone or tablet.
        * more recently, the social media revolution has generated large amounts of data. At the same time sensor-generated data is being collected and stored. Commpanies are using Big Data analytics and data visualization to leverage such data and obtain critical information otherwise unavailable to them.

* Mobile BI technology is poised to have a significant impact on the way BI information is disseminated and processed. If the number of students using smartphones to communicate with friends, update their Facebook status, and send tweets on Twitter is any indicator, you can expect the next generation of consumers and workers to be highly mobile. Leading corporations are therefore starting to push decision making to agents in the field to facilitate customer relationships, sales and ordering, and product support. Such mobile technologies are so portable and interactive that some users call them "disruptive" technologies.
* BI informaiton technology has evolved from centralized reporting styles to the current, mobile BI and Big Data anayltics style in the span of jsut a few years. The rate of technological change is not slowing down; to the contrary, technology advancements are acclerating the adoption of BI to new levels. The next section illustrates some BI technology trends.

# 13-2d Business Intelligence Technology Trends
* several technological advances are driving the growth of business intelligence technologies. These advances create new generations of more affordable products and services taht are faster and easier to use. In turn, such products and services open new markets and work as driving forces in the increasing adoption of business intelligence techologies within organizations. Some of the more remarkable technological trends are:

        * Data storage improvement. newer data storage technologies, such as solid state drives (SSD) and Serial Advanced Technology Attachment (SATA) drives, offer increased performance and larger capacity that make data storage faster and more affordable. Currently you can buy single drives with a capacity approaching 10 terabytes.
        * Business intelligence appliances. Vendors now offer plug-and-play appliances optimized for data warehouse and BI applications. These new appliances offer improved price-performance ratios, simplified administration, rapid installation, scalability, and fast integration. Some of these vendors include IBM, Netezza, EMC Greenplum, and Teradata Aster.
        * Business intelligence as a service. Vendors now offer data warehouses and BI as a service. These cloud-based services allow any corporation to rapidly develop a data warehouse store without the need for hardware, software, or extra personnel. These prepackaged services offer "pay-as-you-go" models for specific industries and capacities, and they provide an opportunity for organizations to pilot-test a BI project without incurring large time or cost commitments. For example, such services are offered by IBM, Oracle, Microsoft, Teradata, MicroStrategy, and SAP.
        * Big Data analytics. The Big Data phenomen is creating a new market for data analytics. Organizations are turning to social media as the new source for information and knowledge to gain competitive advantages.
        * Personal analytics. OLAP brought data analytics to the desktop of every end user in an organization. Mobile BI is extending business decision making outside the walls of the organization. BI can now be deployed to mobile users who are closer to customers. The main requirement is for the BI end user to have a key understanding of the business. Somem personal analytics vendors include MicroStrategy, QlikView, and Tableau. There is a growing trend toward self-sevice, personalized data analytics. it is not so far-feteched to imagine that in a few years, end users will have smart data analytics agents on their smartphones tailored to their personal interests. Such personal agents will provide users with up-to-the-minute "intelligent knowledge" about their personal interests.

* One constant in this relentless technological evolution is the need for better decision support data and the importance of understanding the difference between decision support data and operational data.

## 13-3 Decision Support Data
* Althoug BI is used at the strategic and tactical managerial levels within organizations, its effectiveness depends on the quality of data gathered at the operational level. Yet, operational data is seldom well suited to decision support tasks. The differences between operational data and decision support data are examined in the next section.

### 13-3a Operational Data versus Decision Support Data
* Operational data and decision data serve different purposes.Therefore, itis not surprisinng to learn that their formats and structures differ. Most operaitonal data is stored in a relational database in which the structures (tables) tend to be highly normalized. Operational data storage is optimized to support transactions that represent daily operations. For example, each time an item is sold, it must be accounted for. Customer data, inventory data, and other similar data need frequent updating. To provide effective update performance, operational systems store data inn many tables, each with a minimum number of fields. Thus, a simple sales transaction might be represented by five or more different tables, such as INVOICE, INVOICE LINE, DISCOUNT, STORE, and DEPARTMENT. Although such as arrangement is excellent in an operational database, it is not efficient for query processing. For example, to extract a simple invoice, you would have to join several tables. Whereas operational data is useful for capturing daily business transactions, decision support data gives tactical and strategic business meaning to the operational data. From the data analyst's point of view, decision suppport data differs from operational data in three main areas: time span, granularity, and dimensionality.

        * Time span. Operational data covers a short time frame. In contrast, decision suppport data tends to cover a longer time frame. Managers are seldom interested in a specific sales invoice to Customer X; rather, they tend to focus on sales generated during the last month, the last year, or the last five years.
        * Granularity (level of aggregation). Decision support data must be presented at different level of aggregation, from highly summarized to nearly atomic. For example, if managers analyze regional sales, they must be able to access data showing the sales by region, by city with the region, by store within the city within the region, and so on. In that case, summarized data to compare the regions is required, along with data in a structure that enables a manager to drill down, or decompose, the data into more atomic components--that is, finer-grained data at lower levels of aggregation. In contrast, when you roll up the data, you are aggregating the data to a higher level.
        * Dimensionality. Operational data focuses on representing individual transactions rather than the effects of the transaciotns over time. In contrast, data analysts tend to include many data dimensions and are interested in how teh data relates over those dimensions. For example, an analyst might want to know how productX fare relative to Product Z during the past six months by region, state, city, store, and customer. In that case, both place and time are part of the picture.

* Figure 13.3 shows how decision support data can be examined from multiple dimensions such as product, region, and year, using a variety of filters to produce each dimension. The ability to analyze, extract, and present information in meaningful ways is one of the differences bewteen decision support data and transaction-at-a-time operational data. SKIP FIGURE 13.3

* From the designer's point of view, the differences between operational and decision support data are as follows:

        * Operational data represents transactions as they happen in real time. Decision support data is a snapshot of the operatinoal data at a given point in time. Therefore, decision support data is historic, representing a time slice of the operational data.
        * Operational and decision support data are different in terms of transaction type and transaction volume. Whereas operational data is characterized by update transactions, decision support data is mainly characterized by read-only transactions. Decision support data also requires periodic updates to load new data that is summarized from the operatinoal data. Finally, the concurrent transaction volume in operaitonal data tends to be very high compared with the low to medium levels in decision support data.
        * Operational data is commonly stored in many tables, and the stored data represents information about a given transaction only. Decision support data is generally stored in a few tables derived from the operational data. The decision support data does not include the details of each operational transaction. Instead. decision support data represents transaction summaries; therefore, the decision support database stores data that is integrated, aggregated, and summarized for decision support purposes.
        * The degree to which decision support data is summiarized is very high when contrasted with operational data. Therefore, you will see a great deal of derived data in decision support databases. For example, rather than storing 10,000 sales transactions for a given store on a given day, the decision support database might simply store the total number of units sold and the total sales dollars generated during that day. Decision support data might be collected to monitor such aggregates as total sales for each store or for each product. The purpose of the summaries is simple: they are used to establish and evaluate sales trends and product sales comparisons and to provide other data that serves decision needs (how well are items selling? Should this product be discontinued? Has teh advertising been effective as measured by increased sales)
        * The data models that govern operational data and decision support data are different. The operationl database's frequent and rapid data updates make data anomalies a potential devastating problem. Therefore, the data in a relational transaction (operational) system generally requires normalized structures that yield many tables, support database is not subject to such transaction updates, and the focus is on querying capacity. Therefore, decision support databases tend to be non-normalized and include few tables, each of which contains a large number of attributes.
        * The frequency and complexity of query activity in the operational database tends to be low to allow additional processing cycles for the more crucial update transactions. Therefore, queries against operational data typically are narrow in scope and low in commplexity, and high speed is critical. In contrast, decision support data exist for the sole purpose of serviing query requirements. Queries against decision support data typically are broad in scope and high in compliexity, and less speed is needed.
        * Finally, decisions support data is characterized by very large amounts of data. The large data volume is the result of two factors. First, data is stored in non-normalized strcutures taht are likely to display many data redundancies and duplications. Second, the same data can be categorized in many different ways to represent different snapshots. For example, sales data might be stored in relation to product, store, customer, region, and manager.

### 13-3b Decision Support Database Requirements
* A decision support database is a specialized DBMS tailored to provide fast answers to complex queries. There are three main requirements for a decision support database: the database schema, data extraction, and filtering, and database size.
* **DATABASE SCHEDMA** The decisions support database schema must support complex (non-normalized) data representations. As noted earlier, the decision support database requirements, the queries must be able to extract multidimensional time slices. If you are using an RDBMS, the conditions suggest using non-normalized and even duplicated data. To see why this must be true, take a look at the 10-year sales history for a single store containing a single department. At this point, the data is fully normalized within the single table.
* This structure works well when you have only one store with only one department. However, it is very unlikely that such a simple environment has much need for a decision support database. A decision support database becomes a factor when you are dealing with more than one store, each of which has more than one department. To support all of the decision support requirements, the database must contain data for all of the dimensional queries that track sales by stores, by departments, and over time. For simplicity, suppose that there are only two stores (A and B) and two departments (1 and 2) within each store. Also, change the time dimension to inlcude yearly data. 
* Now, suppose that the company has 10 department per store and 20 stores nationwide, and suppose that you want to access yearly sales summaries. Now you are dealing with 200 rows and 12 monthly sales attributes per row.
* The decision support database schema must also be optimized for query (read-only) retrieval. To optimize query speed, the DBMS must support features such as bitmap indexes and data partitioning. In addition, the DBMS query optimizer must be enhanced to support the non-normalized and complex structures in decision support databases.
* **DATA EXTRACTION AND FILTERING** The decision support database is created largely by extracting data from the operational database and by importing additional data from external sources. Thus, the DBMS must support advanced data extraction and data-filtering tools. To minimizing the impact on the operational database, the data extraction capabilities should allow batch and scheduled data extraction, and should support different data sources: flat files and hierarchical, network, and relational databases, as well as multiple vendors. Data filtering capabilities must include the ability to check for inconsistent data or data validation rules. Finally, to filter and integrate the operational data into the decision support database, the DBMS must support advanced data integration, aggregation, and classification.
* using data from multiple external sources also usually means having to solve data-formating conflicts. For example, data such as Social Security numbers and dates can occur in different formats; measurements can be based on different scales, and the same data elements can have different names. In short, data must be filtered and purified to ensure that only the pertinent decision support data is stored in the database and that it is stored in a standard format.
* **DATABASE SIZE** Decision support databases tend to be very large; gigabyte and terabyte range are not unusual. For example, Wlamart has more than 4 pertabytes of data in its data warehouses. Therefore, the DBMS must be capable of supporting very large databases (VLDBs). To support a VLDB adequately, the DBMS might be required to support advanced storage technologies, and even more importantly, to support multiple-processor technologies, such as a symmetric multiprocessor (SMP) or a massively parallel processor (MPP)
* The complex information requirements and the ever-growing demand for sophisticated data analysis sparked the creation of a new type of data repository. This repository, called a data warehouse, contains data in formats that faciliate data extraction, data analysis, and decision making. It has become the foundation for a new generation of decision support systems.

### 13-4 The Data Warehouse

### 13-6 Online Analytical Processing
* Online analytical processing (OLAP) is a BI style whose systems share three main characteristics:

                * Multidimensional data analysis techniques
                * Advanced database support
                * Easy-to-use end-user interfaces
                

##### 13-6a Multidimensional Data Analysis Techniques
* The most distinctive characteristic of modern OLAP tools in their capacity for multidimensional analysis, in which data is processed and viewed as part of a multidimensional structure. This type of data analysis is particularly attractive to business decision makers because they tend to view business data as being related to other business data

##### 13-6e Relational OLAP
* Relational online analytical processing (ROLAP) provides OLAP functionality by using relational databases and familiar relational query tools to store and analyze multidimensional data. This approach builds on existing relational technologies and represents a natural extension to companies that already use relational database management systems within their organizations. ROLAP adds the following extensions to traditional RDBMS technology:

                * Multidimensional data schema support within the RDBMS
                * Data access language and query performance optimized for multidimensional data
                * Support for very large databases (VLDBs)

##### 13-6f Multidimensional OLAP
* **Multidimensional online analytical processing (MOLAP)** extends OLAP functionality to **multidimensional database management systems (MDBMSs)**. An MDBMS uses proprietary techniques to store data in matrix-like n-dimensional arrays. MOLAP's premise is that multidimensional database are best suited to manage, store, and analyze multidimensional data. Most of the proprietary techniques used in MDBMSs are derived from engineering fields such as computer-aided design/computer-aided manufacturing and geographic information system. MOLAP tools store data using multidimensional arrays, row stores, or column stores

# Chapter 14: Big Data and NoSQL
* Big Data is an ill-defined term that describes a new wave of data storage and manipulation possiblities and requirements. Organizations' efforts to store, manipulate, and analyze this new wave of data represent one of the most urgent emerging trends in the database field. The challenges of dealing with the wave of Big Data have led to the development of NoSQL databases that reject many of the underlying assumptions of the relational model
* Big Data generally refers to a set of data that displays the characteristics of volume, velocity, and variety (the 3 Vs) to an extend that makes the data unsuitable for management by a relational database management system. These characteristics can be defined as follow:

                * Volume - the quantity of data to be stored
                * Velocity - the speed at which data is entering the system
                * Variety - the variations in the structure of the data to be stored

* The key is that the characteristics are present to an extent that the current relational database technology struggles with managing the data.

## 14-2 Hadoop
* Big Data requires a different approach to distributed data storage that is designed for large-scale clusters. Although other implementation technologies are possible. Hadoop has become the de facto standard for most Big Data storage and processing. Hadoop is not a database. Hadoop is a Java-based framework for distributing and processing very large data sets across clusters and computers. While the Hadoop framework includes many parts, the two most important components are the Hadoop Distributed File System (HDFS) and MapReduce. HDFS is a low-level distributed file processing system, which means that it can be used directly for data storage. MapReduce is a programming model that supports processing large data sets in highly parallel, distributed manner. While it is possible to use HDFS and MapReduce separately, the two technologies complement each other so that they work better together as a Hadoop system. Hadoop was engineered specifically to distribute and process enormous amounts of data across vast clusters of servers.
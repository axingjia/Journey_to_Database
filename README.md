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
        * Map conceptual model t o logical model components-> Activity: Define tables, columns, relationships, and constraints

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
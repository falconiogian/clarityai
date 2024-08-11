Summarized Recommendation
========

For this architecture we could apply a microservices architecture to have scalability, maintainability and flexibility. We could consider as the main key components: Data Ingestion Services, Data Processing and Normalization Services, C-Rating Calculation Service, Data Storage Services, API Gateway, Web Application, Message Queue, Caching Layer, and Monitoring and Logging Services. 


Partner Management Services will make it possible to deal with the acquisition of data from the partner platforms. This component comprises of a REST API Connector for real time data acquisition, a File Ingestion Service for processing intermittent feeds, and an FTP Client for file transfer with added security being SFTP. These services are coordinated through a Data Ingestion Orchestrator which handles data versioning and the reinforcement of fault tolerance mechanisms such as the Circuit breaker pattern. 

Normalization and Data Processing Services are available for processing and transforming raw data. The Data Cleaning Service deals with issues of redundancy and missing data and The Data Normalization Service scales ratings. A Genre Mapping Service stores a set master genre taxonomy, and then uses machine learning for genre selection. The Title Reconciliation Service applies matching algorithms to find the movie’s names that are similar or referring to the same movie between different sources. 

The C-Rating Calculation Service is the main part of the offer, which produces the distinguished C-Rating. It also works with a customizable weighting model for partner platforms, establishes the mapping of partner-specific categories to the C-Movie’s unified several categories and apply statistical techniques to sum up the ratings with between-partner outliers and biases elimination. A Calculation Scheduler monitors the need to recalculate values due to new data, or a specified time interval, while it performs incremental update.

Data Storage Services utilize a combination of specialized databases to manage the platform’s data. A document-based NoSQL database is used to store movie metadata, while a time-series database is used to handle historical rating data; the C-Rating information is stored in a key-value store at present. Several of these storage systems use a uniform Data Access Layer that supplies generic data access interfaces. 

It connects to the API Gateway which is the single interface of ROS through which all clients’ request access is regulated in terms of routing, authentication, and rate limiting. It implements OAuth 2. Supports authentication for a secure access with the status of 0, uses JSON Web Tokens for the stateless authentication, and supports response caching for frequently requested data. The gateway is also used for managing the versioning of APIs so that one version does not break another version. 

The Web Application comes with a client-side web interface created using a rubust JavaScript framework, and a small backend web server. It has built-in modules for SEO-supportive server-side rendering and initial loading, and server-side caching for a better response rate. 

The Caching Layer complements by overriding the database requests and responses. It provides several caching mechanisms where cache-aside mechanism is used for readings and write-through mechanisms are used for writing to optimize between data timeliness and system performance.

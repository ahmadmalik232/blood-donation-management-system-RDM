1.	Description of Entities, Attributes, and Relationship
Entities and Attributes:
I.	Donor:
•	Primary key: Donor-id
•	Attributes: name, age, blood type, contact-number, address, last-donation-date.
II.	Donation:
•	Primary key: Donation-id
•	Attributes: Donor-id, date-of-donation, blood-quantity, blood-type, donation-center.
III.	Blood-inventory:
•	Primary key: Inventory-id
•	Attributes: blood-type, quantity-available, expiry-date, storage-location, donation-id.
IV.	Recipient:
•	Primary key: Recipient-id
•	Attributes: name, age, blood-type-needed, hospital-id, contact-number, request-date.
V.	Hospital:
•	Primary key: Hospital-id
•	Attributes: hospital-name, location, contact-number, blood-bank-affiliation, emergency-level.
VI.	Blood-request:
•	Primary key: Request-id
•	Attributes: Recipient-id, blood-type-requested, quantity-requested, fulfilment-status, request-date.
Relationships:
I.	Donor-Donation:
Relationship: A donor can make multiple donations, but each donation is linked to one donor.
Degree: Binary
Cardinality: one-to-many
II.	Donation-Blood inventory:
Relationship: Each donation updates the blood inventory; one inventory record contain record of one or more donations.
Degree: Binary
Cardinality: one-to-many
III.	Recipient-Blood request:
Relationship: A recipient can make multiple blood request and each request has separate recipient
Degree: Binary
Cardinality: one-to-many
IV.	Blood inventory –Hospital:
Relationship: A hospital has access to more than one blood inventory and each inventory record can be accessed by more than one hospital if needed.
Degree: Binary
Cardinality: many-to-many
V.	Hospital-Recipient:
Relationship: A hospital can serve multiple recipients and each recipient is associated with one hospital.
Degree: Binary
Cardinality: one-to-many
VI.	Blood request -Blood inventory:
Relationship: Each blood request form access more than one inventory record and each inventory satisfy multiple blood request.
Degree: Binary
Cardinality: many-to-many
2.	Challenges and Considerations
•	Normalization:
No data redundancy while being high on performance and scalable
•	Data Integrity:
Keeping tables in sync when updating donations and inventories.
•	Scalability:
Creating a flexible design that allows for the addition of other attributes (e.g., donor medical history)
•	Real-World Complexity: 
This is considering edge cases where a donations is divided for multiple uses or hospitals share the same inventory.
•	Constraints:
Implementing business rules such as matching blood-types for requests & donation
3.	Tables, Fields, and Data Types
Table Name	Fields	Data Types
Donor	Donor ID (PK)	INT
	Name	VARCHAR(100)
	Contact number	VARCHAR(150)
	Blood Type	CHAR(3)
	Age	INT
	Address	INT
	Last-donation date	DATE

Table Name	Fields	Data Types
Donation	Donation ID (PK)	INT
	Donor ID (FK)	INT
	Date of donation	DATE
	Blood Type	CHAR(3)
	 Blood Quantity	DECIMAL(5,2)
	Donation center	INT

Table Name	Fields	Data Types
Blood Inventory	Inventory ID (PK)	INT
	Quantity available	INT
	Blood Type	CHAR(3)
	Expiry date	DATE
	Storage location	INT
	Donation id	INT

Table Name	Fields	Data Types
Recipient	Recipient ID (PK)	INT
	Name	VARCHAR(100)
	Contact number	VARCHAR(150)
	Blood Type needed	CHAR(3)
	Age	INT
	Hospital id	INT
	Request date	DATE




Table Name	Fields	Data Types
Hospital	Hospital ID (PK)	INT
	 Hospital Name	VARCHAR(100)
	Location	VARCHAR(150)
	Contact number	INT
	Blood bank affliation	INT
	Emergency level	INT

Table Name	Fields	Data Types
Blood Request	Request ID (PK)	INT
	Fulfilment status	INT
	Recipient ID (FK)	INT
	Blood Type	CHAR(3)
	Quantity	DECIMAL(5,2)
	Date	DATE

4.	Establishing Relationships
•	Donor-donation (Donor-id PK in donor and FK in donation)
•	Donation-Blood inventory (Donation-id PK in donation and FK in blood inventory)
•	 Recipient id-blood request (Recipient-id PK in recipient and FK in blood-request)
•	 Hospital id –recipient (Hospital-id PK in hospital and FK in recipient)
5.	Transformation of ERD into Relational Data Model (RDM).
 
6.	Report on Design Decisions 
•	Entity Identification: We identified key entities based on the core functionalities of a blood donation management system. The focus was on donors, donations, blood inventories, hospitals, recipients, and requests.
•	Normalization: Tables were designed to eliminate redundancy. For example, blood type data is not duplicated unnecessarily across multiple entities.
•	Relationships and Integrity: Foreign keys were implemented to maintain relationships between entities, ensuring data consistency. For example, DonorID in the Donation table links to the Donor table.
•	Challenges Addressed:
o	Ensured flexibility in blood inventory management by linking donations indirectly through a process.
o	Addressed potential future scalability by allowing for additional attributes or entities without redesigning the schema.
•	Data Types: Data types were chosen to optimize storage and enforce constraints. For instance, CHAR(3) was used for BloodType to represent standardized blood groups (e.g., "A+", "O-").


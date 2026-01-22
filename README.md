# Dairy-Product-Database

Project Overview and Utility
The dairy industry is a critical food production sector requiring high-precision management for manufacturing, preparation, and storage. A modern dairy enterprise must integrate raw materials, production processes, inventory, logistics, and financial operations into a centralized environment. This project provides a robust Enterprise Resource Planning (ERP) solution developed to manage the entire supply chain, including milk intake pooling, multi-step production tracking, and cold-chain logistics.

Technical Foundation
The system architecture is built on PostgreSQL 18.0 for data management and Python (Streamlit) for the user interface. The design demonstrates professional database principles including high normalization, complex constraint enforcement, and data integrity mechanisms suitable for production environments.

Core System Modules
The following table summarizes the thirteen specialized modules that govern the factory operations:
| Module | Purpose and Functionality |
| :--- | :--- |
| **Party Model** | [cite_start]Unified model for persons and organizations that can act as suppliers, customers, or drivers[cite: 71, 29]. |
| **Employee Management** | [cite_start]Tracking of organizational roles, departments, and self-referencing manager hierarchies[cite: 71, 214]. |
| **Supply Chain** | [cite_start]Coordination between raw milk suppliers, external carriers, and the factory vehicle fleet[cite: 71]. |
| **Product Management** | [cite_start]Maintenance of stock codes, categories, storage requirements, and price histories[cite: 71, 452]. |
| **Warehouse Management** | [cite_start]Real-time monitoring of storage zones, specific locations, and environmental logs[cite: 71, 510]. |
| **Machine Management** | [cite_start]Scheduling of maintenance events and assignment of operator responsibilities[cite: 71, 603]. |
| **Milk Intake** | [cite_start]Pooling of raw or pasteurized milk from multiple suppliers with quality metrics like pH and fat ratio[cite: 71, 717]. |
| **Production** | [cite_start]Management of multi-step production orders for main products and byproducts[cite: 71, 865]. |
| **Inventory** | [cite_start]Batch-based tracking using weak entities to support splitting, movement history, and expiry management[cite: 71, 1031]. |
| **Sales** | [cite_start]Processing of sales orders and invoices with automated tax and gross amount calculations[cite: 71, 1085]. |
| **Logistics** | [cite_start]Documentation of shipments, waybills, and driver assignments for cold-chain distribution[cite: 71, 1282]. |
| **Pricing** | [cite_start]Administration of customer-specific contracts and time-sensitive price validity[cite: 71]. |
| **Finance** | [cite_start]Integration of financial records from invoices, payroll, and maintenance with status control[cite: 71, 1374]. |

Advanced Database Engineering
The system utilizes specialized PostgreSQL features to enforce business rules at the database level rather than the application level.

Temporal Data Management and Exclusion Constraints To ensure logical consistency over time, the system implements GiST (Generalized Search Tree) indexes for exclusion constraints. This prevents overlapping intervals in vehicle assignments, product pricing, and batch location history. For instance, a vehicle cannot be assigned to two different carriers during the same time interval.





Automated Triggers and Immutability Complex business rules are enforced through deferred triggers, ensuring every milk intake has a supplier and every production order has at least one step. Immediate triggers automate the computation of invoice line items and header totals. Additionally, financial records marked with a POSTED status are rendered immutable to prevent unauthorized modifications or deletions.





User Interface and Dashboard
The application provides a Streamlit-based interface designed for operational efficiency. An integrated dashboard offers a quick glance at total raw milk inventory, total income/outcome in Turkish Lira, and the status of malfunctioning machinery across facilities. Users can perform standard CRUD (Create, Read, Update, Delete) operations through intuitive menus without manual SQL coding.



Data Disclaimer and Compliance
Due to KVKK data protection constraints, real company data was not utilized. Representative sample data was generated using AI tools to ensure it satisfies all business rules and constraints while maintaining data privacy.



Development Team
This system was developed as a term project for STAT311: Modern Database Systems at Middle East Technical University (METU).


Bartu Batum conceptualized the system and handled overall design and communication. Ozan Durmaz and Tuna Gökyokuş focused on PostgreSQL coding and constraint implementation. Serhan Yavlal and Cihangir Osman Dokucu managed project visualization, ER diagrams, and UI design.

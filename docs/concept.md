# Business Unit Data Migrator - Concept Document

## Overview

**Business-Unit-Data-Migrator** (BU Data Migrator) is a Node.js-based tool that facilitates seamless data migration between business units within the **Dataverse** ecosystem. By leveraging an intuitive configuration system, BU Data Migrator ensures that complex data relationships, including foreign key references and large dataset transfers, are migrated efficiently and accurately. This tool is designed to support enterprises aiming to re-organize, split, or consolidate their business units without facing data consistency issues or significant downtime.

The tool is highly configurable and allows businesses to define the source and destination business units, migrate select tables and fields, handle complex entity relationships, and maintain data integrity throughout the migration process.

## Key Features

1. **Flexible Configuration-Based Migration**:
    - **BU Data Migrator** provides a flexible configuration that lets users specify key migration details, including source and destination business units, tables to migrate, and how foreign keys should be managed.
    - Configurations are simple to define, making the migration process highly customizable and adaptable to specific business needs.

2. **Efficient Data Management**:
    - The tool enables bulk data migration with configurable batch sizes (e.g., 1000 items per batch) to ensure optimal performance and prevent overloading the Dataverse infrastructure.
    - Supports complex relationships between entities, ensuring that data dependencies are respected during the migration.

3. **Foreign Key Mapping and GUID Replacement**:
    - Handles foreign key relationships seamlessly, ensuring the correct linkage of entities between different business units.
    - **GUID replacement** is automated, providing consistent IDs across the source and destination without conflicts, ensuring data integrity is maintained.

4. **Data Validation and Integrity Checks**:
    - The tool performs validation checks during migration, ensuring data conforms to the requirements of the destination business unit.
    - Includes optional patch fields to be handled differently, such as recalculating financial or business-specific data.

5. **Join Table Handling**:
    - Capable of handling **join tables** that define many-to-many relationships, ensuring these complex data structures are correctly migrated and linked.

## Use Cases

1. **Business Unit Restructuring**:
    - When organizations merge or reorganize their business units, the BU Data Migrator ensures all relevant data is moved and linked appropriately, minimizing disruption.

2. **Data Consolidation**:
    - Useful for consolidating multiple smaller business units into a single unit by seamlessly migrating all the associated records.

3. **System Upgrades and Environment Segregation**:
    - Allows for data migration between test, staging, and production environments within the Dataverse, supporting development, testing, and deployment processes.

## Architectural Overview

- **Node.js and JavaScript Configuration**:
    - The BU Data Migrator is built on **Node.js**, providing cross-platform compatibility and ease of scripting.
    - Configuration is managed through JavaScript (`config.js`), allowing for a flexible and programmatic approach to defining migration parameters.

- **Migration Flow**:
    1. **Configuration Loading**: The tool loads configuration details from a JavaScript or `.env` file.
    2. **Entity Selection and Filtering**: Based on the configuration, the tool identifies which entities and fields are to be migrated.
    3. **Data Extraction**: Data is extracted from the **source business unit**.
    4. **GUID Mapping and Data Transformation**: GUIDs are replaced, and foreign key mappings are handled to ensure the data integrity in the new environment.
    5. **Data Loading to Destination**: The data is loaded into the **destination business unit**, with batch handling to ensure the migration is manageable and does not overload the system.

## Configuration Overview

Below is a high-level breakdown of the configuration used in BU Data Migrator:

- **Credentials**:
    - Allows access to the Dataverse environment using authentication credentials.
    - Parameters such as `clientId`, `clientSecret`, `tenantId`, and `baseUrl` are provided for secure connectivity.

- **Source and Destination Business Units**:
    - **`sourceBuId`** and **`destinationBuId`** indicate the respective business units for migration.
    - **`destinationOwnerId`** is also specified to ensure all migrated records are correctly owned in the new unit.

- **Migratable Entities**:
    - Define **`migratables`**, which are data tables/entities that should be migrated.
    - For each entity, the configuration specifies:
        - **`name`**: The table name to be migrated.
        - **`select`**: Fields to be migrated, offering fine-grained control.
        - **`replaceGuids`**: GUIDs that need to be re-generated or mapped in the new environment.
        - **`foreignKeys`**: Defines mappings for foreign keys, ensuring relationships are retained between tables.
        - **`isJoinTable` or `isJoinTableOrg`**: Indicates if the entity represents a join table, which is important for correctly managing many-to-many relationships.

## Configuration Example

```javascript
require('dotenv').config();

module.exports = {
    credentials: {
        baseUrl: process.env.BU_MIGRATION_BASE_URL,
        clientId: process.env.BU_MIGRATION_CLIENT_ID,
        clientSecret: process.env.BU_MIGRATION_CLIENT_SECRET,
        tenantId: process.env.BU_MIGRATION_TENANT_ID
    },
    sourceBuId: process.env.BU_MIGRATION_SOURCE_BU_ID,
    destinationBuId: process.env.BU_MIGRATION_DESTINATION_BU_ID,
    destinationOwnerId: process.env.BU_MIGRATION_DESTINATION_OWNER_ID,
    itemsPerBatch: 1000,
    migratables: [
        {
            name: 'smvs_localise_website_ontents',
            select: [
                'smvs_aboutorganization',
                'smvs_appointment_success_message',
                'smvs_eligibilitytext',
                '_smvs_language_code_value',
                'smvs_translation_status',
                'statecode'
            ],
            replaceGuids: [
                'smvs_localise_website_ontentid'
            ],
            foreignKeys: {
                '_smvs_language_code_value': {
                    retrievalName: '_smvs_language_code_value',
                    submissionName: 'smvs_language_code',
                    tableName: 'smvs_language_codes'
                }
            }
        }
    ]
};
```

### Configuration Breakdown

- **Credentials**: Secure Dataverse access details (base URL, client ID, etc.).
- **Source and Destination**: `sourceBuId` and `destinationBuId` determine the business units to migrate between.
- **Migratables**:
    - The `name` specifies which table is being migrated.
    - The `select` array allows you to specify which fields to migrate, giving flexibility to exclude unnecessary fields.
    - **GUID Management**: The `replaceGuids` section lists fields that require new GUIDs for the destination.
    - **Foreign Keys**: Handles the mapping of related entities between business units.

## Future Enhancements

1. **Automated Rollback Functionality**:
    - Implement automated rollback features to revert changes in case of a migration failure, ensuring data integrity is always protected.

2. **Conflict Resolution**:
    - Enhance the migrator to provide options for resolving conflicts, such as custom logic for merging or updating data when duplicates are detected.

3. **Migration Logging and Analytics**:
    - Add logging capabilities that provide insights into the migration process, including detailed reports on data transferred, errors, and performance metrics.

4. **User Interface**:
    - Develop a web-based interface to simplify configuration management, providing non-technical users with a more intuitive way to initiate migrations.

## Contribution Guidelines

We welcome contributions to improve the **Business-Unit-Data-Migrator**. Key areas for contributions include:
- **Enhancing data integrity checks** and **optimizing performance**.
- **Extending compatibility** for various versions of Dataverse or adding support for new entity types.
- **Improving documentation** and sample configurations for better community adoption.

Please refer to the `CONTRIBUTING.md` document in the repository for further details on contributing.

## Conclusion

The **Business-Unit-Data-Migrator** aims to simplify and streamline the process of migrating data between business units within Dataverse, providing configurable, reliable, and efficient migration solutions. By focusing on maintaining data integrity and relationships, the tool minimizes risks associated with data movement while providing organizations with the flexibility they need to manage their data effectively.

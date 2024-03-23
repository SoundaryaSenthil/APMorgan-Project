AP Morgan Data Platform Project

- Overview

The Azure AP Morgan Data Platform Project is a sophisticated data processing solution designed to handle CSV files generated by many internal applications. These files are crucial for business operations and require careful validation and organization to maintain data integrity. The project utilizes Azure services and tools to automate the ingestion, validation, and sorting of these files, ensuring accuracy and efficiency in data management.

- Process
 
<img width="394" alt="Project2_Archiecture" src="https://github.com/SoundaryaSenthil/proj2/assets/161588836/edd5bf16-0b42-4994-a5be-b556134749bd">
 
- Data Ingestion: CSV files are received from an internal application and stored in Azure Data Lake Storage Gen2 (ADLS). This step involves establishing a reliable pipeline for transferring files from the application to the storage container.

 Validation and Sorting: Upon arrival in ADLS, the CSV files undergo validation checks to ensure data quality. This includes verifying the filename against predefined criteria and validating the date formats within the files. Databricks notebooks are employed to execute these validation tasks efficiently.

- Validation Process:
When new data arrived, we compared its schema with the source schema.
     -Check for duplicate rows. If it contains duplicate rows,file need to be rejected.
     -Need to validate the date format for all the date fields.Date column names and desired date format is stored in Azure SQL server.If validations fails,file need to be rejected.

- Folder Management: Based on the validation results, the files are sorted into distinct folders within ADLS. Files that pass validation are moved to the staging folder for further processing, while files that fail validation are redirected to the rejection folder for manual review and resolution. This folder management system ensures that only accurate and reliable data is processed further, while flagged data can be addressed separately.

- Benefits:
Ensures that only unique files proceed to the staging area.
Prevents redundant data processing and maintains data integrity.

Tools and Technologies

The project utilizes various Azure services and tools to accomplish its objectives:

  Azure Data Factory (ADF): ADF orchestrates and automates data workflows, including the ingestion of CSV files into ADLS and triggering validation processes.

  Databricks: Databricks provides a scalable data analytics platform for executing validation checks efficiently using Python or Scala notebooks.

  Azure Data Lake Storage Gen2 (ADLS): ADLS serves as the storage repository for the incoming CSV files, providing a scalable and reliable storage solution for big data processing.
  Azure SQL Server
  SQL server Management Studio
  Azure Key Vault: Key Vault securely stores and manages sensitive credentials, ensuring secure connections between Azure services, such as Databricks and Azure SQL.

- Implementation

The project is implemented using Python scripts for tasks such as file filtering, date format validation, and folder management. These scripts are integrated into Databricks notebooks for seamless execution within the Azure environment. Additionally, Azure Data Factory pipelines are configured to automate the entire data processing workflow, triggered by the arrival of new CSV files in the storage container.

 Security and Automation

Security is a paramount concern in the project, and Azure Key Vault is employed to securely store sensitive credentials and connection strings. This ensures that only authorized users and services can access the required resources. Automation is achieved through Azure Data Factory triggers, which automatically initiate data processing workflows in response to new file arrivals, minimizing manual intervention and maximizing efficiency in data processing operations.

 Conclusion

The Azure AP Morgan Data Platform Project provides a robust and scalable solution for managing CSV files generated by an internal application. By leveraging Azure services and tools, the project ensures data integrity, accuracy, and security throughout the data processing lifecycle, enabling organizations to make informed decisions based on reliable data insights.

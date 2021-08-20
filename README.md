# sp_CRUDGen

sp_CRUDGen is a free open-source SQL Server stored procedure that generates stored procedures for you based on your tables and metadata like foreign keys and data types. The generated stored procedure code utilizes the SQL Server community best practices.

You can use sp_CRUDGen to generate 11 different stored procedures from basic your **C**reate, **R**ead, **U**pdate, **D**elete, Upsert stored procedures to extremely advanced safe dynamic search stored procedures otherwise known as optional parameters, kitchen sink, Swiss army knife, catch-all queries.

sp_CRUDGen will auto-generate and regenerate stored procedures for you. If you want to customize one of the generated stored procedures you can remove `<auto-generated>` comment section and the stored procedure will not be overwritten.

Install and execute sp_CRUDGen in the user database and not master.

Each table takes around 7 seconds to create the stored procedures. There is some looping in sp_CRUDGen that could be changed to set based operation if anyone would like.

Fork the repo to change the T-SQL style (or format with a tool like Redgate SQL Prompt) and naming conventions. Remember to create a pull request if you added something cool so the rest of the community can benefit.

Table names should be PascalCase for best table alias naming.

Use FOREIGN KEY REFERENCES between tables for ReadEager and Search to recurse over related tables.

There are included table columns you can edit in sp_CRUDGen to customize for your column naming convention.

 - RowUpdatePersonId int - Is the person who last updated the row.
   FOREIGN KEY REFERENCES to a Person table.
 - RowUpdateTime datetimeoffset(7) - is the date and time with offset
   when the row was last updated.
 - RowCreateTime datetimeoffset(7) - is the date and time with offset
   when the row was created.
 - RowVersionStamp timestamp/rowversion - is used for optimistic
   concurrency in the delete and update stored procedures.

The Search stored procedure does not work with every column data type.

If you use extended properties description names on tables and columns they will be included as comments in the stored procedures.

Do not use SQL Server reserved keywords in object names.
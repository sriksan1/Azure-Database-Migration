Milestone 2:
-- Created a VM called srikantsantoshvm with a Windows 11 operating machine logging into an aicoreuserprofile. Setup an RDP protocol and downloaded the file and uploaded to a microsoft remote desktop.
-- Installed SSMS and the SQL on the VM, setup an authentication profile
-- Download AdventureWorks.bak file and click restore database in SSMS.

Milestone 3:
-- Create SQL Database by logging online into my azure online account called Srikant_Online with server called srikantaicore and setup an SQL login and pw
-- Having downloaded azure data studio connect to the local database by setting the server as localhost then for the online database as srikantaicore.database.windows.net. Choose SQL login and select the appropriate database name and connect to the online db and the local database.
-- Download the server schema migration extension then perform the migration. Then the data migration can be performed can be perfomed by clicking the local database and then clicking migration then setup an online Database Migration Service and setup an integration runtime.
-- To check migration success, I looked online and checked out the online database and just performed some search queries and the results looked the same. By writing '''select *, from person.Contact;'''

Milestone 4:
-- Crate a Full backup of the on premise db on the local machine using SSMS, then go onto blob storage and then create a container and upload a file to my account called backupssrikant.
Provision a new vm srikantdevelopmentmachine and download SSMS and Azure Data Studio. Download the backup from the container and restore db from the localhost and setup the db on azure data studio called production_db and setup periodic backups. First setup server credentials and from the storage account find the access key and save credentials as a query. In SSMS setup a Manitenance Plan Wizard to setup a weekly backup schedule. Upload it to my storage container backupssrikant and hit execute.

Milestone 5:
--Mimic Data Loss, I corrupted the data '''select *
from Person.ContactType 
--UPDATE TOP (15) Person.ContactType
--SET Name = CONCAT('Anon', ContactTypeID)''' to the database. I restored the database to the previous point before the corruption.
--I checked select *
from Person.ContactType to make sure the restored db was correct.

Milestone 6: I have selected production_db to restore then since srikantaicore is its server, I found replicas and create-replica and made a new US server srikantreplicationserver.
-- Then I created a failover group srikfailover then performed failover and checked a few of the tables using sql query editor in azure to check the databases all looked the same. Then reversed it back to make UK the primary.

Milestone 7:
-- So setup an Microsoft Entra Admin as srikantsantosh@btinternet.com for my production_db database. I chose it from the list of users and mine was selected from the list on azure. Then I reconnected to my azure database on Azure Data Studio online using my email account. 
-- Went on Microsoft Entra ID homepage and created a user DB_Reader_srikant, then the SQL query '''CREATE USER [DB_Reader_srikant@aicoreusers.onmicrosoft.com]FROM EXTERNAL PROVIDER;
ALTER ROLE db_datareader ADD MEMBER [DB_Reader_@srikant@aicoreusers.onmicrosoft.com];
'''Then connected to the local production_db and logged in.
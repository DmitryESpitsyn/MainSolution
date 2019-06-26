# MainSolution
This script creates all jobs that you might need for SQL Instance (as standard)
  File:     MaintenanceJobs.sql
  Version:	1906.260626 - June, 2019

  Summary:  	
	This script creates a maintenance job based on the solution from Ola Hallengren (State: 14 June 2019).
	Any updates will be included in next release.
	Note that you always need CommandExecute; DatabaseBackup, DatabaseIntegrityCheck, and IndexOptimize are using it. 
    	You need CommandLog if you are going to use the option to log commands to a table.

  Supported SQL Server Versions: 2008R2 | 2012 | 2014 | 2016 | 2017

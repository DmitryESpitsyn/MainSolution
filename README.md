# MainSolution
This script creates all jobs that you might need for SQL Instance (as standard)
  File:     MaintenanceJobs.sql
  Version:	1906.260626 - June, 2019

  Summary:  	
		This script creates a maintenance job based on the solution from Ola Hallengren (State: 14 June 2019).
		Any updates will be included in next release.
    Note that you always need CommandExecute; DatabaseBackup, DatabaseIntegrityCheck, and IndexOptimize are using it. 
    You need CommandLog if you are going to use the option to log commands to a table.

  Version Updates:
	14.06.2019: | Added by Dmitry Spitsyn
	- Creates a Database Mail account holding information about an SMTP account
	05.06.2019: | Added by Dmitry Spitsyn
		- Apply Prefix as variable for environment
	30.04.2019: | Added by Dmitry Spitsyn
		- Extend check existing modules and prove number of Solution Version
		- Step created to exclude a situation where a database backup would fail, 
      # for example due to a network error - specifically "Operating system error 59(An unexpected network error occurred.)"
			# The solution identify only those database backups that failed and retry back them up again
			# Extend and sort all backup jobs parameters
			# Specify extended parameters for full backups
			# Specify descriptions for backup jobs if backup directory is none standard
			# Points attention for service account rights on this directory
			# Remove unused variable and all assignments
	04.03.2019: | Added by Dmitry Spitsyn
			# Optimize check existing modules
		  	# Changes in output file for delete short file names
			# Specify MaxDOP value
			# Specify the database order for user databases
			# Include copy-only option, which does not affect the normal sequence of backups
			# Changes in create / delete routine
			# Specify the full backup databases process in parallel
			# Specify extended parameters for full backups
	28.11.2018: | Added by Dmitry Spitsyn
			# Determine Collation setting for SharePoint instances
			# Extend parameter TimeLimit for SharePoint and none SharePoint instances
			# Extend fragmentation level, methods and execution time for SharePoint instances
			# Extend Integritet check for none SharePoint instaces
	11.11.2018: | Added by Dmitry Spitsyn following parameters
			# Set parameter LockTimeout in ST02: OPTIMIZE_INDEX_USER_DATABASES to 300 seconds
			# Set parameter StatisticsModificationLevel in step ST02: OPTIMIZE_INDEX_USER_DATABASES to 5 percent
			# Delete parameter OnlyModifiedStatistics
			# Optimize random time for job execution
			# Set OutputFileIndexOptimize only for USER databases.
			# Include parameters @retry_attempts (2) and @retry_interval (10) 
      # in step ST02: OPTIMIZE_INDEX_USER_DATABASES | none SharePoint Instances
	01.09.2018: | Added by Dmitry Spitsyn following steps and parameters
			# Change Backup-Operator to CCMS-Operator (Managed Service)
			# Naming conventions and general rules for Maintenance Solution in environment 
      # (Purpose: adding clarity and uniformity to scripts and functionality)
			# Create Step: ST01: CHECK_INTEGRITY_ALL_DATABASES
			# Create Step: ST02: OPTIMIZE_INDEX_ALL_DATABASES
			# Create Step: ST03: OPTIMIZE_INDEX_MSDB
			# Create Step: ST04: CLEANUP_BACKUP_HISTORY
			# Create Step: ST05: CLEANUP_TABLE_COMMANDLOG
			# Create Step: ST06: CLEANUP_JOBS_HISTORY
			# Create Step: ST07: CLEANUP_MESSAGES
			# Create Step: ST08: CLEANUP_OUTPUT_FILE
			# Create Step: ST09: CHECK_STEPS_ERRORS
			# Create Job: STOP_EXECUTION_MAINTENANCE_JOBS
			# Integration Backup Jobs	
			# Extended event for DeleteMaintenanceSolution
			# Check for existing Solution Version and modules
			# Extended comments
			# Specify dynamically backup directory
			# Specify parameters for all steps
			# Generate random values for execution time
			# Error message for agent job step failure
	22.10.2017: | Added by Dmitry Spitsyn
			# Added step OutputFileCleanup to the job
	15.05.2015: | Added by Dmitry Spitsyn
			# Made Backup Job Creation an Option, Added Creation of Job Killer Job for future use
			# Added two Timeout Paramters, one for Database Integrity Checks, one for Index Optimizing
	27.11.2014: | Added by Dmitry Spitsyn
			# Added Notification and Backup-Operator Life-cycle for backupfiles set to one week
	16.05.2014: | Added by Dmitry Spitsyn
			# Added Database Backup
	26.09.2013: | Added by Dmitry Spitsyn
			# Initial Version

	Supported SQL Server Versions: 2008R2 | 2012 | 2014 | 2016 | 2017

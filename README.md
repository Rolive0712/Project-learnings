**** SSIS learnings


1. In UAT and PROD database, SQL agent job owner cannot be Service Account (SA). So setup Proxy Account which will have necessary roles/ permissions to execute jobs.
All agent job owner will be proxy account. The "Run AS" dropdown for the Agent job "STEP" will also run using proxy account.

2. Packages can be deployed in SQL server (MSDB DB), File System, SSISDB catalog.
To move out of MSDB, its easy as during job creation, we just have to change path from MSDB path to filesystem.
Once in filesystem, we can execute jobs using "DTEXEC" command which can be setup in batch files. batch file path should be configured in agent job script during deployment.

3. One important point, is to proxy proxy account access to subsystems. for batch file execute, the account should have permission on "CMDEXEC" subsystem.


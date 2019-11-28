# Excel Connection String Issue in SSIS
## SSIS Error: The requested OLE DB provider Microsoft.Jet.OLEDB.8.0 is not registered.


This error actually happens conditionally:

1. When running in _Visual Stuodio (SSDT)_ Debug Mode, As long as you set **Run64BitRuntime = False** in the Debug Configuration,
_The ETL package would run without raising this Error_


2. When run as SSIS in a **SQL Server Agent Job**, _it will give you this Error_!


Solution:
Manually modifying the connection string in the ETL Package to (example):

Provider=Microsoft.**_ACE.OLEDB.12.0_**;Data Source=_\\Server\\Filepath\_;Extended Properties="**_Excel 8.0_**;HDR=YES";

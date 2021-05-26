# autoUpdateTable
**READ ME**

Introduction -------------

The Python script, "autoUpdateInfo_SCRIPT.py", automatically updates the number of User Licenses in an Excel spreadsheet as it is changed in 
Salesforce. Python libraries are used to fetch a Salesforce URL's HTML, which is then parsed to locate the relevant Salesforce object, and 
copy it to a CSV file. Windows scheduler is then used to automatically run the script monthly. The script can be adapted to retrieve data 
from any table in Salesforce.

Requirements--------------  
- Windows 10
- Python 3.8.1 (or later version)
- Windows Powershell/ CMD

Steps---------------------

1) Download the latest version of Python from https://www.python.org/downloads, and install to a custom folder (ex. C:\My_Python)
2) Open "Scripts" file (where pip files are present)
3) Open Windows Powershell or Command Prompt and enter the following code segments seqeuntially: 
	pip install requests
	pip install lxml
	pip install bs4
4) Save "autoUpdateInfo_SCRIPT.txt" as "autoUpdateInfo_SCRIPT.py" in the "Scripts" file
7) Open CMD from Python file directory > c:\\My_Python: execute command autoupdateScript.py

To Use Code----------------

Note: The CSV file is saved in the same file directory as c:\\My_Python
• In the payload object in the script; change "password" to your Salesforce password, change "username" to your Salesforce username
• The string "logInUrl" must be changed to the url of the sign-in page of your Sandbox or Production Environment. Defaulted to Salesforce production sign-on page
• The string "destinationUrl" must be changed to the url of the landing page where the table of interest is located in your Sandbox or Production Environment. Defaulted to Company Information page in Salesforce production
• The numerical id on line "div = soup.find(..)" must be changed to the HTML id of the Salesforce table. Defaulted to User Licenses table id in Company Information
	- To locate the HTML id of a table in Salesforce, right click the web page and select "view page source". Then use CRTL-F and search up "User License". Copy and paste the HTML id most similar to "RelatedUserLicenseList_body", into the script. 

Explanation----------------
Uses "datetime" library to retrieve the current date, which is used to create a dated filename. Uses the "requests" library to create a session with Salesforce to login using your log-in information.
Parses through webpage HTML to locate table using "beautiful soup" library, and iterates through table using known HTML table tags to retrieve table data and output to csv file.  

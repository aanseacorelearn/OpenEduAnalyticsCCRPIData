Set up for OEA with Contoso module with custom data
You can setup this fully functional reference architecture (which includes test data sets for basic examples of usage) in 3 steps:
1.	Open cloud shell in your Azure subscription (use ctrl+click on the button below to open in a new page)
 
2.	Download the OEA framework setup script and framework assets to your Azure clouddrive
cd clouddrive
git clone https://github.com/aanseacorelearn/OpenEduAnalyticsCCRPIData.git oea
 
3.	Run the setup script like this (substitute "mysuffix" with your preferred suffix representing your org, which must be less than 13 characters and can only contain letters and numbers - this will be used as a suffix in the naming of provisioned resources):
./oea/setup.sh [mysuffix]

Set up Microsoft Education Insights module with test data
•	Open cloud shell in your Azure subscription (use ctrl+click on the button below to open in a new page)
 
•	Download the module release to your Azure clouddrive
1.	cd clouddrive
2.	wget https://github.com/microsoft/OpenEduAnalytics/releases/download/module_Microsoft_Education_Insights_v0.1/module_Microsoft_Education_Insights_v0.1.zip
3.	unzip ./module_Microsoft_Education_Insights_v0.1.zip
•	Run the setup script like this (substitute "mysynapseworkspacename" with your synapse workspace name, which must be less than 13 characters and can only contain letters and numbers - e.g. syn-oea-workspacename):
./module_Microsoft_Education_Insights_v0.1/setup.sh mysynapseworkspacename) to install this package into your own environment.
After this, both setups follow the below steps
1)	Trigger 0_main pipeline file for Contoso module with test data landing
2)	Trigger 0_main pipeline file for insights module with test data landing
3)	The Power BI .pbix files can be found in the below link, 
https://github.com/aanseacorelearn/OpenEduAnalyticsCCRPIData/tree/main/powerbi
		Import the two files below into the Power BI desktop and publish them in the workspace.
-	Contoso Reports.pbix
-	Insights Module Report.pbix

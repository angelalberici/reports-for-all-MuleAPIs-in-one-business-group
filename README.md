# reports-for-all-MuleAPIs-in-one-business-group
Export all the Runtime Manager Mule APIs in all Environments for one Business Group and Export all the Anypoint Monitoring Reports


# Disclaimer 
This is not a MuleSoft Product. MuleSoft does not have any responsability over your usage and there is no Support available around it. It's an utility application that helps displaying your Patched dates for applications. Content is my own and not the views of my employer. I am not representing MuleSoft in this content.

# When to use it
Recommended only for bigger Enterprises with at least 20+ APIs where Governability becomes more and more important. Allows you to: 
1. Get a Report for all the applications in all environments running in one Business Group. Runtime Manager only displays all applications in each Environment without vCores visualization, now you can get a report for all APIs in all Environments in a Business Group
2. Get a all Reports consolidated. Anypoint Monitoring displays all applications in one Environment, instead you can get a Report for all applications in all Environments for one Business Group 

# WIP [FIVE (5) Minutes Video]()
Topics from the recording: 
1.WIP

# WIP What is it? listing-all-apis-versions
Three componentes: 
1. A MuleSoft App to list all Cloudhub APIs for an environment and aggregate the PatchDate, then produces a CSV. You need to add your own Credentials to the Property file
![](img/MuleApp-Flow.png)

2. Postman Collection to call that MuleApp. You need to add your own Auth Headers (OrgID and EnvID). This returns the CSV
![](img/PostmanCollection.png?raw=true)

3. GoogleSpreadsheet Dashboard (based on [this GoogleSheet](https://docs.google.com/spreadsheets/d/1HeiraxiYTIPLPbpST7tcmsIpIcu2WmiDXIdI3CVXu5Q/edit?usp=sharing)  ), where you paste the CSV and you go to the Dashboards tab to visualize all your APIs patch dates 
![](img/DashboardSpreadsheet.png?raw=true)

# WIP How to use it 
1. Download and import the Jar file into Anypoint Studio. Add your own client_id/client_secret in the properties 
2. Download and import the Postman Collection. Add your own OrganizationID and EnvironmentID in the HTTP Headers. Copy the CSV response 
3. Get a fresh copy of [the public GoogleSheet](https://docs.google.com/spreadsheets/d/1HeiraxiYTIPLPbpST7tcmsIpIcu2WmiDXIdI3CVXu5Q/edit?usp=sharing) . Go to Data tab, paste the CSV and use the "Split Text to Columns" (whch splits by Comma)
4. Done. Check your Dashboards view, enjoy! 

# WIP More Context 
1. The Runtime Manager view shows Mule Versions (x.y.z) without the Patch Date (x.y.z PatchDate), unless you go API by API, one by one. You know there are updates pending, but, you want to know if it is patch related 
“Date Modified” includes “Restarts and other updates to the app”. It does not mean last time a Patch was pplied
![](img/RuntimeManagerScreen.png?raw=true)

2. Using Platform APIs you can retrieve CloudhubAPIs, it won’t have the Patch Date; Customer need to make so advanced Loop logic with a MuleAPI or other programming to be able to get a list with all the patch date info. Below in the left, example of what a Customer gets
![](img/PlatformAPIsListCloudhubAPIs.png?raw=true)

3. Ideally, when Patch Update is available, you will immediately apply it and run any automated regression tests, without waiting until Mandatory Patch. Realistically, you prefer to plan it, applying it to most important APIs and testing before the automatic update thus having some time in the unlikely scenario there was a bug

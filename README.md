
RLS row level security - restricts the access to the data over the reports, data published in power BI service by limiting access based on user roles. 

To implement RLS some configurations needs to be done on power BI desktop.  On PBI desktop In Modeling tab , click on Manager roles and write the DAX query as per the requirement and test RLS by clicking on View as . Once configuring in desktop is done publish the report to PBI service and some configuration settings needs be done to implement RLS. If user is admin or member or contributor then RLS is not applicable and if user has viewer access then only RLS works as expected. 

There are 2 types of RLS 1) static RLS  2) Dynamic RLS ...

Static RLS is used when the roles are static and we apply fixed filters to roles. 
Dynamic RLS is used when the users to view the reports keeps on adding or removed. 
Setup – The set-up/configuring is same for both DRLS and SRLS in power BI Desktop .

In my current role I have developed a report for one application and for that particular app users need to raise request to access that application, if user requests access and request is approved then only user will be able to see info in app. So, we had a requirement to implement RLS on that particular report whenever user gets added, that new user should have privilege to access the data in the report. Existing users and users getting added have some roles. Based on that role access needs to restricted. For example, if user is Admin or developer or any special role, they should not have any restriction over the data and the other roles should see the data related to their roles only. So, for this special role I have added a column and given a numbering as 1, for other roles I gave number as 0.  For this column I have applied filter and if the user principal name() gets filtered to 1 then no restriction , if user principal name filters 0 then rows will be filtered and those rows related info only will be shown in report and the user can download only that info. In power BI desktop I wrote a DAX query to filter these roles using user principal name() in modeling tab – mange roles and tested in power BI desktop in view roles. Published the same report in to  power BI service and did some configurations and there also I used test as and tested few users. Also if a user is admin or contributor or member RLS does not work. 

---
layout: default
title: Unused Apps
parent: Apps
grand_parent: Asset Management
nav_order: 1
---

# Remove/Quarantine Unused Apps

For this task, we will use the Operations Monitor application.   Make sure this application is currently being reloaded each day. If you are having issues with this reload or the application settings, please refer to [Operations Monitor - Help Site](https://help.qlik.com/en-US/sense-admin/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Administer_QSEoW/Monitoring_QSEoW/Operations-monitor-app.htm) for descriptions and troubleshooting of the app.			

# Process
1. Open the Operations Monitor App
2. Select the "Apps" sheet
3. In the App Details table object, sort by Last Accessed field and scroll to old dates or null dates 

    - **Priority 1**
        - Look for applications that are Published but have not been accessed
	  [![fig_1.png](images/fig_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/fig_1.png)
    - **Priority 2**
        - Look for applications that are Published and have not been used for a long time
        - (fig 2)
    - **Priority 3**	
        - Look for Unpublished applications that have not been used for a long time
        - (fig 3)
		
    - **Actions**
    	
        1. If you don't already have a stream named "Quarantine", this is a good time to create one. 
            - See instructions and security rule here --> **insert link**
        2. Contact the application owners to let them know you are moving their app(s) to Quarantine	
	    3. Move the applications from Priorities 1,2 and 3 to the Quarantine Stream (fig 4)	
	    4. Any applications that have been in the Quarantine stream for X number of days can be removed (you decide how many days to keep them)
	    
	   ```
	   NOTE:  Instead of just deleting any apps, it is considered a best practice to export the QVF without data and store a copy somewhere to retain the code.
	   ```
	   
    - **Links**
        - [Operations Monitor](https://help.qlik.com/en-US/sense-admin/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Administer_QSEoW/Monitoring_QSEoW/Operations-monitor-app.htm)
        - **insert link to quarantine stream video**
        - **insert link to removing unused apps video**

  
  **Tags**
  
  #monthly

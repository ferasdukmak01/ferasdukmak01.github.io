<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>In this exercise, we will create two domains (and two domain controllers) - one using the Server Manager GUI, and one using PowerShell. We will then create users and groups in each domain using the Active Directory Users and Computers GUI and PowerShell.</title>
</head>
<body>
    <h1>Active Directory HomeLab</h1>
    <p> On the taskbar, click the Windows Start icon, then click the Server Manager icon to open the Windows Server Manager. Allow Server Manager time to load fully (~30 seconds).:</p>
    <img src="https://i.imgur.com/nWZPIb2.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> In the Server Manager, click the Add Roles and Features link to open the Add Roles and Features Wizard.:</p>
    <img src="https://i.imgur.com/t1GQeQv.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> On the Server Roles page, click the Active Directory Domain Services checkbox. Add Features to include the Features required for the Active Directory Domain Services role.:</p>
    <img src="https://i.imgur.com/vR21luf.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> Wait a few minutes for Active Directory Domain Services to be installed. When the installation is complete, you will see a note indicating that there are additional configuration tasks required to promote this server to a domain controller.:</p>
    <img src="https://i.imgur.com/LaVThXR.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> In the upper-right corner, click the Notifications menu, then click the Promote this server to a domain controller link to open the Active Directory Domain Services Configuration Wizard.:</p>
    <img src="https://i.imgur.com/rFUSyE5.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> On the Deployment Configuration page, select the “Add a new forest" radio button, then type superfriends.local in the Root Domain Name field and click Next to continue.:</p>
    <img src="https://i.imgur.com/AgdZ5sV.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    
</body>
</html>

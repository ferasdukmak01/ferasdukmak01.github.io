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
     <p> The Active Directory installer will now perform a prerequisite check to ensure that Active Directory Domain Services can be installed and this server can be promoted to a Domain Controller. There will be a number of warnings that can be ignored. You should see a green checkmark and a message stating, "All prerequisite checks passed successfully".:</p>
    <img src="https://i.imgur.com/gulED90.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> Once re-connected to the Windows Server 2022 GUI machine, right-click the Windows Start icon and select Run, then type dsa.msc and press Enter to launch the Active Directory Users and Computer (ADUC) tool. In the ADUC, you should see your new domain (superfriends.local). ADUC is one of the primary tools for managing Active Directory. You can use ADUC to create and manage organizational units (OU), users, and groups.:</p>
    <img src="https://i.imgur.com/8sXaSMg.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> At the PowerShell prompt, type the following command and press Enter to install Active Directory Domain Services. { Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools }:</p>
    <img src="https://i.imgur.com/5Nmjs5B.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
     <p> At the PowerShell prompt, type the following and press Enter to create the new legionofdoom.local domain: :</p>
    <img src="https://i.imgur.com/xLgbmkl.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> Next, let's return to the superfriends.local domain and start creating some domain objects. From the Machines tab, connect to the Windows 2022 GUI machine. In the ADUC window, expand superfriends.local. Take note of the built-in folders (called containers) the Active Directory Installer created.: :</p>
    <img src="https://i.imgur.com/9RbfvuK.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> In the New Object - User window, fill in the information below for Bruce Wayne, then click Next to continue.
First Name: Bruce
Last Name: Wayne
User logon name: bruce.wayne: :</p>
    <img src="https://i.imgur.com/Sk6L9Ql.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> Click Finish to create the Bruce Wayne User using the ADUC tool. Take note of the new Bruce Wayne user in the Hall of Justice OU. :</p>
    <img src="https://i.imgur.com/rliTPCO.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> From the Machines tab, connect to the Windows 2022 PowerShell machine.
At the PowerShell prompt, type New-ADOrganizationalUnit -Name "Hall of Doom" -Path "DC=legionofdoom,DC=local" and press Enter to create a new OU in the legionofdoom.local domain. At the PowerShell prompt, type Get-ADOrganizationalUnit -Filter ' Name -like "*" ' | Format-table Name and press Enter to confirm your OU's creation. </p>
    <img src="https://i.imgur.com/EM3onXk.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> As you saw with the ADUC tool in the superfriends.local domain, you will see two OUs. In this case, you will see Domain Controllers and Hall of Doom. :</p>
    <img src="https://i.imgur.com/ley4b0b.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> At the PowerShell prompt, type the following and press Enter to create the Lex Luthor user in the Hall of Doom OU.:</p>
    <img src="https://i.imgur.com/xEa8r7f.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
     <p> At the PowerShell prompt, type the following and press Enter to create the Lex Luthor user in the Hall of Doom OU.:</p>
    <img src="https://i.imgur.com/xEa8r7f.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
     <p> When prompted, enter P@ssw0rd! for Lex Luthor's login password. Now at the PowerShell prompt, type Get-ADuser -Filter ' Name -like "Lex*" ' and press Enter to confirm the creation of Lex Luthor's user account.:</p>
    <img src="https://i.imgur.com/xMbNSdu.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> On the taskbar, right-click the Windows Start icon and select Run, then type dsa.msc and press Enter to launch the Active Directory Users and Computer (ADUC) tool. In the ADUC window, expand the legionofdoom.local domain object, then click Hall of Doom. You should see the new Lex Luthor user account.</p>
    <img src="https://i.imgur.com/72ZuEOC.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
     <p> Close the Bruce Wayne and Lex Luthor Properties windows.
Next, we will learn how to create groups. In Active Directory, groups can be used for communication (distribution groups) and permission (security groups). Distribution Groups are only used when Microsoft Exchange is added to a domain. Security Groups are the primary way to grant permissions to domain resources (like files and folders). There are three types of Security Groups: Universal, Global, and Domain Local. Universal Groups: Contains users and groups from any domain in a forest. Global Groups: Contains users and groups from the same domain. Domain Local: Used to grant access to domain objects. Because we have only a single domain in each of our two forests, there is no need to use Universal Groups. With only a single domain, Microsoft recommends the following best practice: AGDLP. AGDLP stands for "account, global, domain local, permission". That means user accounts are added to Global groups, which are added to Domain Local groups. The Domain Local groups are granted permissions to objects.</p>
<p> In the next steps, we will create a Global group in each domain and add our users to the group we create.
From the Machines tab, connect to the Windows 2022 GUI machine.
In the ADUC window, right-click the Hall of Justice OU and select New > Group to open the New Object - Group dialog box.
In the New Object - Group dialog box, enter the following information, then click OK.

Group Name: Heroes
Group scope: Global
Group type: Security

In the ADUC window, you will see a new Global security group in the Hall of Justice OU.</p>
    <img src="https://i.imgur.com/uHkpMix.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
    <p> In the ADUC window, double-click the new Heroes group to open the Heroes - Properties window.
In the Heroes Properties window, click the Members tab, then click Add… to open the Select Users… window.
In the Select Users… window, type Bruce Wayne and click Check Names.

Active Directory will search for Bruce Wayne and fill in his full user principal name. Click OK to complete adding Bruce Wayne to the Heroes Global group.</p>
<img src="https://i.imgur.com/zigKNiM.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
<p> In the Heroes Properties window, verify that Bruce Wayne is now listed on the Members tab, then click OK to close the window.

Now let's create a new Global group using evil PowerShell.
From the Machines tab, connect to the Windows 2022 PowerShell machine.
At the PowerShell prompt, type the following and press Enter to create the Villains Global group in the Hall of Doom OU. At the PowerShell prompt, type Get-ADGroup -Filter ' Name -like "Villains" ' and press Enter to confirm the new group creation.</p>
<img src="https://i.imgur.com/3CflQ9q.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
<p> At the PowerShell prompt, type Add-ADGroupMember -Identity "Villains" -Members lex.luthor and press Enter to add Lex Luthor to the Villains Global group.
At the PowerShell prompt, type Get-ADGroupMember -Identity "Villains" and press Enter to confirm that Lex Luthor is now a member of the Villains Global group.</p>
<img src="https://i.imgur.com/LoaZqnX.png" alt="Lab Screenshot" style="max-width: 100%; height: auto;">
<p> In the ADUC window, open the Properties window for Villains and verify that Lex Luthor is a member.

And that's it! You've now installed Active Directory Domain Services and created multiple OU's, Groups, and Users on two servers, using two different methods. Be sure to answer the questions on the Tasks tab if you haven't already, then proceed to the Challenge Exercise for additional practice. </p>
</body>
</html>

<p align="center">
<img src="https://i.imgur.com/DxGyNuM.png" alt="Network File Shares and Permissions"/>
</p>

<h1>Network File Shares and Permissions</h1>
In this tutorial, we will work with File Shares and Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Network File Shares and Permissions

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2>Actions and Observations</h2>

<!--- Step 1 -->
<p>
In this lab, we will be setting up Network File Shares and Permissions. We will create folders in the Domain Controller Azure Virtual Machine and share them on the network. Certain files will have certain permissions for security access. Only designated people will be able to view certain files.
</p>
<p>
Go to C:/ on the Domain Controller machine and create four folders:
</p>

- read-access
- write-access
- no-access
- accounting

<p>
<img src="https://i.imgur.com/rRoBsNg.png" height="80%" width="80%" alt="C Drive"/>
</p>
<br />

<!--- Step 2 -->
<p>
After the four folders are created. We are going to want to share them on the network so that the Client Machine can view them. We can also set the permissions of the folders in the Domain Controller. Set the following permissions for the Domain Users group:
</p>

- Folder: read-access, Group: "Domain Users", Permissions: "Read"
- Folder: write-access, Group: "Domain Users", Permissions: "Read/Write"
- Folder: no-access, Group: "Domain Admins", Permissions: "Read/Write"
- Skip accounting for now


<p>
<img src="https://i.imgur.com/ABQSHHX.png" height="80%" width="80%" alt="Write Access"/>
</p>
<p>
<img src="https://i.imgur.com/B6NgokB.png" height="80%" width="80%" alt="Network Access"/>
</p>
<br />

<!--- Step 3 -->
<p>
When we login to the Client Machine with a normal user account (use one of the dummy accounts we created in this <a href="https://github.com/galexwade/configure-ad">lab</a>), we can test out the shared files we just created. As you can see the permissions that we set are working properly:
</p>
<p>
<img src="https://i.imgur.com/JBbLJCH.png" height="80%" width="80%" alt="No Access"/>
</p>
<p>
<img src="https://i.imgur.com/s8I0dFD.png" height="80%" width="80%" alt="Network Error"/>
</p>
<br />

<!--- Step 4 -->
<p>
Go back to the Domain Controller. In Active Directory, create a Security Group named "Accountants". The users assigned to this Security Group will be the only ones allowed to view the "Accountants" folder that we created. We have to share the accounting folder just like we did in the previous section. Normal users will not have access to this folder. If we wanted to give a normal user access to the accounting folder they would have to be a part of the "Accountants" Security Group.
</p>
<p>
<img src="https://i.imgur.com/p9xuwa1.png" height="80%" width="80%" alt="Active Directory Users and Computers"/>
</p>
<p>
<img src="https://i.imgur.com/Wx55cGv.png" height="80%" width="80%" alt="C Drive"/>
</p>
<p>
<img src="https://i.imgur.com/PhHBOGl.png" height="80%" width="80%" alt="Domain Drive"/>
</p>
<br />

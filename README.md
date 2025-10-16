# Approach 6: Connect via SSH to the compute instance private IP address using a SSH private key with OCI Bastion host


In this approach, we will connect to the Linux instance using the OCI Bastion service and from there connect to the instance using the private IP address through a tunnel connection.

<img width="2338" height="1710" alt="Access-Manage-Linux-Instance-241" src="https://github.com/user-attachments/assets/0f531fca-fec6-4eb0-8cc7-dc1cf15daca3" />

+ Before we can use the OCI Bastion service, we need to create the OCI Bastion service first.

1. Open the OCI Console and click hamburger menu.
2. Click Identity & Security.
3. Click Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-242" src="https://github.com/user-attachments/assets/56951127-e109-41fd-af3c-467152b6b9f1" />

+ Click **Create Bastion** and enter the following information.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-243" src="https://github.com/user-attachments/assets/b9a40e42-b226-4953-9c05-257b73b30c77" />

1. Enter the Bastion Name.
2. Select the VCN that we want to access with the Bastion service.
3. Select the subnet that we want to access with the Bastion service.
4. Enter an IP address or CIDR that we want to allow to the Bastion service. For this tutorial, we use home IP address of the ISP connection.
5. Click Create bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-244" src="https://github.com/user-attachments/assets/6e677298-056e-41e1-879f-f958bb6408ed" />

+ Click the newly created Bastion service.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-245" src="https://github.com/user-attachments/assets/c9b88c7e-955e-4424-99ae-e2b1883aa6a7" />

+ Notice that the status is set to **CREATING**.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-246" src="https://github.com/user-attachments/assets/7dac60e2-76ed-4489-af90-49f26162e612" />

1. After a few seconds, we will see the status has been changed to ACTIVE.
2. Click Create session to create a session for the Linux instance that we want to manage.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-247" src="https://github.com/user-attachments/assets/40964ea6-db60-430d-905e-083ba21005f6" />

1. Select the **Session Type** as **Managed SSH session**.
2. Enter the **Username**.
3. Enter the Linux compute instance that we want to connect to through the Bastion service.
4. Select a public key that we want to configure for this specific session.
5. Make sure the public key is selected.
6. Click **Create Session**.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-248" src="https://github.com/user-attachments/assets/fbfb0d15-fa7f-43b6-88d1-381c118d7707" />

1. Notice the following error: **To create a Managed SSH session, the Bastion plugin must be enabled on the target instance, but the plugin is disabled**, this means that in order to connect to a Linux instance using Bastion, a piece of software or plugin needs to be installed on the Linux instance and the plugin needs to be enabled.

2. Let’s enable this plugin on the Linux instance and on the OCI Console, click the hamburger menu.

<img width="1516" height="824" alt="Access-Manage-Linux-Instance-249" src="https://github.com/user-attachments/assets/c1d4064e-15f1-4d7a-b1e1-c782bb8008aa" />

+ Click **Instances**.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-250" src="https://github.com/user-attachments/assets/bc506700-18cd-44ab-8c39-ec1d5bfee152" />

+ Select the Linux compute instance.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-251" src="https://github.com/user-attachments/assets/1cb95333-755c-4942-8e13-e7083758e7db" />

+ Scroll down.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-252" src="https://github.com/user-attachments/assets/cbd5116f-0afc-4b17-8210-a1b8a9f15bbf" />

+ Notice that the Bastion plugin is set to disabled.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-253" src="https://github.com/user-attachments/assets/0b7a8f7a-583e-43e9-b573-d542d0cf8a6c" />

+ To enable the Bastion plugin, follow the instruction.

1. Click toggle to enable the Bastion plugin.
2. Wait till the status shows Running.

Note: When we change the toggle from Disabled to Enabled, It can take a minute before the status is actually changed, because in the background the plugin needs to be downloaded, installed and started and this takes time.

3. Let’s recreate the session on the Bastion plugin. On the OCI Console, click the hamburger menu.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-254" src="https://github.com/user-attachments/assets/f5713531-6b6d-45dc-80d5-7a35539c5fe5" />

1. Click Identity & Security.
2. Click Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-255" src="https://github.com/user-attachments/assets/953a9be2-ab36-41cd-a759-8a64482ba746" />

+ Click the Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-256" src="https://github.com/user-attachments/assets/64ca465f-9011-41e9-a3dc-40dc45438153" />

+ Click Create session to create a session for the Linux instance that we want to manage.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-257" src="https://github.com/user-attachments/assets/aa9cd5b6-3c06-40ff-8d80-4f0008ea8156" />

1. Select the Session Type as Managed SSH session.
2. Enter the Username.
3. Select the Linux compute instance that we want to connect to through the Bastion.
4. Select Choose SSH key file.
5. Select a public key that we want to configure for this specific session.
6. Make sure the public key is selected.
7. Click Create Session.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-258" src="https://github.com/user-attachments/assets/6c2b2ea2-72af-49f4-9f1f-c419e1abb122" />

+ Notice the state is Creating.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-259" src="https://github.com/user-attachments/assets/35d0e65c-4b32-4e2a-a4a9-d7481bd9f77e" />

1. When the session is created, see the state is Active.
2. Notice that the default time of the session is 3 hours. After 3 hours the session will be stopped automatically and we will not be able to use the session anymore and we need to create a new session.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-260" src="https://github.com/user-attachments/assets/a5c3ca2d-2348-4591-a936-ff30f8cb5b3e" />

1. Drag and drop the help menu to another spot so that we can access the session menu.
2. Click three dots to access the session menu.
3.Select Copy SSH command.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-261" src="https://github.com/user-attachments/assets/ec4bd60a-394d-43ba-9b1b-5d872d09b701" />

+ Paste the SSH command into a text editor and notice the *<privatekey>* placeholders.

<img width="1118" height="58" alt="Access-Manage-Linux-Instance-262" src="https://github.com/user-attachments/assets/e1cd3c16-7ae8-4db9-a475-05d8437c5a5f" />

Replace the *<privatekey>* placeholders with the name of your private key. Use the private key that corresponds with the public key used, when the Bastion session was created.

<img width="1139" height="60" alt="Access-Manage-Linux-Instance-263" src="https://github.com/user-attachments/assets/f527f185-e44f-4770-916c-15f25448ed82" />

+ Example

* Original command.

```
ssh -i <privateKey> -o ProxyCommand="ssh -i <privateKey> -W %h:%p -p 22 ocid1.bastionsession.oc1.eu-amsterdam-1.amaaaaaaccocy5aapmrn66fdxdlg7lhefofhndmeq2ir6owe5afm2v7oghiq@host.bastion.eu-amsterdam-1.oci.oraclecloud.com" -p 22 opc@10.0.0.176
```

* Modified command.

```
ssh -i ssh-key-2024-01-31.key -o ProxyCommand="ssh -i ssh-key-2024-01-31.key -W %h:%p -p 22 ocid1.bastionsession.oc1.eu-amsterdam-1.amaaaaaaccocy5aapmrn66fdxdlg7lhefofhndmeq2ir6owe5afm2v7oghiq@host.bastion.eu-amsterdam-1.oci.oraclecloud.com" -p 22 opc@10.0.0.176
```

+ Connect to the Linux instance through the Bastion session.

1. Use the full copied command with the private keys added from the computer where we have the private keys stored using the macOS terminal to connect to the Linux instance through the Bastion session.
2. Enter yes to continue.
3. Enter yes to continue.
4. Run the following command to verify the IP address.
5.Verify the IP address.

<img width="1049" height="609" alt="Access-Manage-Linux-Instance-264" src="https://github.com/user-attachments/assets/f4bdd01c-c140-41dd-9cfb-d9a16b3d7a1b" />

+ the Bastion session settings in the OCI Console.

1. Click three dots to access the session menu.
2. Select Delete session.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-265" src="https://github.com/user-attachments/assets/a48abadb-7d15-4ed9-8737-56666e1a238c" />

1. Enter the Session name to confirm the session removal.
2. Click Delete.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-266" src="https://github.com/user-attachments/assets/f1c52eda-0df0-47fe-93c9-fa2c1829fa4a" />

+ Review the state which is Deleting.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-267" src="https://github.com/user-attachments/assets/522c382a-9618-4791-b1c3-3e74df672e96" />

When the session is deleted, the state is set to Deleted.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-268" src="https://github.com/user-attachments/assets/ed10718e-9c63-495c-ab46-24e791d3f58d" />

When the session is deleted the SSH session we opened through the macOS terminal is now also terminated.

<img width="1046" height="609" alt="Access-Manage-Linux-Instance-269" src="https://github.com/user-attachments/assets/c759e0f7-3a8f-4c81-89b0-64d321d4c4f8" />

**Bastion plugin is not present**.

In this approach, we have enabled the Bastion plugin on an already running Linux instance. We can also enable the Bastion plugin when we create an instance from the start.

Select the Advanced options, select the following options and continue with the creation of the instance.

1. Click Oracle Cloud Agent.
2. Select Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-274" src="https://github.com/user-attachments/assets/444f1e55-f73c-4146-b898-3c03a7b7f791" />

When we created a new image from the start and we check the status after the Bastion plugin right after the instance has been created and the status is RUNNING*, we may see an error message with Plugin Bastion not present….

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-275" src="https://github.com/user-attachments/assets/8652763b-ee0c-4662-afcc-a9cfa7d68ab5" />

It can take a minute before the status is actually changed. Because in the background the plugin needs to be downloaded, installed and started and this takes time. Wait for 5 minutes till the status is changed to Running.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-276" src="https://github.com/user-attachments/assets/1e1a0dc5-02d6-4139-b7e6-de47faea28f3" />

When the status is not changed and the message stays **Plugin Bastion not present…**, it may be the case that the Linux instance is not able to reach the internet to download the Bastion plugin. Troubleshoot the internet, NAT and service gateway inside VCN to make sure your instance is able to access the internet.

---

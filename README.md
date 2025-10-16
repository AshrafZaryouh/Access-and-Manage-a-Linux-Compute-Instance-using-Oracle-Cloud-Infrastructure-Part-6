# Approach 6: Connect via SSH to the compute instance private IP address using a SSH private key with OCI Bastion host

In this approach, we will connect to the Linux instance using the OCI Bastion service and from there connect to the instance using the private IP address through a tunnel connection.

<img width="2338" height="1710" alt="Access-Manage-Linux-Instance-241" src="https://github.com/user-attachments/assets/796d029b-852b-4b76-b8b8-97776ad6b32f" />

+ Before we can use the OCI Bastion service, we need to create the OCI Bastion service first.

1. Open the OCI Console and click hamburger menu.
2. Click Identity & Security.
3. Click Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-242" src="https://github.com/user-attachments/assets/7249ec61-28b8-48d5-9d1a-bf0493592d55" />

+ Click **Create Bastion** and enter the following information.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-243" src="https://github.com/user-attachments/assets/3149934c-80bf-4a2d-962a-7701411812e9" />

1. Enter the Bastion Name.
2. Select the VCN that we want to access with the Bastion service.
3. Select the subnet that we want to access with the Bastion service.
4. Enter an IP address or CIDR that we want to allow to the Bastion service. For this tutorial, we use home IP address of the ISP connection.
5. Click Create bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-244" src="https://github.com/user-attachments/assets/4fab9b06-5a5d-40c9-99ba-0e72f76511dd" />

+ Click the newly created Bastion service.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-245" src="https://github.com/user-attachments/assets/e513dc40-a0aa-4aa8-b619-d401eecb8e10" />

+ Notice that the status is set to **CREATING**.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-246" src="https://github.com/user-attachments/assets/6c6ecc38-858d-41eb-a94e-364602448708" />

1. After a few seconds, we will see the status has been changed to ACTIVE.
2. Click Create session to create a session for the Linux instance that we want to manage.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-247" src="https://github.com/user-attachments/assets/3b80320f-c9c9-4fc0-85ea-9967095fcf6d" />

1. Select the **Session Type** as **Managed SSH session**.
2. Enter the **Username**.
3. Enter the Linux compute instance that we want to connect to through the Bastion service.
4. Select a public key that we want to configure for this specific session.
5. Make sure the public key is selected.
6. Click **Create Session**.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-248" src="https://github.com/user-attachments/assets/b38c8b8a-6f86-4147-b09e-9f5bf8d0c644" />

1. Notice the following error: **To create a Managed SSH session, the Bastion plugin must be enabled on the target instance, but the plugin is disabled**, this means that in order to connect to a Linux instance using Bastion, a piece of software or plugin needs to be installed on the Linux instance and the plugin needs to be enabled.

2. Let’s enable this plugin on the Linux instance and on the OCI Console, click the hamburger menu.

<img width="1516" height="824" alt="Access-Manage-Linux-Instance-249" src="https://github.com/user-attachments/assets/18887d6b-c3ef-40a0-96f1-49d15dfb9d42" />

+ Click **Instances**.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-250" src="https://github.com/user-attachments/assets/236c422b-595d-442e-acca-a0ceac9e61d1" />

+ Select the Linux compute instance.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-251" src="https://github.com/user-attachments/assets/4ef46a99-f787-4445-947d-a0fcb67b319f" />

+ Scroll down.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-252" src="https://github.com/user-attachments/assets/4f38efa4-3ae7-41a4-8ebc-c5b91376b6fb" />

+ Notice that the Bastion plugin is set to disabled.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-253" src="https://github.com/user-attachments/assets/e41492bc-7245-4f01-9788-7a572fc7e093" />

+ To enable the Bastion plugin, follow the instruction.

1. Click toggle to enable the Bastion plugin.
2. Wait till the status shows Running.

Note: When we change the toggle from Disabled to Enabled, It can take a minute before the status is actually changed, because in the background the plugin needs to be downloaded, installed and started and this takes time.

3. Let’s recreate the session on the Bastion plugin. On the OCI Console, click the hamburger menu.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-254" src="https://github.com/user-attachments/assets/6dde567d-22b1-4a54-8b97-c8cf1926ef3f" />

1. Click Identity & Security.
2. Click Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-255" src="https://github.com/user-attachments/assets/5b21eb46-1e6c-4fa7-b990-13bce7608231" />

+ Click the Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-256" src="https://github.com/user-attachments/assets/ea15f1b9-f82d-4b62-b22c-5d31f43f3a68" />

+ Click Create session to create a session for the Linux instance that we want to manage.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-257" src="https://github.com/user-attachments/assets/cb7ff88b-a542-427a-9bf8-3d82a8b4088d" />

1. Select the Session Type as Managed SSH session.
2. Enter the Username.
3. Select the Linux compute instance that we want to connect to through the Bastion.
4. Select Choose SSH key file.
5. Select a public key that we want to configure for this specific session.
6. Make sure the public key is selected.
7. Click Create Session.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-258" src="https://github.com/user-attachments/assets/932b5ddd-e178-402e-9b1c-139a923f1550" />

+ Notice the state is Creating.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-259" src="https://github.com/user-attachments/assets/91b28d5b-5f3c-49fe-8a59-4d1824ca46f9" />

1. When the session is created, see the state is Active.
2. Notice that the default time of the session is 3 hours. After 3 hours the session will be stopped automatically and we will not be able to use the session anymore and we need to create a new session.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-260" src="https://github.com/user-attachments/assets/40a6e36f-d5c9-4658-8c12-1de03f6f224f" />

1. Drag and drop the help menu to another spot so that we can access the session menu.
2. Click three dots to access the session menu.
3.Select Copy SSH command.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-261" src="https://github.com/user-attachments/assets/0e072de7-fa03-42f1-ab09-916c42de4c38" />

+ Paste the SSH command into a text editor and notice the *<privatekey>* placeholders.

<img width="1118" height="58" alt="Access-Manage-Linux-Instance-262" src="https://github.com/user-attachments/assets/0f1a134a-2052-48ee-ad43-c0a99d94e18a" />

Replace the *<privatekey>* placeholders with the name of your private key. Use the private key that corresponds with the public key used, when the Bastion session was created.

<img width="1139" height="60" alt="Access-Manage-Linux-Instance-263" src="https://github.com/user-attachments/assets/45656b37-4a54-477f-b383-6a0a9357bc8c" />

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

<img width="1049" height="609" alt="Access-Manage-Linux-Instance-264" src="https://github.com/user-attachments/assets/56b0d1ae-e875-4844-81b8-d38c1c199810" />

+ the Bastion session settings in the OCI Console.

1. Click three dots to access the session menu.
2. Select Delete session.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-265" src="https://github.com/user-attachments/assets/18e5ad1d-c2fa-4e58-8e4a-f12c563994fb" />

1. Enter the Session name to confirm the session removal.
2. Click Delete.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-266" src="https://github.com/user-attachments/assets/163da1f9-c108-42fb-8e95-8dc58cfaa137" />

+ Review the state which is Deleting.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-267" src="https://github.com/user-attachments/assets/7dbf32a3-58ac-4725-a3bc-fee81a85cd3a" />

When the session is deleted, the state is set to Deleted.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-268" src="https://github.com/user-attachments/assets/2b665016-4aa2-4b63-8d8e-4e55e2f88c15" />

When the session is deleted the SSH session we opened through the macOS terminal is now also terminated.

<img width="1046" height="609" alt="Access-Manage-Linux-Instance-269" src="https://github.com/user-attachments/assets/b16fe081-35af-436e-967e-9d45c96948ff" />

**Bastion plugin is not present**.

In this approach, we have enabled the Bastion plugin on an already running Linux instance. We can also enable the Bastion plugin when we create an instance from the start.

Select the Advanced options, select the following options and continue with the creation of the instance.

1. Click Oracle Cloud Agent.
2. Select Bastion.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-274" src="https://github.com/user-attachments/assets/eb0638ec-51f5-4397-afd2-6d88fec5cbee" />

When we created a new image from the start and we check the status after the Bastion plugin right after the instance has been created and the status is RUNNING*, we may see an error message with Plugin Bastion not present….

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-275" src="https://github.com/user-attachments/assets/a85c740f-a9a4-4743-90d7-856d0493ed8e" />

It can take a minute before the status is actually changed. Because in the background the plugin needs to be downloaded, installed and started and this takes time. Wait for 5 minutes till the status is changed to Running.

<img width="1512" height="824" alt="Access-Manage-Linux-Instance-276" src="https://github.com/user-attachments/assets/f0e3aed0-8e01-457f-b8de-8d9520eea0fa" />

When the status is not changed and the message stays **Plugin Bastion not present…**, it may be the case that the Linux instance is not able to reach the internet to download the Bastion plugin. Troubleshoot the internet, NAT and service gateway inside VCN to make sure your instance is able to access the internet.

---

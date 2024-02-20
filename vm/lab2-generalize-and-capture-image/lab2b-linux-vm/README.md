# Lab 2.b: Generalize and capture a Linux Image

This lab will walk you through steps to generalize and capture an image from the VM you created in the previous lab.

<br />

> Note: This lab is part of a series of labs for Mastering the Virtual Machine Offers Workshop. You should finish this lab as well as prior ones before moving on to the next sections.

<br>

## Generalize and Capture
In this module, we will ssh into the vm and generalize the Virtual machine

### SSH into the Virtual Machine
1. On your [Azure Portal](htps://portal.azure.com/#home), navigate to the VM you just created. Click on **Connect** from the tabs on the left under Settings.
1. In the SSH blade, paste the local path where the downloaded private key resides into the Private key path textbox. This will generate the command to ssh into the VM below. Copy this command.
1. Example: when you paste **[C:\Users\CurrentUser\Downloads\vm_key.pem]** into textbox 3, command **ssh -i [C:\Users\CurrentUser\Downloads\vm_key.pem] [user]@[ip]** will be generated at textbox 4.
1. Open command prompt locally and paste this copied command and press enter. Type in yes when prompted to authenticate the host.

### Generalize the VM
1. In the SSH window, enter this command **sudo waagent -deprovision+user**
1. Type Y to continue (you can add the -force parameter to the previous command to avoid the confirmation step).
1. After the command completes, enter Exit to close the SSH client.

### Stop Virtual Machine
1. In the Azure portal, navigate to your VM in your resource group (RG) and de-allocate the VM (Stop).

    Your VM is now generalized and you can create a new VM using this VM disk.

<br>

## Capture the Image
In this module, we will capture an image from the Generalized VM and store it in a Compute Gallery. We will also define Image definitions within the Compute Gallery for organization.

1. Navigate to the VM on [Azure Portal](https://portal.azure.com). You will see that the VM has been stopped under VM Status
1. Click on **Capture** from the options available on top

### Create an Image

1. Select a subscription from the dropdown menu
1. For Resource Group, select the same resource group we created earlier **vmworkshop-rg-YOUR_UNIQUE_STRING**.
1. Under Instance details, select the **Yes, share it to a gallery as a VM image version** radio button
1. Under Gallery Details, select **Create new** and give it a name
1. For Operating system state, select the **Generalized** radio button
1. Click the **Create new** for **Target VM image definition** and give your definition a name and click **OK**
1. Give your image a version name of **0.0.1** 
1. Lastly click **Review + Create** at the bottom. Once validation has passed, click **Create**.

<br>

## Post Image Creation Exercise
In this exercise we will verify that the image is created and ready to be used.
1. In your [Azure Portal](https://portal.azure.com), search for **Compute Gallery** using the search bar and select your new Compute Gallery
1. Click on the definition you created
1. You should now see the version number of the image created as well as verify the Provisioning State is **Succeeded** and Replication Status is **Completed**.


<br>

**Congratulations!** You have now finished this lab.

If you are in a live class setting, please raise your hand (even if virtually) to indicate you are done with the lab.




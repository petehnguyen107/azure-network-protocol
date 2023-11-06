# azure-network-protocol
<h1>Virtual Machine Network in Microsoft Azure</h1>
This tutorial outlines how to set up an Virtual Machine Network in Microsoft Azure and doing some exercises observing traffic.<br />

<h2>Environments and Technologies Used</h2>

<ul>
<li>Microsoft Azure (Virtual Machines/Compute)</li>
<li>Microsoft Remote Desktop</li>
<li>Windows Command Prompt</li>
<li>Wireshark</li>
<li>Network Protocols (ICMP, SSH, DNS, RDP) </li>
</ul>

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Linux (Ubuntu 20.04)

<h2>List of Prerequisites</h2>

<ol>
<li>Microsoft Azure Account and Subscription</li>
<li>Microsoft Remote Desktop Connection</li>
  
</ol>

<h2>Installation Steps</h2>

<h3>Creating our Resource Group and Virtual Machines</h3>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<ol>
  
<li>Through Azure Services, go to Resource groups to create a Resource Group and name your Resource Group RG-VM. Take note of the Region of your Resouce Group as it'll come in play when setting up our VMs. Once done, then click on Review + Create </li>
  
<li>Go to Virtual Machines to create an Azure Virtual Machine. Select the Resource group we've created (RG-VM) and name the virtual machine VM-1. Make sure the Region is the same as your Resource Group and we'll set our Availability Options set to No infrastructure and Security Type to Standard for this tutorial</li>
  
<li>Set the Image (our Operating System) to Windows 10 Pro, Version 22H2, x64 Gen2</li>
  
<li>The Size selected dicates the general processing power and RAM of our VM, for this tutorial we'll set it to Standard_E2s_V3 which provides 2 virtual CPUs and 16 GBs of RAM</li>

<li>Set the username and password of your VM for logging in and make sure to check the box for licensing agreement </li>

<li>Go to the Network tab and notice the Virtual Network created by the Virtual Machine as it should've been made by the Resource Group. It will be made automatically by the Virtual Machine</li>

<li>Then head to the Review + Create and click on Create to deploy your Virtual Machine. Give it some time to fully deploy before moving on.</li>
  
</ol>

<h3>Virtual Machine 2 using Ubuntu</h3>

<ol>
<li>Same process as Virtual Machine 1 but we'll name the VM VM-2 and set the Image to Ubuntu Server 20.04 LTS x64 Gen2</li>

<li>Ubuntu by default has their Administrator Account authentication as SSH public key, so we must set it as Password for logging in through Remote Desktop</li>

  </ol>

  
<h3>Logging into a Virtual Machine using Remote Desktop Connection</h3>
<ol>

<li>Through Azure Services, go to Virtual Machines and select VM-1 we've created and click on Connect to connect to the VM, from this page you can obtain the Public IP Address which we will use to connect to it via Remote Desktop Connection</li>

<li>Copy the address and paste it into Remote Desktop Connection and click on Connect and log in using the username and password you set up for VM-1 (a pop up may show up for verification, just click on "Yes" if it does)</li>

<li>Congrats! You have now successfully logged into your VM!</li>


  
</ol>


</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

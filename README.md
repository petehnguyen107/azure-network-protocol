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

<ol>
  
<li>Through Azure Services, go to Resource groups to create a Resource Group and name your Resource Group RG-VM. Take note of the Region of your Resouce Group as it'll come in play when setting up our VMs. Once done, then click on Review + Create </li>

<img src="https://i.imgur.com/VKSRyve.png" height="60%" width="60%" alt="Creating Resource Group"/>
  
<li>Go to Virtual Machines to create an Azure Virtual Machine. Select the Resource group we've created (RG-VM) and name the virtual machine VM-1. Make sure the Region is the same as your Resource Group and we'll set our Availability Options set to No infrastructure and Security Type to Standard for this tutorial</li>
  
<li>Set the Image (our Operating System) to Windows 10 Pro, Version 22H2, x64 Gen2</li>
  
<li>The Size selected dicates the general processing power and RAM of our VM, for this tutorial we'll set it to Standard_E2s_V3 which provides 2 virtual CPUs and 16 GBs of RAM</li>

<img src="https://i.imgur.com/oVQ9DFE.png" height="60%" width="60%" alt="Selecting Size"/>

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

<h2>Observing Traffic in Virtual Machines</h2>

<h3>Observing ICMP traffic</h3>
<ol>
<li>First, download Wireshark in your VM. Downloads may be slow depending on your VM's CPU
</li>

<li>Once installed, open Wireshark and start capturing packets (the blue fin icon). In the filter bar, type icmp to filter incoming ICMP packets</li>

<li>Back to your physical desktop, head to your Microsoft Azure Account obtain the Private IP Address of VM-2 and copy it</li>

<li>Open up Windows Powershell in VM-1 and in the command line enter ping and the private IP of VM-2. Once done, ICMP packets should now display in Wireshark</li>

<li>We will now start a perpetual / non-stop ping between the Virtual Machines by entering ping then the private IP of VM-2 followed by -t causing nonstop ICMP packets displaying in Wireshark</li>

<li>Heading back to the Microsoft Azure Account, we'll go to the VM-2's Network Security Group (NSG) (which should be named VM-2-nsg) in order to halt the traffic</li>

<li>In VM-2-nsg, we'll go to inbound security rules and create a security rule that denies ICMPs. Click on Add to open a right side pop up to set the rule and dot in Deny under action and ICMP under Protocol. Set the Priority higher than 300 (priorities are inversely proportional meaning lower numbers have higher priority) and name the rule DENY_ICMP_PING then click Add to finish</li>

<li>Once completed, you'll notice the message "Request timed out" will start displaying in Powershell in VM-1, meaning ICMP ping has been halted from our security rule</li>

<li>To reinstate the traffic, simply head back to your Microsoft Azure Account and set the DENY_ICMP_PING inbound rule's action to Allow and save
</li>

</ol>


<h3>Observing SSH traffic</h3>

<ol>
  
<li>In Windows Powershell inside VM-1, type in ssh VM-2@[VM-2's Private IP] then hit Enter, enter in "yes" and it will ask for the password for VM-2</li>

<li>Since we are accessing the Terminal of VM-2 (essentially Linux's version of a command prompt) it doesn't diplay input/dots when typing a password but do know it is registering input when typing</li>

<li>Once logged in, you will be connected to the Terminal of VM-2. You can exit by entering the command exit</li>

<li>Typing in commands such as username and pwd will display traffic on Wireshark, you can filter ssh traffic in Wireshark by typing in ssh in the filter bar</li>

</ol>

<h3>Observing DNS traffic</h3>
<ol>
<li>Filter DNS traffic in Wireshark by entering dns in the filter bar</li>

<li>In Powershell, type in nslookup and a website such as www.disney.com</li>
  
</ol>

<h3>Observing RDP traffic</h3>

<ol>

<li>Filter RDP traffic in Wireshark by entering "tcp.port==3389" in the filter bar and you'll notice non-stop traffic</li>

<li>The reason for the non-stop traffic is due to the RDP is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted</li>

  
</ol>

<h3>Clean up to save resources</h3>

<ol>

<li>Log off Remote Desktop Connection</li>

<li>Delete your Resource Group and VMs after finishing tinkering with them to prevent future costs, deletion of assets on Azure require verification by entering the name of the asset. Also, the Resource Group NetworkWatcherRG is created when creating NSGs for Virutal Machines; delete NetworkWatcherRG too.</li>

  
</ol>

</p>
<br />


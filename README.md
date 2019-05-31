# Azure-VNG-PANOS
Configure IKE/IPSec + BGP for PAN-OS and connect to Azure Virtual Network Gateway

## Brief Description
This skillet will configure IKE/IPSec parameters and BGP in order to connect PAN-OS to Microsoft Azure VNG (Virtual Network Gateway).

## Skillet Details
- Authoring Group: Public Cloud, Networking, IPSec.
- Documentation: Azure VNG IPSec PANOS.pdf
- Github Location: https://github.com/cestebanez91/Azure-VNG-PANOS
- PAN-OS Supported: 8.1.0 minimum
- Cloud Provider(s) Supported:  Azure only dedicated
- Type of Skillet: PAN-OS, multiple xml.
- Purpose: Config

## Detail Description
This skillet will be used to connect your Palo Alto Network device (physical or VM-series) to any Microsoft Azure Virtual Network Gateway to establish an IPSec connection.
Based on parameters given by Azure (VNG public IP address, BGP peer and gateway subnet).
It will create a new IKE gateway and a new Ipsec tunnel, whatever this is already existing, iteration is possible up to four IKE gateways and four IPSec tunnels.
IKE and IPSec profile are compliant to Azure VNG expectations.

This skillet will configure PAN-OS with following features:
-	IKE crypto profile compliant with Azure VNG
-	IPSec crypto profile compliant with Azure VNG
-	IKE gateway to connect to Azure VNG
-	IPSec tunnel
-	Tunnel interface, loopback interface for BGP and Zone
-	Routing and BGP configuration with distribution profile activated

## Content is the following:
-	ikecrypto.xml will configure IKE crypto profile
-	ipseccrypto.xml will configure IPSec crypto profile
-	ikeprofile.xml will configure IKE gateway with iteration
-	ipsecprofile.xml will configure IPSec tunnel with iteration
-	interface.xml will configure tunnel and loopback interfaces
-	zone.xml will configure zones
-	routing.xml will configure BGP parameters to exchange routes



# Prerequisite
In order to run this skillet, you need a running default configuration for PAN-OS and Azure.
## PAN-OS
- VM-Series or physical device running PAN-OS 8.1 running
- untrust and trust interfaces configured
- Default route configured for untrust subnet gateway
- untrust interface is binded to an Azure Public IP ip_address
- Security Policies to allow outbound traffic

## Azure
- VNET, subnets and gateway subnet deployed
- Virtual Network Gateway deployed where you can retreive BGP peer id and AS Number




# Support Policy
The code and templates in the repo are released under an as-is, best effort, support policy. These scripts should be seen as community supported and Palo Alto Networks will contribute our expertise as and when possible. We do not provide technical support or help in using or troubleshooting the components of the project through our normal support options such as Palo Alto Networks support teams, or ASC (Authorized Support Centers) partners and backline support options. The underlying product used (the VM-Series firewall) by the scripts or templates are still supported, but the support is only for the product functionality and not for help in deploying or using the template or script itself. Unless explicitly tagged, all projects or work posted in our GitHub repository (at https://github.com/PaloAltoNetworks) or sites other than our official Downloads page on https://support.paloaltonetworks.com are provided under the best effort policy.

---
title: Running a Demo
description: How to demo the integration.
permalink: /running-a-demo/

layout: post
sidenav: docs-menu
#subnav:
#  - text: Our Pledge
#    href: '#our-pledge'
#  - text: Our Standards
#     href: '#our-standards'
---

1. Find the Windows instance that has been deployed

    ![](../assets/img/connect.png)

    Download the remote desktop file.  The RDP file contains the connection details for the host.  You will need to 
    decrypt the password using the "Get password" link. 

2. Decrypt the password 
    
    ![](../assets/img/decrypt-pwd.png)

3. Connect to the windows instance and verify that the CrowdStrike agent is installed.
    
    Run the command *'sc query csagent'*
    
    ![](../assets/img/cs-status.png)
    
4. Verify from the Windows hostname that the agent is connected to the console and that a policy is applied.

    ![](../assets/img/hostname.png)
    
    Check the falcon console  Got the the Hosts console and search for the hostname shown in the console output.
    
    ![](../assets/img/falcon-host.png)
   
5. Open a browser and try the connect to http://adobeincorp.com

    The connection should fail but it will be sufficient to generate a detection in the console.
    
    ![](../assets/img/generate-detection.png)
    
    

6. Verify the detection in the CrowdStrike console
     
     Observe the "Triggering Indicator" and "command line" fields in the detection providing information about how the 
     detection was triggered. 
     
    ![](../assets/img/detection.png)
    
    
    
7. Check the Security Hub console

    ![](../assets/img/security-hub.png)
    
    Search the security hub console for a finding related to the detection.  *(It may take up to 10 minutes for the 
    detection to appear in security hub as a finding")*
    
    Search by _**"Company name: is CrowdStrike"**_
    
    ![](../assets/img/sec-hub-search.png)
    
    Select the finding of interest
    
    ![](../assets/img/sec-hub-findings.png)
    
    
    
8. Select the finding 
    
    ![](../assets/img/sec-hub-actions.png)
    
    Select the action _*"CRWD-Domain-To-FW"*_
    
    This action will trigger a lambda function which will add the domain to the firewall domain rule group.

9. Goto the Network Firewall Rule Group settings in the AWS console

    ![](../assets/img/net-fw-rg.png)
    
    Verify that the domain has been added to the rule group
    
    ![](../assets/img/domain-rg-policy.png) 

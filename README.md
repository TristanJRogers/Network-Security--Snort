# Network Security-Snort

In this assignment I learned how to use snort within a Linux Environment. 

## Task 1: Stop and Start Snort

In this simple task I simply started and stopped the Snort program in linux. I also performed an nmap scan of www.example.com. Below is the output of the snort terminal

![image](https://github.com/user-attachments/assets/e2246ed0-964c-4f07-8c00-826036531ac6)

## Task 2: Write a simple bad rule

In this task I write a simple bad rule. I did this by first stopping the Snort program. I then add the rule "alert tcp any any -> any any (msg:"TCP detected"; sid:00002:) into the local.rules file with nano. This rule will create an alert whenever a TCP packet from any address on any port is sent to any address on any port. 

![image](https://github.com/user-attachments/assets/754caa8c-af3d-4580-bf50-1a6fb8af5a00)


To test this rule I restarted the snort program and tried to open www.example.com on firefox via a remote machine. Below is a screenshot of the snort terminal afterwards.

![image](https://github.com/user-attachments/assets/928af297-0c86-4c4b-bdfa-5c090b6c2ddc)

## Task 3: Create a custom rule for confidential traffic

In this task there is an unpublished web page that exists on the website www.example.com. Confidential business plans are stored here at www.example.com/plan.html.

We are tasked with adding a rule to snort that will create an alert whenever the text "CONFIDENTIAL" is sent out to the internet. 

To complete this task I created a new rule using nano. The rule is "alert tcp $EXTERNAL_NET any -> $HOME_NET ANY (msg:"CONFIDENTIAL"; content:"CONFIDENTIAL"; nocase; sid:15490385;)".

Rule pt 1

![image](https://github.com/user-attachments/assets/f3a3686e-2600-4a4e-b31f-16bdf9ac38f2)

Rule pt 2

![image](https://github.com/user-attachments/assets/b1fd3d2b-6b8c-4b68-af60-7f2060c9d7c5)

I needed to test this rule so I restarted snort so that the rule takes effect. I then went to the remote machine, cleared the browsing history and visited www.example.com/plan.html. I then checked the snort machine and the rule appears to have worked. 

![image](https://github.com/user-attachments/assets/f99e83cb-14e2-43fd-8be5-aa9060a076b4)

## Task 4: Watching internet traffic

In this task I needed to go to workstation 2 and run "sudo nmap www.example.com". The output did not include the ICMP PING NMAP alerts because snort cannot alert on local traffic. We will need to mirror the traffic in order to see it. 

Next I was tasked with making a change to the rc.local file on the gateway componant so that traffic from workstation 2 would be mirrored to the snort component. See below

![image](https://github.com/user-attachments/assets/747d8251-3efb-494c-8e8e-d62c175c6f64)

I then restarted snort and ran the nmap command again on workstation 2. I could then see the ICMP, PING, and NMAP alerts because the traffic was mirrored which enabled the snort program to see and alert on the traffic. 

![image](https://github.com/user-attachments/assets/9bd2b4e0-bfbd-4ed6-ad5f-d5b3c4dafd97)

## Software/Tools
Snort

Linux

VMware

Nano

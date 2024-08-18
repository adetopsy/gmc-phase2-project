CONDUCTING PRACTICAL WEB APPLICATION ASSESSMENT     USING ZAP


TOOLS NEEDED:

KALI LINUX
 
VIRTUAL MACHINE

OWASP ZAP


PROCEDURES:

(1) Login into Kali after installation in VM

<img width="462" alt="image" src="https://github.com/user-attachments/assets/f2cc1ccc-6aed-4ed8-a6db-4b0516b3dc84">

(2) Open the terminal and input sudo apt update -y

<img width="467" alt="image" src="https://github.com/user-attachments/assets/e1b1ab38-6393-4441-9151-612b0eed86bf">

(3) Upgrade with sudo apt upgrade -y

<img width="470" alt="image" src="https://github.com/user-attachments/assets/5f0d0db7-0366-4a76-af3a-bc45115a073e">

(4) Once finished, you can Install Zaproxy with: sudo apt install zaproxy

<img width="457" alt="image" src="https://github.com/user-attachments/assets/8a92448a-2275-4a5b-be42-fc48ed47d115">

(5) Next, download foxy proxy add-on for firefox browser extension


<img width="482" alt="image" src="https://github.com/user-attachments/assets/6218f3b0-7825-4f50-8874-2113f5d888c0">

(6) Next, open foxyproxy so we can configure it

<img width="247" alt="image" src="https://github.com/user-attachments/assets/4b361b7a-a83c-4248-822e-f57bfc68121c">

(7) 
From here, head to the proxies to enter the following information:
Title: ZAP
Type: HTTP: 
Hostname: 127.0.0.7
Port: 8080
Once finished, click ‘Save’

<img width="470" alt="image" src="https://github.com/user-attachments/assets/63fa8e5e-59c6-4630-b8dc-2630f85b845a">

Whenever we want to proxy through ZAP, head to the addon and select ZAP


Install ZAP certificate

If you don’t use ZAP’s built-in browserbrowse function, you will need to manually set up the certificate on your browser. If you tried accessing any site running SSL/TLS while using your browser outside of ZAP, you must configure it to use ZAP’s CA root certificate to avoid any certificate warnings.

<img width="462" alt="image" src="https://github.com/user-attachments/assets/0f5fdb94-b81a-47b9-b9e4-c5eca5f9ed42">


ZAP recommends you launch your browser through the “Quick Start” area but if you will rather configure your browser manually, here is how to install the Zap certificate-
First, with ZAP running and your Foxyproxy enabled to use ZAP, head https://www.zaproxy.org/download/ once there,click “Download to download the certificate to your system.

<img width="472" alt="image" src="https://github.com/user-attachments/assets/47e5f56b-cd23-4bb5-a3ab-df7e238446ce">

Now, go to your firefox search bar, type: preferences, and press enter. This will take you to the settings page. Search for “certificate” and find the option “ view certificates”

<img width="467" alt="image" src="https://github.com/user-attachments/assets/11b416ed-e3f1-4081-b185-e76c5749f338">


The view certificate let’s you see all your trusted CA certificates. You can import a new certificate for ZAP by pressing “import” and select the file you downloaded.

<img width="464" alt="image" src="https://github.com/user-attachments/assets/5e7cf3e4-9116-4d10-bfce-895d5affa22f">


In the  pop up, select “Trust this CA to identify websites,then click Ok.

<img width="465" alt="image" src="https://github.com/user-attachments/assets/602700ee-ec11-4144-96d5-ae0aae78bc4a">

Any encrypted traffic will work when the ZAP proxy is turned on, allowing us to intercept requests.

(8) Starting ZAP
We can start ZAP in kali in one of two ways; enter zaproxy in the terminal or open it from the applications menu under “Web Application Analysis’

<img width="367" alt="image" src="https://github.com/user-attachments/assets/ec5ff3b9-ef71-457f-85ee-8094570dfcdc">


Then it will open like this:

<img width="349" alt="image" src="https://github.com/user-attachments/assets/dc3f5e7d-246d-4992-a2c7-47fb5cde7f3f">

When you start ZAP, you will see a screen asking, “ Do you want to persist this ZAP session” Persistence will save everything to an HSQL database that you can access to view it’s contents or reload back into ZAP to see all of the request history, site information etc.

We will be choosing “No, I do not want to persist this session at this session at this moment in time”.

<img width="471" alt="image" src="https://github.com/user-attachments/assets/8059d635-c823-4f89-b5f5-a16603585d84">

 (9) ZAP Overview

 
 Before we start using ZAP, let’s examine the main interface and show where some of the key features are located. The interface has a lot of information, ZAP does many things.

 <img width="463" alt="image" src="https://github.com/user-attachments/assets/0d3bef74-9dd3-45c8-a290-8fba4d4c99b1">

Features:

(1) Menu Bar: Here, you can create and manage sessions, create reports, find tools, get help and more.

(2) Toolbar: Includes button that provide shortcuts to the most commonly use features.
(3) Tree window: Displays the hierarchical view of the site you are testing and the script tree.
(4) Quickstart/Workspace Window: This is a quick and ebay way to use ZAP, especially if you are new. It is also  displays request response and scripts you can edit.
(5) Information Window, including:
History tab: This shows a log of all the HTTP requests and responses sent and received through ZAP.
Search tab: This allows you to search through the requests and responses.
Alerts tab: Displays security alerts found during the scans.
Output tab: provides detailed output from various scans and processes
(6) Footer: Displays ZAP status information.

Alerts Counter: This displays a summary of the alerts found. It’s color-coded (like red, yellow, etc.) to represent the severity of the alerts found during the scanning process.
Main Proxy: This is the main proxy configuration that ZAP uses, which is set to "localhost:8080."
Current Scans: This section displays any currently running scans, with icons indicating their status or progress.

Update Addons

Before you begin using ZAP, you should always check for and update any addons that need to be updated. This ensures that you have the most up-to-date experience.

Press CTRL + U  or use the toolbar shortcut to check for updates.

<img width="224" alt="image" src="https://github.com/user-attachments/assets/139a047c-46bb-4c5d-ba5d-33927a9edace">


This will open the installed add-ons. Next to each add-on, you can see its version number and a brief description of its function. If a newer version of an add-on is available, you'll see “Update” to the right of the description.

You can select the ones you want to update individually, but the best way is to update everything simultaneously. 
Select any add-on and “Update All” to initiate the update. 

<img width="475" alt="image" src="https://github.com/user-attachments/assets/63fc9662-7eba-4dc4-9c6e-761c8adb142c">

ZAP Tips
Before we begin, here are a few tips to remember when using ZAP. 

Right-click everywhere and anywhere to see what options are available to you.


<img width="369" alt="image" src="https://github.com/user-attachments/assets/bfcb3553-c175-425b-b31a-91c99d49f78c">


ZAP Spidering
The first tool we’ll show you is the standard spider in ZAP. This spider requests web pages and analyzes them for links to other pages within the same web application. This recursive process keeps going as long as new links are discovered.

The spider builds out the site tree, showing you all the pages found. 

This spider is quite fast and can be used for standard apps. However, you should still consider using this spider on more modern apps in conjunction with the AJAX spider. 

You can select “Spider” from the “Tools” menu or use the CTRL + ALT + S shortcut to start it

<img width="285" alt="image" src="https://github.com/user-attachments/assets/7fdd92a9-cf00-48bb-a7d2-c92ba9567382">

In the following window, enter the URL of the web app you are spidering and select “Recurse.” This tells ZAP to crawl all URLs or directories from the starting URL. 

Once you’re ready, select “Start Scan.”


<img width="461" alt="image" src="https://github.com/user-attachments/assets/52718afb-8f1d-4122-a9ef-4b945bac657f">



Once the spidering is finished, you’ll see all the nodes found for the web app. The lower-right corner indicates that 91 Nodes were found "Nodes Added: 47," which tells us the number of new items the Spider has found and added to the Sites tree during its crawl.


<img width="467" alt="image" src="https://github.com/user-attachments/assets/98c81fef-7fd5-4ca8-8011-cc73d669c68e">


ZAP AJAX Spidering 

More modern apps use JavaScript, and the traditional ZAP spider doesn't really understand how to crawl these properly. 

This is where the AJAX spider comes in. This spider launches a browser, clicks on things, and even fills out forms, giving you a more comprehensive web app overview. It tries to imitate a user's behavior while interacting with the application.

This spider is much slower than the standard one but works much better with today's modern apps. 

To open the AJAX spider, use the “Tools” menu or the shortcut CTRL + ALT + X.

Here, you’ll set the URL of the app you want to test and the browser the spider will use. Options include Firefox, Chrome, and Safari. 

You can also set advanced options. When you’re ready, select “Start Scan.”


<img width="360" alt="image" src="https://github.com/user-attachments/assets/31e15270-7bcc-4841-9def-8fd0c79aa9c5">

Once the scan is finished, any nodes found will be shown in the site tree area with a red spider next to them. The AJAX spider crawled 1461 URLs compared to the standard spider's 138. 

<img width="455" alt="image" src="https://github.com/user-attachments/assets/4a574ace-af82-4fe7-a02c-c0de47d3f9a2">

ZAP Scanning
Before discussing  ZAP's scanning features, remember you should only use ZAP’s active scanning to attack an application you have explicit permission to test.

Passive Scanning
Passive scanning just involves looking at the raw requests and responses. ZAP doesn’t actually do anything; it only looks at the traffic that passes through it. It analyzes this traffic to identify potential vulnerabilities without sending any new requests. 

Passive scanning is safe to use on any web application. 

When you spider a site, ZAP performs a passive scan and reports any alerts in the “Alerts” tab. 

<img width="455" alt="image" src="https://github.com/user-attachments/assets/a7e95aa3-eb64-498b-a097-215049b6a710">

Active Scanning

Active scanning attempts to find other vulnerabilities using known attacks against the selected targets. It can only find certain vulnerabilities, including XSS, SQL injection, buffer overflows, Log4Shell, and remote file inclusion. 

The Active scanner cannot find logical vulnerabilities, such as broken access control.

You can set policies for your scans, although we won’t discuss that here. These policies allow you to set the threshold for the number of issues raised, and the strength options determine the number of attacks performed per parameter.

As with most tools in ZAP, you can set the options for active scanning. These include the number of hosts scanned concurrently, maximum scan duration, and whether to handle CSRF tokens.

Choose “Automated Scan” from the quick start menu to begin.

<img width="476" alt="image" src="https://github.com/user-attachments/assets/45a7fdc5-1e8f-4b79-a29d-572f886aad4a">


This will open up the automated scan launch screen. Here, you’ll set the URL and which spider and browser you want to use. Once you’re ready, select “Attack” to begin.

<img width="469" alt="image" src="https://github.com/user-attachments/assets/03c5fcf2-6e88-4952-ab36-7bbabbe9ebaf">

Once the scan is finished, you can find all the alerts raised by ZAP in the “Alerts” tab.

<img width="303" alt="image" src="https://github.com/user-attachments/assets/c7c6ce15-4ef4-4c82-a277-f20f59432ec8">


As you can see from the above screenshot, ZAP found 15 vulnerabilities organized by severity: high (red), medium (orange), low (yellow), and informational (blue).

ZAP shows you the number of vulnerabilities it has found. Let’s look closer at the SQL injection. Select the arrow next to it to see where the issue was found in the application. Then, select the URL to see detailed information about the alert.


<img width="461" alt="image" src="https://github.com/user-attachments/assets/829ca3d3-7365-46e4-9a33-edf86ddb1930">


ZAP provides quite a bit of information. On the right panel, you’ll see the URL where the alert was found and its risk and confidence level. You’ll also see a CWE and WASC ID from common software security vulnerability lists. Each vulnerability has its own ID number. 

Next, you’ll see a description of the alert and how ZAP confirmed this alert. It notes the attack method used ("AND 1=1 --"). You’ll need to verify this to see if the vulnerability actually exists.  

It also suggests a potential solution: do not trust client-side input and use server-side validation, such as prepared statements, to mitigate the risk.

Next, we will generate report


<img width="477" alt="image" src="https://github.com/user-attachments/assets/75b01f06-f05a-40d5-bd79-348732077c96">


Next click on generate report

<img width="318" alt="image" src="https://github.com/user-attachments/assets/daa4b086-a68c-42ef-95de-c31272670f9b">

Here are the reports:

<img width="455" alt="image" src="https://github.com/user-attachments/assets/7b575e25-96f2-4692-a80d-ed11b15e715e">

<img width="477" alt="image" src="https://github.com/user-attachments/assets/9f23e253-34d6-452e-815f-b6c17bdc09bd">

<img width="391" alt="image" src="https://github.com/user-attachments/assets/0c0999bd-d00b-4f4c-8b79-5e82426d09a5">

<img width="408" alt="image" src="https://github.com/user-attachments/assets/0c7fa304-0e21-4e90-a54c-a75b17bb9380">



<img width="395" alt="image" src="https://github.com/user-attachments/assets/cd8a844f-b089-4211-9b69-c9aa7950f771">

<img width="401" alt="image" src="https://github.com/user-attachments/assets/2d4b542f-ba33-4be2-9e41-ed113a260abb">

<img width="403" alt="image" src="https://github.com/user-attachments/assets/1a760d31-c5ca-43e8-b5c3-10ac247ff50d">

<img width="392" alt="image" src="https://github.com/user-attachments/assets/c9bb9bc0-83e4-40f4-91c2-6768174dadc2">


<img width="370" alt="image" src="https://github.com/user-attachments/assets/88a17dee-6e59-4a94-a124-4120bda26e7f">


<img width="352" alt="image" src="https://github.com/user-attachments/assets/a62a9066-10a6-4591-b0ee-65bf9463cd13">

<img width="439" alt="image" src="https://github.com/user-attachments/assets/1bf705fc-95ca-467c-90f8-8f02cb136406">

<img width="406" alt="image" src="https://github.com/user-attachments/assets/b6e3b9b0-aab0-4977-aa50-bcde016ee0fd">

<img width="342" alt="image" src="https://github.com/user-attachments/assets/9e4a596a-1bd5-4612-b3e0-2c4014f1ad94">

<img width="347" alt="image" src="https://github.com/user-attachments/assets/3dd2fc67-49c7-464b-ac22-8f464517fe32">

<img width="326" alt="image" src="https://github.com/user-attachments/assets/541f9e09-022d-4ef2-8e35-2e38207d1286">

<img width="362" alt="image" src="https://github.com/user-attachments/assets/fb4d1599-bb40-4039-875b-18319b8ddd1c">


<img width="366" alt="image" src="https://github.com/user-attachments/assets/d2a6d1c6-470b-436b-8a03-e3fe272cb8f7">





















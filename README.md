CONDUCTING PRACTICAL WEB APPLICATION ASSESSMENT     USING ZAP


TOOLS NEEDED:

KALI LINUX
VIRTUAL MACHINE
OWASP ZAP


PROCEDURES:

 Login into Kali after installation in VM







Open the terminal and input sudo apt update -y



Upgrade with sudo apt upgrade -y



Once finished, you can Install Zaproxy with: sudo apt install zaproxy


Next, download foxy proxy add-on for firefox browser extension






Next, open foxyproxy so we can configure it
 


From here, head to the proxies to enter the following information:
Title: ZAP
Type: HTTP: 
Hostname: 127.0.0.7
Port: 8080
Once finished, click ‘Save’



Whenever we want to proxy through ZAP, head to the addon and select ZAP




Install ZAP certificate

If you don’t use ZAP’s built-in browserbrowse function, you will need to manually set up the certificate on your browser. If you tried accessing any site running SSL/TLS while using your browser outside of ZAP, you must configure it to use ZAP’s CA root certificate to avoid any certificate warnings.



ZAP recommends you launch your browser through the “Quick Start” area but if you will rather configure your browser manually, here is how to install the Zap certificate-
First, with ZAP running and your Foxyproxy enabled to use ZAP, head https://www.zaproxy.org/download/ once there,click “Download to download the certificate to your system.


Now, go to your firefox search bar, type: preferences, and press enter. This will take you to the settings page. Search for “certificate” and find the option “ view certificates”


The view certificate let’s you see all your trusted CA certificates. You can import a new certificate for ZAP by pressing “import” and select the file you downloaded.



In the  pop up, select “Trust this CA to identify websites,then click Ok.



Any encrypted traffic will work when the ZAP proxy is turned on, allowing us to intercept requests.

Starting ZAP
We can start ZAP in kali in one of two ways; enter zaproxy in the terminal or open it from the applications menu under “Web Application Analysis’





Then it will open like this:



When you start ZAP, you will see a screen asking, “ Do you want to persist this ZAP session” Persistence will save everything to an HSQL database that you can access to view it’s contents or reload back into ZAP to see all of the request history, site information etc.

We will be choosing “No, I do not want to persist this session at this session at this moment in time”.




 ZAP Overview

   Before we start using ZAP, let’s examine the main interface and show where some of the key features are located. The interface has a lot of information, ZAP does many things.



Features:

Menu Bar: Here, you can create and manage sessions, create reports, find tools, get help and more.

Toolbar: Includes button that provide shortcuts to the most commonly use features.
Tree window: Displays the hierarchical view of the site you are testing and the script tree.
Quickstart/Workspace Window: This is a quick and ebay way to use ZAP, especially if you are new. It is also  displays request response and scripts you can edit.
Information Window, including:
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



This will open the installed add-ons. Next to each add-on, you can see its version number and a brief description of its function. If a newer version of an add-on is available, you'll see “Update” to the right of the description.

You can select the ones you want to update individually, but the best way is to update everything simultaneously. 
Select any add-on and “Update All” to initiate the update. 

ZAP Tips
Before we begin, here are a few tips to remember when using ZAP. 

Right-click everywhere and anywhere to see what options are available to you.



ZAP Spidering
The first tool we’ll show you is the standard spider in ZAP. This spider requests web pages and analyzes them for links to other pages within the same web application. This recursive process keeps going as long as new links are discovered.

The spider builds out the site tree, showing you all the pages found. 

This spider is quite fast and can be used for standard apps. However, you should still consider using this spider on more modern apps in conjunction with the AJAX spider. 

You can select “Spider” from the “Tools” menu or use the CTRL + ALT + S shortcut to start it.


ZAP Spidering
The first tool we’ll show you is the standard spider in ZAP. This spider requests web pages and analyzes them for links to other pages within the same web application. This recursive process keeps going as long as new links are discovered.

The spider builds out the site tree, showing you all the pages found. 

This spider is quite fast and can be used for standard apps. However, you should still consider using this spider on more modern apps in conjunction with the AJAX spider. 

You can select “Spider” from the “Tools” menu or use the CTRL + ALT + S shortcut to start it.


In the following window, enter the URL of the web app you are spidering and select “Recurse.” This tells ZAP to crawl all URLs or directories from the starting URL. 

Once you’re ready, select “Start Scan.”





Once the spidering is finished, you’ll see all the nodes found for the web app. The lower-right corner indicates that 91 Nodes were found "Nodes Added: 47," which tells us the number of new items the Spider has found and added to the Sites tree during its crawl.



ZAP AJAX Spidering 
More modern apps use JavaScript, and the traditional ZAP spider doesn't really understand how to crawl these properly. 

This is where the AJAX spider comes in. This spider launches a browser, clicks on things, and even fills out forms, giving you a more comprehensive web app overview. It tries to imitate a user's behavior while interacting with the application.

This spider is much slower than the standard one but works much better with today's modern apps. 

To open the AJAX spider, use the “Tools” menu or the shortcut CTRL + ALT + X.

Here, you’ll set the URL of the app you want to test and the browser the spider will use. Options include Firefox, Chrome, and Safari. 

You can also set advanced options. When you’re ready, select “Start Scan.”

















Once the scan is finished, any nodes found will be shown in the site tree area with a red spider next to them. The AJAX spider crawled 1461 URLs compared to the standard spider's 138. 



ZAP Scanning
Before discussing  ZAP's scanning features, remember you should only use ZAP’s active scanning to attack an application you have explicit permission to test.

Passive Scanning
Passive scanning just involves looking at the raw requests and responses. ZAP doesn’t actually do anything; it only looks at the traffic that passes through it. It analyzes this traffic to identify potential vulnerabilities without sending any new requests. 

Passive scanning is safe to use on any web application. 

When you spider a site, ZAP performs a passive scan and reports any alerts in the “Alerts” tab. 


Active Scanning

Active scanning attempts to find other vulnerabilities using known attacks against the selected targets. It can only find certain vulnerabilities, including XSS, SQL injection, buffer overflows, Log4Shell, and remote file inclusion. 

The Active scanner cannot find logical vulnerabilities, such as broken access control.

You can set policies for your scans, although we won’t discuss that here. These policies allow you to set the threshold for the number of issues raised, and the strength options determine the number of attacks performed per parameter.

As with most tools in ZAP, you can set the options for active scanning. These include the number of hosts scanned concurrently, maximum scan duration, and whether to handle CSRF tokens.

Choose “Automated Scan” from the quick start menu to begin.





This will open up the automated scan launch screen. Here, you’ll set the URL and which spider and browser you want to use. Once you’re ready, select “Attack” to begin.



Once the scan is finished, you can find all the alerts raised by ZAP in the “Alerts” tab.

As you can see from the above screenshot, ZAP found 15 vulnerabilities organized by severity: high (red), medium (orange), low (yellow), and informational (blue).

ZAP shows you the number of vulnerabilities it has found. Let’s look closer at the SQL injection. Select the arrow next to it to see where the issue was found in the application. Then, select the URL to see detailed information about the alert.



ZAP provides quite a bit of information. On the right panel, you’ll see the URL where the alert was found and its risk and confidence level. You’ll also see a CWE and WASC ID from common software security vulnerability lists. Each vulnerability has its own ID number. 

Next, you’ll see a description of the alert and how ZAP confirmed this alert. It notes the attack method used ("AND 1=1 --"). You’ll need to verify this to see if the vulnerability actually exists.  

It also suggests a potential solution: do not trust client-side input and use server-side validation, such as prepared statements, to mitigate the risk.

Next, we will generate report



Next click on generate report




Here are the reports:





























Recommendation

Fixing vulnerabilities identified by OWASP ZAP (Zed Attack Proxy) requires a systematic approach. Here’s a general guide on how to address these vulnerabilities:

1. **Understand the Vulnerabilities:**
   - **Review the Scan Report:** Carefully go through the detailed report provided by ZAP. Each finding will typically include a description of the vulnerability, its severity, the affected URL, and sometimes remediation advice.
   - **Prioritize Vulnerabilities:** Based on the severity (e.g., High, Medium, Low), prioritize which vulnerabilities to fix first. Focus on critical vulnerabilities like SQL Injection, Cross-Site Scripting (XSS), and others that can have severe impacts.

2. **SQL Injection:**
   - **Use Prepared Statements:** Always use prepared statements (parameterized queries) when interacting with the database. This prevents attackers from injecting malicious SQL code.
   - **Input Validation:** Validate and sanitize all user inputs. Ensure that inputs match expected formats (e.g., numbers, email addresses) and reject anything that doesn’t conform.
   - **Use ORM:** If possible, use Object-Relational Mapping (ORM) tools that inherently protect against SQL injection by abstracting database interactions.

3. **Cross-Site Scripting (XSS):**
   - **Escape Output:** Ensure that all dynamic content is properly escaped before being rendered on the webpage. For instance, use context-specific escaping (e.g., HTML, JavaScript, or CSS escaping).
   - **Content Security Policy (CSP):** Implement a robust Content Security Policy that restricts the sources from which scripts can be loaded.
   - **Input Validation:** Sanitize user inputs to ensure that they do not include any malicious scripts.

4. **Cross-Site Request Forgery (CSRF):**
   - **Anti-CSRF Tokens:** Implement anti-CSRF tokens in forms that are validated on the server side. Ensure that these tokens are unique per session.
   - **SameSite Cookies:** Use the `SameSite` attribute for cookies to prevent them from being sent along with cross-site requests.

 5. **Insecure HTTP Headers:**
   - **Set Security Headers:** Ensure that HTTP headers like `X-Content-Type-Options`, `X-Frame-Options`, `X-XSS-Protection`, and `Strict-Transport-Security` are set appropriately.
   - **Content Security Policy (CSP):** A well-defined CSP header can significantly reduce the risk of XSS and other attacks.

 6. **Outdated Software:**
   - **Regularly Update:** Ensure that all software, including third-party libraries and dependencies, is kept up to date. Regularly patch known vulnerabilities.
   - **Dependency Management:** Use tools like OWASP Dependency-Check or Snyk to monitor and update dependencies.

 7. **Authentication Issues:**
   - **Secure Authentication Mechanisms:** Ensure strong authentication mechanisms, such as multi-factor authentication (MFA), password complexity requirements, and account lockout mechanisms after a number of failed attempts.
   - **Session Management:** Implement secure session management, including secure cookies, session timeouts, and invalidation of sessions upon logout.

 8. **Sensitive Data Exposure:**
   - **Encryption:** Ensure sensitive data is encrypted both in transit (using TLS/SSL) and at rest.
   - **Data Masking:** Avoid displaying sensitive data (like full credit card numbers) on user interfaces.

9. **Access Control Issues:**
   - **Least Privilege:** Implement the principle of least privilege, ensuring that users have the minimum access necessary to perform their tasks.
   - **Role-Based Access Control (RBAC):** Implement RBAC to control access to resources based on user roles.

 10. **Business Logic Vulnerabilities:**
   - **Code Review:** Conduct thorough code reviews focusing on business logic to identify and fix any flaws.
   - **Automated Testing:** Implement automated tests to verify that the business logic behaves as expected and doesn't allow bypassing critical controls.

11. **Continuous Monitoring and Testing:**
   - **Automated Scanning:** Integrate ZAP into your CI/CD pipeline to continuously monitor your applications for vulnerabilities.
   - **Manual Testing:** Complement automated scans with manual testing, especially for complex logic and business flows that automated tools might miss.

12. **Documentation and Training:**
   - **Developer Training:** Regularly train your development team on secure coding practices and how to avoid common vulnerabilities.
   - **Maintain Documentation:** Keep up-to-date documentation on security policies, best practices, and how to remediate common vulnerabilities.

By systematically addressing each of these areas, you can significantly improve the security posture of your application and reduce the likelihood of vulnerabilities being exploited.

Conclusion
The above explained in details; conducting practical web application security using ZAP.






























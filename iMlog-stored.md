## Information

### Description
iMLog 1.307 is vulnerable to Cross-Site Scripting via the "User Management" feature which allows users to modify user parameters that they own.  
**Versions Affected:** < 1.307
### Usage/Exploitation
To exploit this vulnerability, an authenticated user needs to navigate to the User Maintenance section. Then by editing his own username, or any other username that he might edit, he can modify the "Last Name" field to add arbitrary code to execute a malicious javascript payload.

### Impact
An attacker could inject malicious javascript code on a controlled user so when an admin goes to the "User Maintenance" malicious code is executed and could lead to new admin user creations resulting in privilege escalation.

### Proof of Concept
========================================
1. Login to user account
2. Go to Setup > "User Maintenance" 
3. Click on "Search" and then select your UserID.
4. Change the "Last Name" input to `<img/src/onerror=prompt('XSS')>`
5. Click on "Save"
6. Refresh the page, XSS will be triggered.

###### Payload: 
`<img/src/onerror=prompt('XSS')>`

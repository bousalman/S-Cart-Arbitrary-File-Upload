# S-Cart Arbitrary File Upload

## Description
The e-Commerce web application S-Cart https://github.com/s-cart/s-cart version 6.4.1 and prior is vulnerable to Arbitrary File Upload on the Admin Panel. Authenticated users on Admin panel can upload a new files thru the Editor module when adding/editing contents such as News or Pages, it's possible to send a HTTP POST request with a malicious payload that contains PHP code. The uploaded file will be written on the content folder and can be accessed thru a GET request. The current checking used by the application when uploading the files is not suffiecient since Attacker can bypass the MIME type checking by sending a crafted img file hosting a magic byte.

## Mitigation
To mitigate this issue, better make a use of the pathinfo() function to get the extension of the uploaded file and make sure to compare it against a whilelist of approved extensions list.

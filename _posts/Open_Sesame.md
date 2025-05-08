---
title: "Pico_CTF_Apriti_sesamo"
date: 2025-03-9
---
![image](https://github.com/user-attachments/assets/0f0d33f4-beb1-4dd6-a717-19338a5a3e45)

This Challenge involved looking at backup pages to find out how authentication worked on *http://verbal-sleep.picoctf.net:58281/impossibleLogin.php* adding a "~" to the end of the url shows a backup of the page that was stored during the development process and inspecting the html I found this blob of php
![image](https://github.com/user-attachments/assets/7310acb8-de64-40e2-ad0d-cd1952d80e52)


"**?php
 if(isset($_POST[base64_decode("\144\130\x4e\154\x63\155\x35\x68\142\127\125\x3d")])&& isset($_POST[base64_decode("\143\x48\x64\x6b")])){$yuf85e0677=$_POST[base64_decode("\144\x58\x4e\154\x63\x6d\65\150\x62\127\x55\75")];$rs35c246d5=$_POST[base64_decode("\143\x48\144\153")];if($yuf85e0677==$rs35c246d5){echo base64_decode("\x50\x47\112\x79\x4c\172\x35\x47\x59\127\154\163\132\127\x51\x68\111\x45\x35\166\x49\x47\132\163\131\127\x63\x67\x5a\155\71\171\111\x48\x6c\166\x64\x51\x3d\x3d");}else{if(sha1($yuf85e0677)===sha1($rs35c246d5)){echo file_get_contents(base64_decode("\x4c\151\64\166\x5a\x6d\x78\x68\x5a\x79\65\60\145\110\x51\75"));}else{echo base64_decode("\x50\107\112\171\x4c\x7a\65\107\x59\x57\154\x73\x5a\127\x51\x68\x49\105\x35\x76\111\x47\132\x73\131\127\x63\x67\x5a\155\71\x79\x49\110\154\x76\x64\x51\x3d\75");}}}?**



This php describes how authentication works on the said "impossible login page". After getting through some simple obfuscation I realized that the website checkes if the username and password are different values. Then it checks if the Sha1 hash of both the username and password vales are equal. If both these checks return true then you get through the login page. A simple Sha1 hash collison.
Here is my python script that utilizes Googles shattered.io pdfs' to preform the hash collision:

![image](https://github.com/user-attachments/assets/e7e3850e-fb48-4873-b6ad-9c7206bebaf1)


This returns the flag! 

![image](https://github.com/user-attachments/assets/df737b4d-95c2-46b2-a525-c094c88ebb88)

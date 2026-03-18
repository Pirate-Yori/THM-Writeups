# Warzone 1
![new](https://assets.tryhackme.com/additional/jrsecanalyst/task2.png)


Ici c'est un exerice de forensic. les outils que je vais utiliser NetworkMiner et Brim (Zui).

### 1-What was the alert signature for Malware Command and Control Activity Detected?

Utilisons Brim pour cela, Brim est un outil d'analyse de paquet tres puissant nous permettant de trouver vite des informations subtentiels.

response : ET Malware MirrorBlast CnC Activity M3


![1](https://github.com/user-attachments/assets/08b43f02-3920-45d3-8857-34e3e1ccb67b)

### 2-What is the source IP address? Enter your answer in a defanged format. 

Ici j'utilise le filtre du nom de la signature et apres avoir pris l'ip source j'utilise le mode defanged ip sur cyberchef, ce qui donne.

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/7d92ef63-a352-48b4-92cb-22ef2e91f17b" />

Response: 172[.]16[.]1[.]102

### 3-What IP address was the destination IP in the alert? Enter your answer in a defanged format. 

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/7d92ef63-a352-48b4-92cb-22ef2e91f17b" />

Idem ici
Response : 169[.]239[.]128[.]11

### 4-Still in VirusTotal, under Community, what threat group is attributed to this IP address?



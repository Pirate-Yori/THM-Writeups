# Warzone 1
![new](https://assets.tryhackme.com/additional/jrsecanalyst/task2.png)


Ici c'est un exerice de forensic. les outils que je vais utiliser NetworkMiner et Brim (Zui).

### 1-What was the alert signature for Malware Command and Control Activity Detected?

Utilisons Brim pour cela, Brim est un outil d'analyse de paquet tres puissant nous permettant de trouver vite des informations subtentiels.

response : ET Malware MirrorBlast CnC Activity M3


![1](https://github.com/user-attachments/assets/08b43f02-3920-45d3-8857-34e3e1ccb67b)

### 2-What is the source IP address? Enter your answer in a defanged format. 

Ici j'utilise le filtre du nom de la signature et apres avoir pris l'ip source j'utilise le mode defanged ip sur cyberchef, ce qui donne.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7d92ef63-a352-48b4-92cb-22ef2e91f17b" />

Response: 172[.]16[.]1[.]102

### 3-What IP address was the destination IP in the alert? Enter your answer in a defanged format. 

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7d92ef63-a352-48b4-92cb-22ef2e91f17b" />

Idem ici
Response : 169[.]239[.]128[.]11

### 4-Still in VirusTotal, under Community, what threat group is attributed to this IP address?

On prend l'adresse ip de destination , l'adresse des hackeurs et on le met dans virustotal

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/1cba8aa2-7814-4e44-a1e4-cb59f2d4a600" />

Response : TA505
TA505, c’est un groupe cybercriminel qui spamme et infecte des systèmes pour gagner de l’argent, souvent via ransomware ou vol de données bancaires.

### 5-What is the malware family?

```MirrorBlast```

MirrorBlast = campagne de malware + phishing
 Utilisé pour infecter des victimes via des documents piégés
 Associé aux tactiques et outils de groupes criminels comme TA505
 Objectif typique : compromettre des organisations (souvent financières) pour installer d’autres malwares ou obtenir des accès furtifs.
 
### 6-Do a search in VirusTotal for the domain from question 4. What was the majority file type listed under Communicating Files?

``` windows installer ```

Dans VirusTotal regarde la partie RELATIONS>Communicated file.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/93689b59-4091-4a24-b213-8144f5e7d541" />


### 7-Inspect the web traffic for the flagged IP address; what is the user-agent in the traffic?


### 8-Retrace the attack; there were multiple IP addresses associated with this attack. What were two other IP addresses? Enter the IP addressed defanged and in numerical order. (format: IPADDR,IPADDR)

### 9-What were the file names of the downloaded files? Enter the answer in the order to the IP addresses from the previous question. (format: file.xyz,file.xyz)


### 10-Inspect the traffic for the first downloaded file from the previous question. Two files will be saved to the same directory. What is the full file path of the directory and the name of the two files? (format: C:\path\file.xyz,C:\path\file.xyz)


### 11-Now do the same and inspect the traffic from the second downloaded file. Two files will be saved to the same directory. What is the full file path of the directory and the name of the two files? (format: C:\path\file.xyz,C:\path\file.xyz)



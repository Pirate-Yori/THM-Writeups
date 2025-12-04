# Hammer
Use your exploitation skills to bypass authentication mechanisms on a website and get RCE.

## 1. Enumeration with rustscan and ffuf
First, we will enumerate the services :

![rar](https://github.com/Pirate-Yori/THM-Writeups/blob/main/WEB/Images/images_hammer/Screenshot%202025-12-04%20102313.png)

On vois ssh et apache on sais tres bien que sans credentials ssh ne va pas nous servir donc jetons un coup d'ooeil a apache.
En allant mettant l'adresse ip:port 1337, On voit une page de login.

![rar](https://github.com/Pirate-Yori/THM-Writeups/blob/main/WEB/Images/images_hammer/Screenshot%202025-12-04%20102641.png)

Si nous connessons l'email on pourra bruteforcer ou on pourra utiliser l'option forgot your password si la generation du code OTP est devinable on aura de la chance.

Continuons l'enumeration
D'abord le code source du site nous donnes une bonne indice

<img width="800" height="385" alt="image" src="https://github.com/user-attachments/assets/8a1e7d88-fbe6-4366-bfe7-6067f86c81cc" />

Ce que veut dire tout les repertoires devrons commencer par hmr ok pas de problemes.
Utilisons fuff

![rar](https://github.com/Pirate-Yori/THM-Writeups/blob/main/WEB/Images/images_hammer/Screenshot%202025-12-04%20100531.png)

Sur hmr_logs/error.log, on vois un username

![rar](https://github.com/Pirate-Yori/THM-Writeups/blob/main/WEB/Images/images_hammer/Screenshot%202025-12-04%20103021.png)

Utilisons l'option forgot password

<img width="1919" height="386" alt="image" src="https://github.com/user-attachments/assets/d7af392f-e4b2-4ccf-b867-bf185d148cb4" />.

<img width="1919" height="487" alt="image" src="https://github.com/user-attachments/assets/bfa15c87-9b5e-4982-89a1-e6bd775c65c2" />

Ok pour bypasser ca sera pas compliqué ils on envoyer un code a 4 chiffre a tester@hammer.thm essayons de deviner.
On peut le faire de plusieurs maniere, moi je prefere utilise du code python qui fera deux choses :
1-Bypasser la restriction rate-limitating
2-generer des codes otps vu que c'est de 4 chiffres on doit envoyer. Avec 4 chiffres nous avons 10 000 combinaisons possibles de chiffres. Cela signifie que, pour garantir que nous avons le bon code, nous devons envoyer au moins 3333,4 requêtes par minute, soit ~56 requêtes par seconde.
je suis aller vite en besogne voici la partie qui montre qu'apres plusuiers tentatices on vous bloque.

<img width="1919" height="487" alt="image" src="https://github.com/user-attachments/assets/c0fbf1c8-9c18-4e37-8a18-eeb643293f28" />

Rate-Limit-Pending: 4 / si on continue on risque d'etre bloquer et pour bypasser c'est restriction vous pouvez jeter un coup d'oeil sur [hackt](https://book.hacktricks.wiki/en/pentesting-web/rate-limit-bypass.html#rate-limit-bypass).
Pour ma part j'ai constaté que la restriction est basé sur les ip donc je dois juste mettre des ips aleatoires qui partent aevec un code a 4 chiffres aleatoires.
X-Forwarded-For aura des ips randoms
j'ai utilisé ce code generer par chatgpt vous avez qu'a chnager votre ip et le phpsessid laisser le port tel qu'il est.
copier le code et mettez le dans un fichier .py rendez le executables et vous aurez un code otp valide

https://github.com/Pirate-Yori/THM-Writeups/blob/main/WEB/Images/images_hammer/code.py

Apres avoir mis le code otp trouve grace au code python changons maintenant le mot de passe en mettant par exemple 12345 et on pourra se connecter mettant avec ces credentials:
tester@hammer.thm:12345


Une fois connecté on constate qu'un code js nous deconnecte en quelque seconde. 
<img width="1919" height="860" alt="image" src="https://github.com/user-attachments/assets/ce3d3ebf-fcd9-4973-b76d-4edcb2d3bb42" />

Avec Burpsuite on va commenter ce code, plus precisement le windows.location.href='logout.php'.

<img width="1919" height="316" alt="image" src="https://github.com/user-attachments/assets/8e71fe46-5f2b-4b75-b9a1-99795a9056eb" />

On vois que le systemes d'authentification utilise est le jwt interessant

<img width="1217" height="335" alt="image" src="https://github.com/user-attachments/assets/a0f9a2a6-8c06-4c9e-8d10-065ccb9ae9a5" />

Allons sur jwt.io ce site est une mine d'or pour les jwt

<img width="1593" height="794" alt="image" src="https://github.com/user-attachments/assets/e008d545-24b0-4318-9f8c-535ab55ba4aa" />

<img width="1396" height="731" alt="image" src="https://github.com/user-attachments/assets/5063f86f-0880-4d0d-adb7-199c403993ea" />

<img width="1621" height="733" alt="image" src="https://github.com/user-attachments/assets/70d7def8-e0b2-4ea8-80a8-100a3167e2cb" />










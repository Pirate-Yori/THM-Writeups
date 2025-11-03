# can_you_see_me
Test your skills as steganography enthusiasts

---

## 1. Decompressing the file
First, we will unzip the file:

![rar](https://github.com/Pirate-Yori/THM-Writeups/blob/main/STEGANOGRAPHY/IMAGES_CTFs/Screenshot%202025-11-03%20103637.png)

We see some text that looks like Japanese: ジョンを知っていますか. Let's translate it.

![japanesse word](https://github.com/Pirate-Yori/THM-Writeups/blob/main/STEGANOGRAPHY/IMAGES_CTFs/Screenshot%202025-11-03%20105702.png)

Ok, this is a hint. We'll need to brute-force, and luckily we have a file `Ouvre_moi.rar`. When we try to unzip it, it asks for a password.

![crack](https://github.com/Pirate-Yori/THM-Writeups/blob/main/STEGANOGRAPHY/IMAGES_CTFs/Screenshot%202025-11-03%20105855.png)

After using `john` to find the password that will allow us to unzip the file, we can finally extract it.

![dezip](https://github.com/Pirate-Yori/THM-Writeups/blob/main/STEGANOGRAPHY/IMAGES_CTFs/Screenshot%202025-11-03%20105957.png)

---

## 2. Inspecting the PDF
We see a PDF file. When we open it, it appears completely blank. Using `strings` we can see a lot of text, so I thought to use `pdftotext` because it converts the readable text from a PDF into plain text (displayed on the screen or saved to a file).

![flag](https://github.com/Pirate-Yori/THM-Writeups/blob/main/STEGANOGRAPHY/IMAGES_CTFs/Screenshot%202025-11-03%20110004.png)

# atelier801-reverse-engineering
atelier801 as a Transformice, RE login password with details. I already have one btw they are for educational purposes only.  
- Illegal attempts can ruin your life
- Date: 07/16/2026, I made it for fun cuz RE is so fun for me.

# What is that JS File?
- It's latest version of atelier801 website javascript codes which all algorithm is here and there is no obfuscate :( (being lazy?)
- If anyone see this and working on Atelier801 or Transformice, I suggest you to do make better security and obfuscate the JS Codes.

# How we can find login password encrypt with reverse-engineering?
- Inside the 1.27.0.js file, there is some libraries like **Crypto**, **SubtleCrypto** and **SHAKikoo**. When you CTRL + F and search for them, you gonna see it easily.
- If it's not working for you,  <img width="590" height="433" alt="image" src="https://github.com/user-attachments/assets/e863808e-cf01-48bb-98a9-50cd4104e520" /> Click all these and leave a breakpoints eventually you will reach to the encryption part.
- After those steps, still can't find the algorithm? Let's try this: <img width="189" height="195" alt="image" src="https://github.com/user-attachments/assets/8d285362-faf9-43af-9624-6dedfbe9a944" /> Form data names like these so we just gonna search pass in 1.27.0.js after some click you will see <img width="699" height="232" alt="image" src="https://github.com/user-attachments/assets/3173c6b4-b0c2-46e3-a06b-04a06e75fcd8" /> this area. this is the password variable name actually #auth_pass_2. As you can see there is jQuery("#auth_pass_2").val(crypte(k)); .val(crypte(k)) this k is non-encrypted password of yours. So crypte(k) is our goal. We found the function of the encrypt algorithm!

# How we can generate encrypted password?
- When you search(ctrl + f) the crypte in 1.27.0.js file  <img width="1488" height="365" alt="image" src="https://github.com/user-attachments/assets/12badd45-9f79-4220-8907-cc6817a8f201" /> You gonna see this beauty. So just copy and paste and use it. As you can see its using Crypto Web Module library and there is another function name is "hash" you can see on the image **, c = hash(a);
    a = [];** right here. <img width="1352" height="153" alt="image" src="https://github.com/user-attachments/assets/678dce79-c681-4aaa-a06f-933b516a4fbf" /> This is the hash function we needed. (I didn't tell it but you need all SHAKikoo funcs like createBlocksFromString and hashBlocks to generate it.)

# DISCLAIMER
**This Repo is just for educational purposes only about reverse engineering and have a license. You're the only responsible about your actions. Just Learn how to do it, do NOT break it, fix it.**

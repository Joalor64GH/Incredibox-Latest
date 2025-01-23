COMPILED APK HERE! (for android users who cant compile it themselves)
https://mega.nz/file/IIhlxTrR#Gu4aq9WaAruwuVfUAW16hzLi-eujQkJmbOfIDyqJTA0

# Requirements
Java Development Kit 
> You can get the latest one [here](https://www.oracle.com/java/technologies/javase-jdk16-downloads.html)

# Setting up Java
1. In Search, search for and then select: System (Control Panel)
2. Click the Advanced system settings link on the right
3. Click Environment Variables
4. In the section System Variables find the PATH environment variable
5. Select it and click Edit
6. Find C:\Program Files\Common Files\Oracle\Java\javapath select it and click Delete
7. Click New and enter C:\Program Files\Java\jdk-16.0.1\bin  
   If you have different version of JDK, check in C:\Program Files\Java and use C:\Program Files\Java\YOUR_VERSION\bin  
   where you replace YOUR_VERSION with version you have in C:\Program Files\Java  
9. Click OK and close Environment Variables
10. Open Command Prompt and try to run command `keytool`  
   If it works you can continue

# Modifying
Before each modification, redownload this repo to be sure that all files are correct  

1. Go to /source/assets/www/ where you can modify Incredibox to your needs  
2. After doing your modifications, go back to /android and open Command Prompt here  
3. In Command Prompt first thing you want to do is building the apk with this command  
   ```
   java -jar apktool.jar b -f -d source -o Incredibox-v0.7.0-unaligned.apk
   ```  
4. Then you need to sign the apk file but first we need to generate a key with this command  (please note the typing is invisible!)
   ```
   keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -deststoretype PKCS12 -keysize 2048 -validity 10000
   ```  
   You will be asked to enter keystore password, remember this password because you will need to use it later 
   You will also be asked to enter details, you can keep it all Unknown and when it asks you if it is correct, answer <ins>yes</ins>  

  # IMPORTANT NOTE BY RIZSIM STUDIOS
   The default password is "changeit" if not then go check you set it to make this work

5. Now we can sign the apk file with this command  
   ```
   jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 -keystore my-release-key.keystore Incredibox-v0.7.0-unaligned.apk alias_name
   ```  
6. Verify the apk file with this command  
   ```
   jarsigner -verify -verbose -certs Incredibox-v0.7.0-unaligned.apk
   ```  
   If verification passed correctly, you can continue  
7. Last thing you need to do is aligning the apk file with this command  
   ```
   zipalign -v 4 Incredibox-v0.7.0-unaligned.apk Incredibox-v0.7.0.apk
   ```  
8. You should now have file called `Incredibox-v0.7.0.apk` which you can move to your phone and install  
   If a prompt shows up saying <ins>Blocked by Play Protect</ins>, just click <ins>install anyway</ins>  
   The reason, you recieve this promt is because you signed the apk file yourself and Play Protect doesn't recognize the developer's signature  

# IMPORTANT THING IS
to make sure your mod DOES NOT replace the OG APP itself use APK Editor Pro: https://mega.nz/file/ocxwVJCL#W7D0UmR38rRP-UZ0fDZTqLNimbowWTHRAKI5MZdSYvk (its the thing I like using alot) and yes it safe I used this before plently amount of times to know that by now

# FINDING THE MANIFEST THING
to replace the app manifest line if you are using apk editor pro is go to APK FILE first (once you have apk editor pro open) if you downloaded it then
then you click full edit on edit mode and decode all files

# THE MANIFEST LINE
find "com.sofarsogood.incredibox" (if you compiled it yourself) or "com.rizsimstudios.incredibox.v9moddablecopy" (if you downloaded the pre complied one)
and replace the line with whatever you want starting with "com"

heres an example "com.yournamehere.modname.versionnodots" (its opitional to have it also included with the the thing ".v9codeport" for anyone downloading it would know)

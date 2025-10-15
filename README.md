# ShadowTrace CTF Walkthrough
A Tryhack me CTF writeup for the ShadowTrace room


<p align="left">
First Open the attackbox on the site and navigate to the location of the binary at C:\Users|DFIRUSER\Desktop\windows-update.exe <br/>
Note: You will have to use this attack box as its a special room so using your own won't work
You Should See this Page <br/>
<img src="https://i.imgur.com/PPeITjM.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

For the first flag we can see it asks for the architecture of the file <br/>
So let's analyze this file, Click on the DFIR Tools folder <br/>
Here we're going to use the tool Pestudio <br/>
Once that's open either drag or open the file ontp the pestudio program and it should look like this <br/>
<img src="https://i.imgur.com/xiSpw3p.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

If we look on the right we can see a property and file section <br/>
If we go to the property thats says "file > type" we can find our first flag, that the file is 64-bit <br/>
<img src="https://i.imgur.com/Ae51uJ9.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

The second flag asks for the hash of the sha256 <br/>
We can find this in the same area if we look at the "file > sha256" property <br/>
Copy that long string in the value section for the flag <br/>
<img src="https://i.imgur.com/BrPj58U.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>



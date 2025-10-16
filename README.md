# ShadowTrace CTF Walkthrough
A Tryhack me CTF writeup for the ShadowTrace room

<h2>Part One: File Analysis</h2>
<br/>
  
<p align="left">
First Open the attackbox on the site and navigate to the location of the binary at C:\Users\DFIRUSER\Desktop\windows-update.exe <br/>
Note: You will have to use this attack box as its a special room so using your own won't work <br/>
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

The third flag asks for use to identify a URL that could be a indicator of compromise <br/>
Let's click on the indicators (imports > flag) section <br/>
Here we can see two indicators called "string > url-pattern" <br/>
Only one gives us an actual URL so copy that and you have your third flag <br/>
<img src="https://i.imgur.com/gTyK4nN.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

The fourth flag asks us to spot a domain <br/>
Unfortunately Pestudio does not have a search function, so while we can find our answer there in any strings related to tryhatme.com it might take some parsing <br/>
let's switch to PE-Bear <br/>
Once there and you've loaded the windows file, click on the string sub category <br/>
Then in the "Search String" section type tryhatme <br/>
Here we can see three strings, and only one looks like a domain with responses.tryhatme.com
<img src="https://i.imgur.com/dEw1Rw9.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

The fifth flag asks for a decoded flag <br/>
If we take a look at the three strings available there is another interesting one, it says tryhatme.com/VEhNe3lvdV9nMHRfc29tZV9JT0NzX2ZyaWVuZH0= <br/>
This looks like something that can be decoded, so I use a site called base64decode.org and enter the entire string that was after tryhatme.com/ <br/>
Looks like we got our flag! <br/>
<img src="https://i.imgur.com/UtJgS15.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

The sixth flag asks for a library related to socket communication <br/>
Let's gp back to Pestudio <br/>
Select the libraries (flag > 3) section <br/>
There's a couple here, so if we take a look at the descriptions then we can find one that says "windows Socket library" <br/>
This seems like what we're looking for so click on the line and we can see the library this belonngs to is WS2_32.dll our final flag for this section! <br/>
<img src="https://i.imgur.com/D5BteWt.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

<h2>Part Two: Alert Analysis</h2>
<br/>


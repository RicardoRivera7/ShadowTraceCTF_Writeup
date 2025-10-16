# ShadowTrace CTF Walkthrough
A Tryhack me CTF writeup for the ShadowTrace room

<h2>Part One: File Analysis</h2>
<br/>
  
<p align="left">
First Open the attackbox on the site and navigate to the location of the binary at C:\Users\DFIRUSER\Desktop\windows-update.exe <br/>
You Should See this Page <br/>
<img src="https://i.imgur.com/PPeITjM.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

<h2>First Flag</h2>
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

<h2>Second Flag</h2>
The second flag asks for the hash of the sha256 <br/>
We can find this in the same area if we look at the "file > sha256" property <br/>
Copy that long string in the value section for the flag <br/>
<img src="https://i.imgur.com/BrPj58U.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>


<h2>Third Flag</h2>
The third flag asks for use to identify a URL that could be a indicator of compromise <br/>
Let's click on the indicators (imports > flag) section <br/>
Here we can see two indicators called "string > url-pattern" <br/>
Only one gives us an actual URL so copy that and you have your third flag <br/>
<img src="https://i.imgur.com/gTyK4nN.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>


<h2>Fourth Flag</h2>
The fourth flag asks us to spot a domain <br/>
Unfortunately Pestudio does not have a search function, so while we can find our answer there in any strings related to tryhatme.com it might take some parsing <br/>
let's switch to PE-Bear <br/>
Once there and you've loaded the windows file, click on the string sub category <br/>
Then in the "Search String" section type tryhatme <br/>
Here we can see three strings, and only one looks like a domain with responses.tryhatme.com
<img src="https://i.imgur.com/dEw1Rw9.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

<h2>Fifth Flag</h2>
The fifth flag asks for a decoded flag <br/>
If we take a look at the three strings available there is another interesting one, it says tryhatme.com/VEhNe3lvdV9nMHRfc29tZV9JT0NzX2ZyaWVuZH0= <br/>
This looks like something that can be decoded, so I use a site called base64decode.org and enter the entire string that was after tryhatme.com/ <br/>
Looks like we got our flag! <br/>
<img src="https://i.imgur.com/UtJgS15.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

<h2>Last Flag</h2>
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

For the first flag it wants us to find the malicious URL in the Powershell.exe processs <br/>
This is the first alert that appears, let's take a look at the command given <br/>
Upon inspection we can see a string and a command before it that states it's in Base64 <br/>
<img src="https://i.imgur.com/PSuJSgi.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

Let's copy this string and paste it into the cyber chef website to see what we find <br/>
You can either drag the base64 recipe from the left to decode it or hit the magic wand icon next to output to do it for you! <br/>
And looks like we dfound our malicious URL! <br/>
<img src="https://i.imgur.com/tLVHchF.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

The Next flag asks for us to find another URL, this time in theChrome.exe process <br/>
Inspecting the command we can immediately seecan interesting string of numbers at the start <br/>
Im unsure of what format this is but cyber Chef can detect thiss if it is anything so Copy all thee numbers <br/>
<img src="https://i.imgur.com/pAqDQxP.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

Paste it into Cyber chef and click the magic wand icon next to Output <br/>
Looks like we were right, it was in decimal format and we found our malicious URL! <br/>
<img src="https://i.imgur.com/AFZGLD5.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>

The final flag asks for the name of the file that was saved by the chrome.exe alert <br/>
If we inspect the command we can see a download section followed by a txt file <br/>
Looks like it was called test.txt and we have our last flag!
<img src="https://i.imgur.com/K7IfQpZ.png" height="80%" width="80%" alt="Pickle Rick"/>
<br/>
<br/>


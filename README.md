Download Link: https://assignmentchef.com/product/solved-cpe-549-introduction-to-cybersecurity-engineering-lab-1-password-cracking
<br>
<strong>Objective:</strong> Use a dictionary attack to crack Linux Passwords.

<strong><em>Background Information: </em></strong>

<ol>

 <li>Linux Password Storage: http://techlister.com/linux/linux-how-to-change-the-hashing-algorithm-on-linux-system/796/</li>

 <li>Windows Password Storage: http://techgenix.com/how-cracked-windows-password-part1/</li>

 <li>John the Ripper Password Cracker: http://openwall.info/wiki/john/tutorials</li>

 <li>Implementation of SHA512-crypt vs MD5-crypt: http://www.vidarholen.net/contents/blog/?p=33</li>

</ol>

Steps:

<ol>

 <li>Write a Python script to perform a dictionary attack on a Linux password file.

  <ol>

   <li>Copy /etc/shadow file to your local directory. Study the format of this file.</li>

   <li>Add the following 3 lines to the /etc/shadow file. For speed purposes remove all other lines.</li>

  </ol></li>

</ol>

tommy:$6$HFQQdE2g$g0eyz6UN.c4Pg1tiQgdPPPXdQ1fEOwttCwzSah/Jo4RE9Eac4H7pgksaNLI/WSIyN8tNtCX4NaAq6Uwz.o.4W1:17400:0:99999:7:::

mathis:$6$niptplk1$.mMMVx4T375WhFkDN5RWEaD93HcmDCx3aBQrn2ZalbiRpl4FB2Rww/BeCPEfSYbegjPvoHM2llQmk/VBbSxWj.:17400:0:99999:7:::

tristan:$6$MWwusFJx$KCoO1wiWKtE.7j/7UiwD.1jXmOckMb5X4GGt1DotLS0laXdFga5n3wGfu43FC/Opxki7mY6Yf9XT.cBGN.pkp0:17400:0:99999:7:::




<ol>

 <li>Use the “crypt” library crypt function to create your hash.</li>

 <li>Use the “hmac” library compare_hash function to compare hashes from the /etc/shadow file to the hashes produced from your guesses.</li>

 <li>Use the string split() function to separate the separate the password lines from the shadow file by the ‘:’ delimiter to isolate the userid and the hash from an entry in the shadow file.</li>

 <li>Calculate the appropriate hash (using the method specified for the entry from the shadow file) for each word in this wordlist (<a href="https://www.openwall.com/passwords/wordlists/password-2011.lst">http://www.openwall.com/passwords/wordlists/password-2011.lst</a>), compare the hash, and stop comparing when you find a match.</li>

 <li>Attempt the dictionary attack for each entry in the shadow file.</li>

 <li>Remember you need to provide the word from the dictionary, the method, and the salt to the crypt() function.</li>

 <li>Print the userid and password when a match is found:“Match found for userid [userid]. Password = [password]”</li>

 <li>Print the “No match was found for [userid]” when there no match in the dictionary.</li>

</ol>
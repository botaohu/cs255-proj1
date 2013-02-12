Team members:

Botao Hu (botaohu@stanford.edu)
Borui Wang (borui@stanford.edu)

Special Instructions:

-Runing Program

We created our own UI imitating the original facebook style. We designed the UI to follow the exact requirement of this assignment. Namely, when user logs in, she has to setup a database password if she hasn't done so. Once the password is setup, she has to enter the password to proceed to view the page on each new browser tab. If the password is wrong, she won't be able to continue and the UI reflects the wrong password. If no key is found in a group, we show a message box to indicate the user to create one. 
We didn't change the workflow of group key creation. So the user, say $A$, could generate a new group key in account setting page. If the other user $B$ want to see the encrypted message sent by $A$, she has to add the same group key of $A$ in $B$'s account setting page. 

Because we can not modify the UI logic of the starter code in the submission, there is a small issue of user experience, i.e., if you enter the group page directly by url, we will prompt you to enter your password; and after that, you will not immediately see the decrypted messages. You have to refresh the page for activating the decryption of the message with your just entered password. 

-Code

We didn't change menifest.json except modifying the javascript file name and adding our names to the description.

We didn't make any change to the code below GetRandomValues() and we implemented the required functions (Encrypt, Decrypt, GenerateKey, SaveKeys, LoadKeys) in the assignment. We added several helper functions under LoadKeys(), their main purposes are building UI (BuildUIBox), initiating and querying database password (GetDBSecurePassword), calculate padding (Unpadding, Padding), implementing the nounce-based counter mode (CTRAESDecript, CTRAESEncript), and implementing the CBC-MAC (CBCMAC). It's easy to see the documentation in the code to learn what they do. Please check our writeup for full details.

- Response to milestone 1 feedback

In response to the milestone 1 feedback, here are several items we want to specially emphasize to make sure the TA understands our design (also commented in code).

1. Notice that we only store the encrypted password in sessionStore and the salt for the password in localStorage. We NEVER store the clear text of password in any location.
2. Notice that we use a random nonce and XOR the nonce with the counter to generate the IV. The counter assumes that we're not encrypting over 2^32 bits of data.
3. Notice that we first encrypt the message, then MAC the cipher text, which is suggested to be more secure in class.
4. Notice that the encrypted db password and the encrypted group keys are all CBC-MAC-ed, and no same MAC key is used for multiple purposes.
5. As we are using callback functions for UI and it's quite complex to change our code back to prompt again. We'll leave it there. We're sorry to create the extra work for you to test through it manually. We made sure we passed all tests suggested in https://piazza.com/class#winter2013/cs255/137 
Team members:

Botao Hu (botaohu@stanford.edu)
Borui Wang (borui@stanford.edu)

Special Instructions:

-Runing Program

We created our own UI imitating the original facebook style. We designed the UI to follow the exact requirement of this assignment. Namely, when user logs in, she has to setup a database password if she hasn't done so. Once the password is setup, she has to enter the password to proceed to view the page on each new browser tab. If the password is wrong, she won't be able to continue and the UI reflects the wrong password. If no key is found in a group, we show a message box to indicate the user to create one. We didn't change the workflow of group key creation.

-Code

We didn't change menifest.json except modifying the javascript file name and adding our names to the description.

We didn't make any change to the code below GetRandomValues() and we implemented the required functions (Encrypt, Decrypt, GenerateKey, SaveKeys, LoadKeys) in the assignment. We added several helper functions under LoadKeys(), their main purposes are building UI (BuildUIBox), initiating and querying database password (GetDBSecurePassword), calculate padding (Unpadding, Padding), and implement the nounce-based counter mode (CTRAESDecript, CTRAESEncript). It's easy to see the documentation in the code to learn what they do.
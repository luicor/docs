# Seobinggo

Seobinggo is P2P backup software for Seattle.   It backs up files on other user machines that run Seobinggo.

This software was developed by Yoon Hong Song: hys235@cs.washington.edu

## LICENSE
Legal Statement:

Copyright (c) 2009 The University of Washington

Permission is hereby granted, free of charge, to any person obtaining a copy ofthis software
and/or hardware specification (the "Work") to deal in the Work without restriction, including
without limitation the rights to use, copy, modify, merge, publish, distribute,sublicense, and/or
sell copies of the Work, and to permit persons to whom the Work is furnished todo so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included in all copies or
substantial portions of the Work.

THE WORK IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE WORK OR THE USE OR OTHER DEALINGS
IN THE WORK.


## Running Seobinggo
1.Install/Setup


        1. Download and install Seattle.
           ```https://seattleclearinghouse.poly.edu/download/flibble/```

        b. Untar the package
                ```tar -zxvf Seobinggo.tar.gz```

        c. Copy the files in Seobinggo to the ```seattle/seattle_repy``` directory

        d. Enter the ```seattle/seattle_repy``` directory

2. Run Seobinggo
        ```python repy.py restrictions.default Seobinggo.repy```

3. Using Sebinggo

        1. Point your webbrowser at ```127.0.0.1:12345```

        b. Now you can use the User Interface to backup local files to peers.


## Known Issues & Limitation

1. File size bigger than 3MB will not be stored in peers because recvAll()
   does not work correctly. Once recvAll() works correctly, Seobinggo should
   backup any file in any size.

2. Privacy/Security.
   Seobinggo uses RSA encryption to protect backup files in peers. However,
   current encryption policy does not guarantee full securty of backup files
   in many reasons.

        1. Confidentiality - Before sending backup file to peers, Seobinggo encrypt
           the data with the user's public key(RSA). This way, anyone without matching
           private key will not be able to read the original file.

        b. Integrity - When Seobinggo backup a file, it records version information
           corresponding to the file. Anyone with the same public key will be able
           to backup a file under the public key and a specific file name.

        c. Availability - Any backup file is available to any user that has thesame
           public key. Although the file data is encrypted with public key, this is
           not ideal security policy.

## Improvement & Schedule

1. Security
   SHA1 will be adopted to improve the security of the system. As before, file data
   will be encrypted with user's public key(RSA). Then, a hash value will be 
   calculated by SHA1(the file data).  Instead of storing only encrypted file data in 
   peers, the encrypted hash value(with user's private key) will be stored in peer 
   nodes.  This way, hash value can be compared when retrieval request received in peer
   nodes to check the user has the correct private key. This is possible because 
   Seobinggo stores encrypted hash values(with private key) in peer node and this can 
   be decrypted to compare with SHA1(file data) which returns hash value.

2. UI
   User interface is very important. It will be updated soon.


## Challenge Info
They've been trying to breach our infrastructure all morning! They're trying to get more info on our covert kangaroos! We need your help, we've captured some traffic of them attacking us, can you tell us what tool they were using and its version?

## Work
Using the `strings` tool to filter out strings from the packet capture file, I found Nikto v2.1.6 written in some of the requests. It is a tool which is used for discovering vulnerabilities in web applications.
So, if this is the tool used, then the flag can be DUCTF{nikto_2.1.6}


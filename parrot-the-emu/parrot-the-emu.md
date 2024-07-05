## Challenge Writeup: "Parrot the Emu"

### Challenge Description
The challenge is titled "Parrot the Emu," and the hint provided is, "It is so nice to hear Parrot the Emu talk back." This challenge involves exploiting a Server-Side Template Injection (SSTI) vulnerability to retrieve the flag from a vulnerable web application.

### Vulnerability Explanation
SSTI is a web security vulnerability that occurs when user input is embedded in templates and rendered by the server without proper sanitization. This can allow an attacker to inject malicious template code, leading to remote code execution, data exfiltration, or other malicious activities.

### Exploitation Steps

1. **Identifying the Vulnerability:**
   - The challenge hint suggests interaction with a template engine, which is a strong indicator of a potential SSTI vulnerability.
   - By injecting specific payloads into the input fields or URL parameters and observing the application's response, we can confirm the presence of SSTI. (Additional can be taken from : https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection)

2. **Constructing the Payload:**
   - The payload is designed to exploit the `get_flashed_messages` function, which is commonly used in Flask applications to display messages to the user.

3. **Retrieving the Flag:**
   - The command to retrieve the flag is: `{{ get_flashed_messages.__globals__.__builtins__.open("./flag").read() }}`.
   - This payload works by:
     - Accessing the `get_flashed_messages` function's global scope.
     - Navigating to the `__builtins__` module, which contains built-in functions and variables.
     - Using the `open` function to open the `flag` file located in the current directory.
     - Reading the contents of the flag file.

### Flag
Upon successful exploitation, the application will display the flag:
```
DUCTF{PaRrOt_EmU_ReNdErS_AnYtHiNg}
```

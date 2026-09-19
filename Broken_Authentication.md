Task — 1

In cybersecurity, authentication is the process of verifying that a user, device, or system is really who or what it claims to be before granting access.

Simple example
When you log into a website:

You enter a username.
You enter a password.
The server checks whether the credentials match its records.
If they do, you are authenticated and granted access.
Authentication vs Authorization
People often confuse these:

Authentication = “Who are you?”
Authorization = “What are you allowed to do?”
Common Authentication Mechanisms
Password authentication
MFA / 2FA
Session cookies
OAuth (e.g., “Login with Google”)
SSO (Single Sign-On)
Biometric authentication
API keys and tokens
Why Authentication Matters in Web Security
Many web vulnerabilities target authentication systems, including:

Username enumeration
Credential stuffing
Password brute forcing
Authentication bypass
Weak password reset flows
Session hijacking
Cookie manipulation
In this room we will ffuf(Fuzz Faster U Fool!) command.

You may get confused between gobuster and ffuf like I did, so I will attaching a screenshot I found on google for the comparision.

Press enter or click to view image in full size

Task — 2

Press enter or click to view image in full size

1. Username Enumeration
What it is:
Finding out which usernames/accounts exist on a system.

Why it’s dangerous
Once valid usernames are known, attackers can focus attacks on real accounts instead of guessing blindly.

Typical indicators
Different error messages
Different response times
Different password reset responses
Output
A list of valid usernames/accounts.

2. Credential Brute Force
What it is:
Trying many password combinations against valid usernames until one works.

Common forms
Password Spraying
Many accounts + one common password.

Credential Stuffing
Using usernames/passwords leaked from other breaches.

Why it works
Many people:

Reuse passwords
Choose weak passwords
Never enable MFA
Output
A working username/password pair.

3. Logic Flaws
What it is:
Abusing mistakes in the authentication workflow rather than guessing credentials.

This is often the most interesting category for penetration testers.

Why it works
Developers assume users will follow the intended sequence of steps.

Attackers intentionally break that sequence.

Output
Account access without knowing credentials.

4. Cookie Manipulation
What it is:
Modifying cookies or session data used by the application.

Output
Higher privileges or access to another account.

Task — 3

Username Enumeration (Simple Explanation)
Username enumeration is the process of finding out which usernames or email addresses are registered on a website.

Think of it like this:

You try to sign up with different usernames:

admin → Website says: "Username already exists"
random12345 → Website says: "Account created successfully"
From these different responses, you learn that admin is a real account and random12345 is not.

Why attackers do it
Before trying to guess passwords, attackers want to know which accounts actually exist.

Instead of guessing:

admin, john, alice, bob

and not knowing whether they’re real, they first identify valid usernames and then focus only on those accounts.

Where it commonly happens
Signup forms
“Username already exists”
Login forms
“User not found”
“Wrong password”
Password reset forms
“Email not registered”
How ffuf helps
ffuf automates the process.

Become a Medium member
Instead of manually testing hundreds of usernames, it:

Takes a wordlist of names.
Sends each one to the signup page.
Looks for a specific response such as:
username already exists

4. Prints only the usernames that trigger that response.

Example:

admin, john, alice

These are likely real accounts.

Press enter or click to view image in full size

Now we will save these usernames for finding the passwords using ffuf in the next task.


Press enter or click to view image in full size

What is the username starting with si*** ?

simon

What is the username starting with st*** ?

steve

What is the username starting with ro**** ?

robert

Task — 4

Credential Brute Force (Simple Explanation)
After finding valid usernames through username enumeration, the next step is often credential brute forcing.

The idea is simple:

You have a list of real usernames.
You have a list of common passwords.
You try every username with every password until one works.
How do you know when you succeed?
The tool needs a success signal.

Press enter or click to view image in full size

What is the valid username and password (format: username/password)?

steve/thunder

Task — 5

Logic Flaws
A logic flaw happens when an application behaves in a way the developer didn’t expect, allowing a user to bypass security without hacking, SQL injection, or malware.

You can follow all the steps from the room to get the answer of the question.

What is the flag from Robert’s support ticket?

THM{AUTH_BYPASS_COMPLETE}

Cookie Manipulation (Simple Explanation)
Websites need a way to remember that you’ve logged in.

Since HTTP is stateless, the server uses cookies:

Set-Cookie: session=abc123

Your browser stores the cookie and sends it back with every request:

Cookie: session=abc123

The server then knows who you are.

The Vulnerability
A website becomes vulnerable when it trusts information stored in the cookie.

Instead of storing:

session=abc123

it stores:

logged_in=true
admin=false

and blindly trusts those values.

1. Plain Text Cookies
Example:

Cookie: logged_in=true; admin=false

The server reads:

logged_in=true → User is logged in
admin=false → User is not admin

But the attacker can simply change:

Cookie: logged_in=true; admin=true

Now the server thinks:

Logged in
Admin privileges

because there is no protection.

Why it fails
The cookie contains the authorization decision itself.

The server should be making that decision, not the client.

2. Hashed Cookies
A hashed cookie stores a hash value instead of the original data.

The server applies a hash function to some data and stores the resulting hash in the cookie.
Hashing is a one-way process: you can generate the hash from the data, but you cannot directly recover the data from the hash.
Some developers mistakenly assume that hashing makes a cookie secure against tampering.
However, a hash by itself does not prove authenticity because anyone who knows the original value can generate the same hash.
A hash provides integrity checking only when combined with a secret (e.g., HMAC), not when used alone.
3. Encoded Cookies
An encoded cookie stores data in an encoded format rather than plain text.

Encoding transforms data into a different representation so it can be safely transmitted or stored.
The transformation is fully reversible.
Encoding is designed for compatibility and transport, not for security.
Anyone who can read the cookie can usually decode it, modify the contents, and encode it again.
Common encoding schemes include Base64 and Base32.
What is the flag from changing the plain text cookie values?

THM{COOKIE_TAMPERING}

What is the value of the md5 hash 3b2a1053e3270077456a79192070aa78 ?

Press enter or click to view image in full size

463729

What is the base64 decoded value of VEhNe0JBU0U2NF9FTkNPRElOR30= ?

Press enter or click to view image in full size

THM{BASE64_ENCODING}

Encode the following value using base64 {“id”:1,”admin”:true}

Press enter or click to view image in full size

eyJpZCI6MSwiYWRtaW4iOnRydWV9

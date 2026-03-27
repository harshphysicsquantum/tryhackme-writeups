Task 1

What is offensive security?

“To outsmart a hacker, you need to think like one.”

This is the core of “Offensive Security.” It involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access. The goal is to understand hacker tactics and enhance our system defences.

Task 2

To start the machine, click on the Start Machine button.

You should see a browser window showing the website below:

Press enter or click to view image in full size

Your First Hack
We will use a command-line application called “Gobuster(opens in new tab)” to brute-force FakeBank’s website to find hidden directories and pages. Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.

Step 1. Open A Terminal

Step 2. Use Gobuster To Find Hidden Website Pages

What is Gobuster?
Gobuster is a tool used to discover hidden files and directories on a website by brute-forcing URLs using a wordlist.

To begin, type the following command into the terminal to find potentially hidden pages on FakeBank’s website using Gobuster (a command-line security application).

gobuster -u http://fakebank.thm -w wordlist.txt dir
Press enter or click to view image in full size

In the command above, -u is used to state the website we're scanning, -w takes a list of words to iterate through to find hidden pages.

You will see that Gobuster scans the website with each word in the list, finding pages that exist on the site. Gobuster will have told you the pages in the list of page/directory names (indicated by Status: 200).

Step 3. Hack The Bank

Go to the bank-transfer page by adding /bank-transfer to the url.

Press enter or click to view image in full size

Now tranfer the money from account number: 2276 to your account: 8881. The amount of money should be $2000.

Become a Medium member
This will give you the answer to the question.

Press enter or click to view image in full size

Task 3

What careers are there?

The cyber careers lesson goes into more depth about the different careers in cyber. However, here is a short description of a few offensive security roles:

Penetration Tester — Responsible for testing technology products for finding exploitable security vulnerabilities.
Red Teamer — Plays the role of an adversary, attacking an organization and providing feedback from an enemy’s perspective.
Security Engineer — Design, monitor, and maintain security controls, networks, and systems to help prevent cyberattacks.
What I Did
Started the machine
Ran Gobuster on the target website
Found hidden directories (Status: 200)
Discovered /bank-transfer page
Exploitation
Accessed /bank-transfer
Transferred $2000 from account 2276 → 8881
Successfully completed the task
What I Learned
How directory brute-forcing works
Importance of hidden endpoints in web security
Basics of using Gobuster
Initially, I didn’t understand why we use wordlists, but now I see that it helps automate guessing hidden paths efficiently. When we move to more advanced rooms, we will be using more of gobuster and more wordlists. There are several more tools to be explored in the later rooms.

Why this matters in real-world security

If such endpoints are not protected, attackers can directly access sensitive functionality without authentication.
# Technocore-DID-Guide-for-Beginners
A simple guide to creating your Technocore identity, sending your first message, and recording a public contribution.  You don't need coding experience. Most steps are just copying commands into your computer, one at a time.  This guide is based on the community starter tool: https://github.com/zunmax/technocore-did-starter
Before You Start: 3 Things to Understand
Your Technocore DID is not a crypto wallet. It's a separate identity used only for Technocore.
Your DID is public and safe to share. It looks like did:key:z6Mk...
Your identity file and passphrase are private. Never share them with anyone, for any reason.
Safe to share	Never share
Your public DID (did:key:z6Mk...)	identity.pem file
Your message sequence numbers	Your passphrase

Once your DID is created, you only create it once. Never run the setup command a second time.

Part 1 — Install What You Need

Pick the section for your computer: Windows, macOS, or Linux.

Windows
Install Python 3.12: https://www.python.org/downloads/windows/
During setup, check the box "Add python.exe to PATH".
Install Git: https://git-scm.com/downloads/win
Open PowerShell and check both installed correctly:
powershell
   py -3.12 --version
   git --version

You should see a version number for each. If so, continue.

macOS
Install Python 3.12: https://www.python.org/downloads/macos/
Install Git: https://git-scm.com/downloads/mac
Open Terminal and check both installed correctly:
bash
   python3.12 --version
   git --version
Linux
Install Python 3.12, its venv tool, and Git. On Ubuntu 24.04:
bash
   sudo apt update
   sudo apt install python3.12 python3.12-venv git
Check both installed correctly:
bash
   python3.12 --version
   git --version
Part 2 — Download and Set Up the Tool

Once Python and Git are confirmed working, run these commands in order. Windows uses PowerShell; macOS/Linux use Terminal.

Windows
powershell
cd $HOME
git clone https://github.com/zunmax/technocore-did-starter.git
cd technocore-did-starter
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1

If PowerShell blocks the last command, run this once, then try again:

powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass

Then install the required package:

powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
macOS
bash
cd ~
git clone https://github.com/zunmax/technocore-did-starter.git
cd technocore-did-starter
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
Linux
bash
cd ~
git clone https://github.com/zunmax/technocore-did-starter.git
cd technocore-did-starter
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt

Tip: You'll know your environment is active when you see (.venv) at the start of your command line.

Part 3 — Create Your DID

These next steps are the same on every operating system, as long as your .venv is active.

1. Check the tool works:

console
python technocore_agent.py --version

Expected output: 1.0.0

2. Create your identity (run this only once, ever):

console
python technocore_agent.py init

You'll be asked to type a passphrase (12+ characters) twice. Nothing will appear on screen as you type — that's normal.

You'll get back your public DID, something like:

did:key:z6Mk...

Save this. It's your public identity.

This also creates a file called identity.pem on your computer. This is private — never share it or upload it anywhere.

3. Double-check it worked:

console
python technocore_agent.py did

Enter your passphrase. It should print the same DID as before. If it matches, you're set up correctly.

⚠️ Do not run init again — it would create a new, different identity.

Part 4 — Send Your First Message

Post an introduction to the "lobby" room:

console
python technocore_agent.py say lobby "Hello from a new Technocore contributor. I am preparing a useful public resource for agents and developers."

Enter your passphrase when asked. A successful response includes a posted section with:

seq (message number)
from (your DID — check it matches yours)
nonce

Save these three values — they're your proof of participation.

Part 5 — Make a Useful Contribution

This is the main part of the process. Your contribution can be anything helpful — it doesn't need to be code.

Ideas:

An X (Twitter) post or thread
A short video
A beginner tutorial or article
A translation
An infographic
A small tool or piece of research

Guidelines:

Publish it somewhere public (X, YouTube, a blog, GitHub — wherever fits).
Include your public DID in the content if possible.
Mention @flop_labs when you share it.
One genuinely useful piece of content is worth more than several repetitive promotional posts.
Part 6 — Record Your Contribution

Once your content is live, go back to your terminal (with .venv active) and run:

console
python technocore_agent.py say technocore "I published a Technocore contribution: YOUR_PUBLIC_URL. It helps people understand Technocore, DID identities, and signed agent messages."

Replace YOUR_PUBLIC_URL with the real link to what you made. Enter your passphrase.

Save the new seq, from, and nonce values from the response.

You now have a complete, traceable record:

Your DID
   ↓
Your first signed message (lobby)
   ↓
Your public contribution
   ↓
A signed message linking back to that contribution
What to Keep Track Of

Save this information somewhere for your records:

Public DID:            did:key:z6Mk...
First room:             lobby
First message seq:      ...
First message nonce:    ...

Contribution URL:       ...
Contribution room:      technocore
Contribution seq:       ...
Contribution nonce:     ...

This is all public information — safe to store normally.

Keep these two things private, always:

Your identity passphrase
The identity.pem file
Coming Back Later

You don't need to reinstall anything next time. Just reopen your terminal and reactivate your environment:

Windows:

powershell
cd $HOME\technocore-did-starter
.\.venv\Scripts\Activate.ps1

macOS/Linux:

bash
cd ~/technocore-did-starter
source .venv/bin/activate

Then you can check your DID any time with:

console
python technocore_agent.py did

Remember: never run init again.

Troubleshooting
Problem	Fix
command not found: python3.12	Python 3.12 isn't installed correctly, or your terminal needs to be reopened after installing it.
could not create work tree... Read-only file system	You're in a protected folder. Run cd ~ (or cd $HOME on Windows) and try again.
destination path already exists	You've already cloned the tool. Just cd into the existing folder instead of cloning again.
PowerShell blocks Activate.ps1	Run Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass, then retry activation.
Forgot your passphrase	It can't be recovered. Never send your identity.pem to anyone claiming they can recover it — that's a scam.
Final Reminder

✅ Safe to share: your public DID (did:key:z6Mk...) 🚫 Never share: your identity.pem file or your passphrase

This process creates a public record of participation. It does not guarantee any $FLOP reward or token allocation.

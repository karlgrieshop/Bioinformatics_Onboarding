```
#     ____        __                           
#    / __ \____ _/ /_____ _                    
#   / / / / __ `/ __/ __ `/                    
#  / /_/ / /_/ / /_/ /_/ /                     
# /_____/\__,_/\__/\__,_/                      
#   / ___/_____(_)__  ____  ________           
#   \__ \/ ___/ / _ \/ __ \/ ___/ _ \          
#  ___/ / /__/ /  __/ / / / /__/  __/          
# /____/\___/_/\___/_/_/_/\___/\___/           
#   ____ _____  ____/ /                        
#  / __ `/ __ \/ __  /                         
# / /_/ / / / / /_/ /                          
# \__,_/_/ /_/\__,_/_       ____               
#    / __ )(_)___  (_)___  / __/___  _____     
#   / __  / / __ \/ / __ \/ /_/ __ \/ ___/_____
#  / /_/ / / /_/ / / / / / __/ /_/ / /  /_____/
# /_____/_/\____/_/_/ /_/_/  \____/_/          
#    ____ ___  ____ _/ /_(_)_________          
#   / __ `__ \/ __ `/ __/ / ___/ ___/          
#  / / / / / / /_/ / /_/ / /__(__  )           
# /_/ /_/ /_/\__,_/\__/_/\___/____/            
```

# Data Science and Bioinformatics Onboarding

Welcome to Data Science and Bioinformatics (BIO-7051B)! 

Complete this tutorial before the Day 1 (February 4, 2025). 

It should take you about two hours.

---


## Table of Contents

1. [Preamble](#Preamble)
2. [Key Concepts & Tools](#key-concepts--tools)
3. [GitHub account](#GitHub-account)
4. [VS Code](#VS-Code)
5. [Git (Git Bash)](Git-(Git-Bash))
6. [Copilot Command Line tutorial](#Copilot-Command-Line-tutorial) 
7. [SSH Keys](#SSH-Keys)
8. [HPC](#HPC)



---

## Preamble

**Part 8 of this tutorial ([HPC](#HPC)), and Day 1 of your Bioinformatics module (February 4, 2025), require:** 
- A UEA username and email address, 
- The [multi-factor authenticator (MFA)](https://www.uea.ac.uk/about/university-information/it-information/mfa), 
- The [GlobalProtect VPN](https://my.uea.ac.uk/divisions/it-and-computing-services/service-catalogue/network-and-telephony-services/vpn-services/global-protect-on-windows), 
- And an account for you on UEA's High Performance Computing cluster (HPC) "Hali", which I have set up for all students registered to this module.

If you are having trouble with your username, email, MFA, or VPN contact [UEA IT Service Desk](https://www.uea.ac.uk/about/university-information/it-services/it-service-desk).

If you are missing any of the above, you can still do the large majority of this tutorial. Proceed below, and sort out the rest with UEA IT Service Desk (link above) prior to Day 1 (February 4, 2025). 

---

## Key Concepts & Tools

### Files vs Folders (Directories)

- **File:** A file is a single item that stores data, such as a document, image, script, or dataset. Example: `notes.txt`, `script.sh`, `data.csv`.
- **Folder (Directory):** A folder (or directory) is a container that holds files and/or other folders. Folders help organize your files. Example: most of you have a `Documents/` folder on your local machine, where a slash "/" indicates that something could be stored within it.
- **Path:** A path shows the location of a file or folder in the filesystem. Example: if Sally's `notes.txt`, `script.sh`, and `data.csv` were all in her `Documents/` folder, which is next to her `Desktop/` folder under the username `Sally/`, like so: 
  ```
  /
  └── Users
      └── Sally
          ├── Desktop
          └── Documents
              ├── notes.txt
              ├── 👉 script.sh 👈
              └── data.csv
  ```
  Then the path to the path to `script.sh` would be: `/Users/Sally/Documents/script.sh`. 

- **The $PATH** You don't need to know it for this tutorial, but just in case your Google search gets you down the wrong rabbit hole, "The $PATH" is not "a path" — "The $PATH" is a special environment variable in Unix-like systems that stores a list of directories that will be searched before anything else so that you can, e.g., call a program from anywhere without having to type out the path to the program. 

### Command Line, Script, and Text Editor

- **Command Line (Terminal, Shell):** The empty box with a cursor. An interface where you type commands to interact with your computer (instead of pointing and clicking with a mouse). You can navigate folders, run programs, and manage files directly by typing commands.
- **Script:** A text file containing a series of commands that can be executed by the computer (e.g., a `.sh` bash script). Scripts are used to automate tasks. Note: In RStudio, you may be used to running scripts one line at a time, but in the command line, scripts are usually run all at once from start to finish.
- **Text Editor:** A program for creating and editing text files (including scripts). Examples: VS Code (recommended, intallation instrcutions below), Notepad, BBedit, nano, vim.


### Local vs Remote Work

- **Local:** Working directly on your own computer (laptop or desktop). All files and programs are on your machine.
- **Remote (HPC via SSH):** Connecting to a powerful remote computer (High Performance Computing cluster) using SSH (Secure Shell) from your terminal. You type commands on your local terminal, but they run on the remote cluster of compute nodes. This is useful for large analyses that require more resources than your local computer.

### Note on Shells and Syntax Differences

- **Linux:** The default shell is usually `bash`, but could also be `zsh` or others. Most HPCs systems are Linux-based and use `bash` or similar shells.
- **Mac:** The default shell is usually `zsh` (or sometimes `bash`). Mac is a Unix-based OS, so terminal commands and syntax are very similar to those used on most HPC systems.
- **Windows (PC):** You will NOT use the default Windows shell (PowerShell or Command Prompt) becasue their syntax is different from bash/zsh and many basic Unix commands (like `ls`, `cp`, `mv`, `grep`) will not work the same way, or at all. INSTEAD you will use Git Bash (more on that below).
  - If you insist on sticking with Powershell, you'll commonly have to google alternatives, e.g.:
    - Unix: `ls` (list files) → PowerShell: `dir` or `ls` (aliased, but not always identical)
    - Unix: `cp file1.txt folder/` (copy `file1.txt` into `folder/`) → PowerShell: `Copy-Item file1.txt folder/`
    - Unix: `mv file1.txt folder/` (move `file1.txt` into `folder/`) → PowerShell: `Move-Item file1.txt folder/`
    - Unix: `cat file.txt` (view `file1.txt`) → PowerShell: `Get-Content file.txt`

---

## GitHub account
You were provided a link to [this tutorial](https://github.com/karlgrieshop/Bioinformatics_Onboarding) that you're reading now through Blackboard and email, and that link brought you here to a website called GitHub, a forum for sharing code. If you don't already have a GitHub account, start a free GitHub account using your university email address by clicking [here](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home). If you already have a GitHub account, log in.

After starting an account and logging in, find your way back to [this tutorial](https://github.com/karlgrieshop/Bioinformatics_Onboarding) and continue to the next step. 

---

## VS Code 

A text editor is where you write code - it's like MS Word, but for code. 

We recommend using VS Code as your text editor **and** your terminal. 

**Download and setup VS Code:**

- **Windows users**, first install [Git for Windows](https://git-scm.com/download/win) first.
- Then, **everybody** [Download VS Code](https://code.visualstudio.com/Download).

  **Installation Tips:**
- Accept all default options during installation.
- **Do not uncheck “Add to PATH”.**
- Let VS Code register as the default editor for supported files (like .txt, .md, .sh, .py, etc.).
- It should have installed the “GitHub Copilot” extension, but if not, do that. 
- Sign in with your GitHub account.
- If VS Code asks whether you trust the workspace, click “Yes”.
- [Getting started with VS Code](https://code.visualstudio.com/docs/introvideos/basics)

This tutorial that you're reading, if you're still reading it on GitHub, is actually a README.md script, where the `.md` file extension stands for "mark down" and GitHub repositories automatically mark down a `README.md` script into this fancy readable format you see in front of you. 

To see the raw `README.md` script,  scroll all the way back up to the top of this repository where its contents are listed and click the `README.md` file, or click this [shortcut](https://github.com/karlgrieshop/Bioinformatics_Onboarding/blob/main/README), and find your way back to this place in the tutorial using Ctl+f (or Cmd+f) to search for the term *monkey*. 

OK, you're now looking at the raw `README.md` script in its online repository on GitHub.com. This is what mark down code looks like on the inside. 

Now, download the `README.md` script by clicking the little download arrow button in the top right corner, save it somewhere on your local machine that you can remember, open it in VS Code, and find your way back to this place in the tutorial using the search term *crocodile*.

You should now be looking at this `README.md` script in VS Code.

If it opens in a different program (e.g. Notepad), that's because you have a different text editor set as the default for files with a `md` extension. There are various ways to fix that issue, [here are some](https://letmegooglethat.com/?q=How+do+I+make+VS+code+my+default+text+editor).  

You will need to get familiar with your computer, how to adjust default settings, where files are stored when you download them, and how to Google your question when you hit a snag.

If you still can't open a file in VS Code, here's a work-around: In the VS Code menu bar click `File` → `New File...` and create a new file called `README.md`, and copy and past the entire contents of the raw `README.md` script as you see it [here](https://github.com/karlgrieshop/Bioinformatics_Onboarding/blob/main/README) into your new `README.md` file in VS Code, save, and find your way back to this place in the tutorial again. 

### VS Code terminal

Lastly, in VS Code, in the menu bar in the top click `Terminal` → `New Terminal` to open a terminal window in VS Code. (*If your screen got split in half horizontally, just click `zsh`, `Bash`, `Git Bash` or `Powershell` → `Move Terminal to Editor Area` for a better experience.*) 

**Windows users**
If the terminal opens as `Powershell`, click the dropdown arrow in the terminal tab and select `Git Bash` (**Git Bash** should be there if you installed **Git for Windows**, above). I recommend setting `Git Bash` as your default shell: click the dropdown arrow again and choose **Select Default Profile…**, then choose **Git Bash**. 

**Mac and Linux users**
For Mac and Linux users I sugest setting `zsh` as your default shell, but `Bash` is fine, too. 

I like to slide my terminal session tab(s) all the way over the left and scripts to the right to keep things organised (click and drag the tabs like you would your web browser).

You should now have two tabs open in VS Code: a terminal shell tab and the `README.md` script.

Congrats!

---

## GitHub Copilot
GitHub Copilot is built into VS Code, as well as built into GitHub - you're going to use both to prompt your way through a self-guided commandline tutorial that will simultaneiously teach you how to navigate your machine and how to optimise GitHub Copilot's value.

### GitHub Copilot in VS Code
In VS Code, at the top, just to the right of the search bar, is the little Copilot chat icon, click the drop down and select **Open Chat** to pop out the Copilot chat bar to the right side of your VS Code session.

**Side-bar "Ask" versus "Edit"**
In the bottom of that bar is your chat prompt window, where you can toggle between `Ask` and `Edit` (and perhaps also `Agent`, which we will not use). In `Ask` mode you will get answers there in the chat bar only, while `Edit` mode gives Copilot permission to directly impliment changes to scripts you've attached with tracked changes that you can later accept or reject. You can also toggle among different language models (i.e. GPT, Claude Sonnet, etc.). 

**Self-guided command line tutorial**
Toggle the chat prompt window to `Edit` mode and attach this `README.md` script to the conversation by dragging the `README.md` tab down into the chat bar. `README.md` **must** be listed as as one of the attachments in your chat for the next step to work. 

Modify the prompt below to your personal machine (e.g. Windows, Mac, Linux) and your skill level (e.g. novice, intermediate, erexpert), and copy and past it into the chat bar:

"
This `README.md` file is a bioinformatics tutorial. It is important that you do not modify it outside of the specific permission I'm granting you. Please insert a self-guided command-line tutorial tailored to my specific learning needs in between the "*Elephant*" and "*Tiger*" of this `README.md` script. I want the tutorial to take me about 10 minutes, and I want it cover the basics of navigating directories in my terminal, tabbing into commands, identifying my current working directory, making new directories, making new files, copying files, and moving files. You can assume I've read everything above "*Elephant*" this `README.md` script, hence, I'm using VS Code, I have a terminal tab open, I have this `README.md` script open. You only type the essentials in between the "*Elephant*" and "*Tiger*" of this `README.md` script, and I know how to ask for further clarification in Copilot chat bar on side. Lastly, my current command line skill level is *[insert skill level]* and my operating system is *[Windows or Mac or Linux]*.  
"

Ok, so modify, copy, and past that prompt (above) into the chat bar on the side, and see how it goes. If it doesn't produce what you were aiming for, reject the change and try again. When you get what you want, accept the changes to the script, **save the changes**, do your 10-Minute Command Line Tutorial and then move on.

*Elephant*

*Tiger*

**Now that you're finished editing/modifying the README.md script**
I'd like to show you that you can view this `README.md` script in its clean, marked down version, the way it would look on GitHub website, right here in VS Code by either finding the buttons and clicking them, or using these keyboard shortcuts:
**As a new tab (my preference)**
Windows/Linux: Ctrl+Shift+V
Mac: Cmd+Shift+V
**Or side-by-side**
Windows/Linux: Ctrl+K V 
Mac: Cmd+K V  

You can't edit these preview modes, but they might softer on your eyes for following the remainder of the tutorial from within VS Code.

**Now that you can use the terminal**
Check if you have git installed by running this command in your terminal:

```
git
```

If you see usage instructions, then `git` is already installed (great!), then you're done with this step.

But if you get an error, [download and install git here](https://git-scm.com/downloads) choosing the correct version for your operating system and choosing the default intallation options.

You will need `git` for the next step.

### GitHub Copilot on GitHub.com

Go to the main page of [this tutorial](https://github.com/karlgrieshop/Bioinformatics_Onboarding) on GitHub and click the GitHub Copilot chat icon in the top right.

**Attach GitHub repositories, scripts, local files, etc.**  
The karlgrieshop/Bioinformatics_Onboarding repository should be attached automatically, but if not, attach it by clicking the "+" icon in the chat prompt area and selecting **Repositories** and finding karlgrieshop/Bioinformatics_Onboarding. 

Attach a local file, specifically, your modified `README.md`, by clicking the "+" icon in the chat prompt area and selecting **Upload from computer** and finding your file modified `README.md`.

Now, write your own detailed prompt in the Copilot chat on GitHub.com, with the repo and your personalized `README.md` attached as context, asking for step-by-step instructions to fork the karlgrieshop/Bioinformatics_Onboarding repo to your GitHub account, clone it to your local machine.
**Prompting tips**
 - Use the word "fork".
 - Use the word "clone"
 - Clone with git and the HTTPS link.
 - Think about where you want to clone the repo on your local machine.
    - Design the directory names and orgnisation logically 
    - Navigate to that directory before running your `git clone` line.
 - Ask Copilot if you don't know what these words mean.
 - Then put some time into a thorough prompt.

Go!

---

## Command Line Basics (local)

Ok, so you should now have a modified local copy of `README.md` that you downloaded earlier (probably the one you're looking at now), **AND** a local copy of the full Bioinformatics_Onboarding/ GitHub repo, with the following structure:

```
Bioinformatics_Onboarding/
├── README.md
├── LICENCE
├── GitHub_tutorial/
│   ├── GitHub_CheatSheet.md
│   └── GitHub_tutorial.md
└── Unix_help/
    └── Unix.Cheat.Sheet.txt
```

Navigate around your terminal to identify those two alternative versions of the `README.md` script in their two distinct locations on your machine, as well as the remaider of your cloned copy of the Bioinformatics_Onboarding/.

**Modify the cloned repo (don't be shy)**

Using terminal commands that taught yourself above (between the large animal and striped animal), modify your cloned copy of the Bioinformatics_Onboarding/ repository on your local machine to incorporate your new version of the `README.md` script in a way that seems logical to you. 

**Relax**, it's your local copy (cloned repo) of a copy (forked repo) of a public resource - you can always start over from the original. Go wild. Organise it how you wish.

For example, you could overwrite the original with:
 
```
# Note phrases like "path/to/your" are generic helper phrases - modify accordingly.
# Also note this line will overwrite without asking permission.
cp path/to/your/modified/README.md path/to/your/Bioinformatics_Onboarding/
```

Or perhaps its safer to create a new sub-directory for it, e.g.:

```
mkdir path/to/your/Bioinformatics_Onboarding/My_work/
```
```
cp path/to/your/modified/README.md path/to/your/Bioinformatics_Onboarding/My_work/
```

When you're satisfied with your changes, we'll push your changes to your forked copy of the repo on your GitHub account so that these changes are documented. 

But before you can push changes from your local machine to your GitHub account, you need to set up your authentication. After all, we can't have just anyone pushing work to your profile! 

## SSH Keys

Setting up SSH keys allows you to securely push and pull code between your local machine and your GitHub repositories without entering your password every time. Follow these steps:

1. **Open your terminal in VS Code. Make sure you are in your home directory:**
   ```
   cd ~
   ```

2. **Check if you already have SSH keys:**
   ```
   ls -al ~/.ssh
   ```
   - If you see files like `id_rsa` and `id_rsa.pub` or `id_ed25519` and `id_ed25519.pub`, you may already have keys. If not, continue.

3. **Generate a new SSH key (recommended: ed25519):**
   ```
   ssh-keygen -t ed25519 -C "your_email@uea.ac.uk"
   ```
   - If you get an error about ed25519 not being supported, use:
     ```
     ssh-keygen -t rsa -b 4096 -C "your_email@uea.ac.uk"
     ```
   - When prompted for a file location, press Enter to accept the default.
   - You can set a passphrase or leave it empty.

4. **List your new SSH key files:**
   ```
   ls -al ~/.ssh
   ```
   - You should see `id_ed25519` and `id_ed25519.pub` (or `id_rsa` and `id_rsa.pub`).

5. **Display your public key (never share your private key!):**
   ```
   cat ~/.ssh/id_ed25519.pub
   ```
   - Copy the entire output (your public key).

6. **Add your SSH key to your GitHub account:**
   - Go to [GitHub SSH Keys settings](https://github.com/settings/keys).
   - Click **New SSH key**.
   - Paste your public key into the box, give it a title (e.g., "My Laptop"), and save.

7. **Test your SSH connection to GitHub:**
   ```
   ssh -T git@github.com
   ```
   - The first time, you may be asked to confirm the connection. Type `yes`.
   - If successful, you'll see a message like: "Hi USERNAME! You've successfully authenticated..."

8. **(Optional) If you have multiple keys or issues, ask Copilot for help or refer to [GitHub's SSH documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).**

You are now ready to push and pull code to and from your GitHub repositories using SSH!

---

## HPC

---

## Cheat Sheets

There are some bash language cheat sheets and random helpful code compilations in:

```
YOURNAME/OmicsCheatSheets/
```

Have a casual look through those before moving on so that you know where to look for help later on.

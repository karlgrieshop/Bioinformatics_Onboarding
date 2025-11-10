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

Complete this tutorial before the Day 1 (February 4, 2026). 

It should take you about two hours.

---


## Table of Contents

1. [Preamble](#Preamble)
2. [Key Concepts & Tools](#key-concepts--tools)
3. [GitHub Account](#GitHub-Account)
4. [VS Code](#VS-Code)
5. [Copilot Command Line Tutorial](#Copilot-Command-Line-Tutorial)
6. [SSH Keys](#SSH-Keys)
7. [Git and GitHub tutorial](#Git-and-GitHub-tutorial)
8. [HPC](#HPC)



---

## Preamble

**Part 8 of this tutorial ([HPC](#HPC)), and Day 1 of your Bioinformatics module (February 4, 2025), requires:** 
- A UEA username and email address, 
- A "Hali" account (UEA's High Performance Computing cluster (HPC)), **which I have already set up for all students registered to this module**,

**To access the Hali from a personal device, requires:**
- The [multi-factor authenticator (MFA)](https://www.uea.ac.uk/about/university-information/it-information/mfa), 
- The [GlobalProtect VPN](https://my.uea.ac.uk/divisions/it-and-computing-services/service-catalogue/network-and-telephony-services/vpn-services/vpn-for-non-managed-devices), 

**If you are having trouble with your username, email, MFA, or VPN, contact:** 
- [UEA IT Service Desk](https://www.uea.ac.uk/about/university-information/it-services/it-service-desk).

**UEA-managed devices**
- Should enable the full tutorial, but relevant notes along the way. 

If you are missing any of the above, proceed through as much of this tutorial as you can, and sort out the rest with UEA IT **prior** to Day 1 (February 4, 2025). 

---

## Key Concepts & Tools

### Files vs Folders (Directories)

- **File:** A file is a single item that stores data, such as a document, image, script, or dataset. Example: `notes.txt`, `script.sh`, `data.csv`.
- **Folder (Directory):** A folder (or directory) is a container that holds files and/or other folders. Folders help organize your files. Example: most of you have a `Documents/` folder on your local machine, where a slash "/" indicates that something could be stored within it.
- **Path:** A path shows the location of a file or folder in the filesystem. Example: if Sally's `notes.txt`, `script.sh`, and `data.csv` were all in her `Documents/` folder, which is next to her `Desktop/` folder under the username `Sally/`, like so, 
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
  then the path to the path to `script.sh` would be: `/Users/Sally/Documents/script.sh`. 

- **The $PATH** You don't need to know about the $PATH for this tutorial, but just in case your Google search gets you down the wrong rabbit hole, "The $PATH" is NOT the same as "a path" — "The $PATH" is a special environment variable in Unix-like systems that stores a list of directories that will be searched before anything else so that you can, e.g., call a program from anywhere without having to type out a path to the program. 

### Command Line, Script, and Text Editor

- **Command Line (Terminal, Shell):** The empty box with a cursor. An interface where you type commands to interact with your computer (instead of pointing and clicking with a mouse). You can navigate folders, run programs, and manage files directly by typing commands.
- **Script:** A text file containing a series of commands that can be executed by the computer (e.g., a bash script ends with the extension `.sh`). Scripts are used to automate tasks. 
- **Text Editor:** A program for creating and editing text files (including scripts) - it's like MS Word, but for code. Examples: VS Code (recommended, intallation instrcutions below), Notepad, BBedit, nano, vim.


### Local vs Remote Work

- **Local:** Working directly on your own computer (laptop or desktop). All files and programs are on your machine.
- **Remote (e.g. HPC):** Connecting to a powerful remote computer (High Performance Computing cluster), e.g., using SSH (Secure Shell) from your terminal. You type commands on your local terminal, but they run on a remote cluster of compute nodes. This is useful for large analyses that require more resources than your local computer.

### Note on Shells and Syntax Differences

- **Linux:** The default shell is usually `bash`, but could also be `zsh` or others. Most HPCs systems are Linux-based and use `bash` or similar shells.
- **Mac:** The default shell is usually `zsh` (or sometimes `bash`). Mac is a Unix-based OS, so terminal commands and syntax are very similar to those used on most HPC systems.
- **Windows (PC):** You will NOT use the default Windows shell (PowerShell or Command Prompt) becasue their syntax is different from bash/zsh and many basic Unix commands (like `ls`, `cp`, `mv`, `grep`) will not work the same way, or at all. **INSTEAD** you will use **Git Bash** (more on that below).
  - If you insist on sticking with Powershell, you'll commonly have to google alternatives, e.g.:
    - Unix (list files): `ls`  → PowerShell: `dir` or `ls` (aliased, but not always identical)
    - Unix (copy `file1.txt` into `folder/`): `cp file1.txt folder/`  → PowerShell: `Copy-Item file1.txt folder/`
    - Unix (move `file1.txt` into `folder/`): `mv file1.txt folder/`  → PowerShell: `Move-Item file1.txt folder/`
    - Unix (view `file1.txt`): `cat file.txt`  → PowerShell: `Get-Content file.txt`

---

## GitHub Account
You are viewing this tutorial on a website called GitHub, a forum for sharing code. If you don't already have a GitHub account [open this link in a new tab to start a free GitHub account](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home) using your UEA email address. If you already have a GitHub account, log in. If you've registered your account to a different email address, you may wish to change that to your UEA email. 

---

## VS Code  

I recommend using VS Code as your text editor **and** your terminal. 

**Download and setup VS Code:**

- **Windows users**, first install [Git for Windows](https://git-scm.com/download/win).
- If you cannot download/install **Git for Windows**, proceed with Powershell but mind the notes above about how you may need to Google alternative commands. We'll sort out your specific issue on Day 1.
- **Everybody**, if you haven't already done so, [Download VS Code](https://code.visualstudio.com/Download).

**Installation Tips:**
- Accept all default options during installation.
- **Do not uncheck “Add to PATH”.**
- Let VS Code register as the default editor for supported files (like .txt, .md, .sh, .py, etc.).
- It should have installed the “GitHub Copilot” extension, but if not, do that. 
- Sign in with your GitHub account.
- If VS Code asks whether you trust the workspace and you recognize the workspace as a directory on your local device, click “Yes”.
- For additional advice see, [getting started with VS Code](https://code.visualstudio.com/docs/introvideos/basics)

Ok, this tutorial that you're currently reading, if you're still reading it on GitHub, is actually a README.md script, where the `.md` file extension stands for "mark down," which GitHub will automatically render into this fancy readable format you see in front of you. 

To see the raw `README.md` script,  scroll all the way back up to the top of this repository where its contents are listed and click the `README.md` file, or here's a [shortcut](https://github.com/karlgrieshop/Bioinformatics_Onboarding/blob/main/README), and find your way back to this place in the tutorial using Ctl+f (or Cmd+f) to search for the term *monkey*. 

OK, you're now looking at the `README.md` script in its online repository on GitHub.com, either in `Preview` mode or `Code` mode (at the top).  

Now, download this `README.md` script by clicking the little download arrow button in the top right corner, save it somewhere on your local machine that you can remember, open it in VS Code, and find your way back to this place in the tutorial using the search term *crocodile*.

You should now be looking at this `README.md` script in VS Code.

If it opens in a different program (e.g. Notepad), that's because you have a different text editor set as the default for files with a `.md` extension. You'll have to figure that out.  

You will need to get familiar with your computer, how to adjust default settings, where files are stored when you download them, and how to Google your question when you hit a snag.

If you still can't open a file in VS Code, here's a work-around: In the VS Code menu bar click `File` → `New File...` and create a new file called `README.md`, and copy and past the entire contents of the raw `README.md` script as you see it [here](https://github.com/karlgrieshop/Bioinformatics_Onboarding/blob/main/README) into that new empty `README.md` file you just created in VS Code, save (Ctl+s or Cmd+s), and find your way back to this place in the tutorial again. 

### VS Code terminal

Ok, you've seen how we open scripts VS Code, now we'll open the terminal in VS Code. 

In the menu bar in the top click `Terminal` → `New Terminal` to open a terminal window in VS Code. (*If your screen got split in half horizontally, just click `zsh`, `Bash`, `Git Bash` or `Powershell` → `Move Terminal to Editor Area` for a better experience.*) 

**Windows users**
VS Code should use `Git Bash` as your terminl by default because you installed **Git for Windows** earlier, above. If it opened a `Powershell` terminal instead, click the dropdown arrow in the terminal tab and select `Git Bash`. I recommend setting `Git Bash` as your default shell: click the dropdown arrow again and choose **Select Default Profile…**, then choose **Git Bash**. 

I like to slide my terminal tab(s) all the way over the left and scripts to the right to keep things organised.

You should now have two tabs open in VS Code: a terminal tab and the `README.md` script.

Congrats!

---

## Copilot Command Line Tutorial
GitHub Copilot is built into VS Code, as well as built into GitHub.com. You'll use both to prompt your way through a self-guided command line tutorial, learning how to use the command line and how to use GitHub Copilot.

GitHub Copilot is AI-powered and can suggest code, commands, annotations, troubleshooting, or documentation as you type or as prompted. It works by analysing your current context and providing relevant suggestions, which you can accept, reject, or modify.

**Tips for GitHub Copilot**
- Depending on how you set up VS Code, it might be auto-completing lines or blocks of code. If you don't like that, or the suggestions are coming too fast, you can turn that off or delay the suggestions in the settings.
- Be descriptive in prompts (e.g. below). The clearer you are, the better suggestions Copilot can provide.
- You can toggle among the different large language models (LLMs) that it's basing its answers on (e.g. GPT-4, Claude Sonnet, etc.) – I have no specific advice in that area.
- Remember that Copilot is a tool to assist you. Always review, understand, and test the code it suggests.

### GitHub Copilot in VS Code
In VS Code, click the little Copilot chat icon at the top, just to the right of the search bar (or click the drop down and select **Open Chat**). The Copilot chat bar should open to the right side of your VS Code session.

**Side-bar "Ask" versus "Edit"**
In the bottom of that bar is your chat prompt window, where you can toggle between `Ask` and `Edit` (and perhaps also `Agent`, which we will not use). `Ask` mode gives answers in the chat bar only. But with `Edit` mode Copilot can impliment changes to scripts you attach, which you can accept or reject. You can also toggle among different language models (i.e. GPT, Claude Sonnet, etc.). 

**Self-guided command line tutorial**
Toggle the chat prompt window to `Edit` mode and attach this `README.md` script to the conversation by dragging the `README.md` tab down into the chat bar. `README.md` **must** be listed as as one of the attachments in your chat for the next step to work. 

Personalise the prompt below (e.g. length of time, operating system, skill level), then copy and past it into the chat bar prompt window:

"
This `README.md` file is a bioinformatics tutorial. It is important that you do not modify it outside of the specific permission I'm granting you. Please insert a self-guided command-line tutorial tailored to my specific learning needs in between the "*Elephant*" and "*Tiger*" of this `README.md` script. My current command line skill level is *[beginner, intermediate or advanced]*, my operating system is *[Windows, Mac or Linux]*, and I want the tutorial to take me about *[10, 20, or 30]* minutes. Be sure to cover the basics of navigating directories in my terminal, tabbing into commands, identifying my current working directory, making new directories, making new files, copying files, moving files, remomoving files, flags, and help documentation. You can assume I've read everything above "*Elephant*" in this `README.md` script, hence, I'm using VS Code, I have a terminal tab open, I have this `README.md` script open, and if I'm on a Windows machine I'm using [Git Bash or Powershell]. If this prompt still has multiple options in each set of brackets, return the following error: "Customise the prompt by editing within the brackets."   
"

Ok, so customise that prompt, copy and past it into the chat bar on the side in `Edit` mode, and watch the magic. If it doesn't produce what you were aiming for, reject the change and try again. When you get what you want, accept the changes to the script by clicking `Keep`, and **save the changes** to the script, then follow the Command Line Tutorial you just created for yourself.

*Elephant*

*Tiger*

**Now that you're finished editing/modifying the README.md script**
I'd like to show you that you can view this `README.md` script in `Preview` mode right here in VS Code, too, by either finding the buttons and clicking them, or using these keyboard shortcuts:
**As a new tab (my preference)**
Windows/Linux: Ctrl+Shift+V
Mac: Cmd+Shift+V
**Or side-by-side**
Windows/Linux: Ctrl+K V 
Mac: Cmd+K V  

You can't edit these `Preview` modes, but they might be softer on your eyes for following the remainder of the tutorial from within VS Code.

**Now that you can use the terminal**
Check if you have git installed by running this command in your terminal:

```
git
```

If you see usage instructions, then `git` is already installed (great!), and you're done with this step (this should be the case for those who needed to install **Git for Windows** earlier).

**But** if you get an error, [download and install git here](https://git-scm.com/downloads) choosing the correct version for your operating system and choosing the default intallation options.

You will need `git` for the next step.

### GitHub Copilot on GitHub.com

Go to the main page of [this tutorial](https://github.com/karlgrieshop/Bioinformatics_Onboarding) on GitHub.com and click the GitHub Copilot chat icon in the top right.

**Attach GitHub repositories, scripts, local files, etc.**  
The karlgrieshop/Bioinformatics_Onboarding repository should be attached to your Copilot conversation automatically, but if not, attach it by clicking the "+" icon in the chat prompt area and selecting **Repositories** and finding karlgrieshop/Bioinformatics_Onboarding. 

Attach a local file, specifically, your modified `README.md`, by clicking the "+" icon in the chat prompt area and selecting **Upload from computer** and finding your modified `README.md` file.

Now, write your own detailed prompt in the Copilot chat on GitHub.com, with the repo and your personalized `README.md` attached as context, asking for step-by-step instructions to:
1. Fork a copy of the karlgrieshop/Bioinformatics_Onboarding repo to your GitHub account,
2. Clone that copy to your local machine using the terminal command `git clone` and the HTTPS link for the repo. 
**Tip**
- If you don't know what "repo", "fork" and "clone" mean, ask Copilot.
- If you want your forked copy to be private, change that in the settings of your forked repo.
- Think about where you want to clone the repo to on your local machine.
  - Design the directory names and orgnisation logically 
  - Navigate to that directory before running your `git clone` line.

Go!

### Document Changes to Forked Repo

Ok, so you should now have a modified local copy of `README.md` that you downloaded earlier (probably the one you're looking at now), **AND** a local copy of the full Bioinformatics_Onboarding/ repo, with the following structure:

```
Bioinformatics_Onboarding/
├── README.md
├── LICENCE
├── GitHub_tutorial/
│   ├── GitHub_CheatSheet.md
│   └── git_and_GitHub_tutorial.md
├── Unix_help/
    └── Unix_CheatSheet.md
```

Navigate around your terminal to explore that repo using `cd`, `cd ..`, `ls`, `pwd` etc.

**Document your personal command line tutorial in your cloned repo**

1. In your terminal, navigate to your cloned `Bioinformatics_Onboarding/` directory.

2. Create a new directory for your tutorial:
   ```bash
   mkdir Command_line_tutorial
   ```

3. Move into that directory:
   ```bash
   cd Command_line_tutorial
   ```

4. Create a new empty file for your tutorial:
   ```bash
   touch Command_line_tutorial.md
   ```

5. Open the new file in VS Code:
   ```bash
   open Command_line_tutorial.md
   ```
   *Or find another way to open this new file if that command doesn't work on your system.*

6. In VS Code, attach the empty `Command_line_tutorial.md` to your Copilot conversation (and ensure the `README.md` is still attached as well).

7. Prompt Copilot to cut-and-paste your self-guided command line tutorial from in between "*Elephant*" and "*Tiger*" of your `README.md` script (or by explicit line numbers if needed) into this new empty `Command_line_tutorial.md` file. *(Yes, you could cut-and-paste this manually yourself, but practice prompting Copilot well enough to get what you want out of it so you can put it to good use later.)*

8. Review the changes, accept (`Keep`) them if you got what you wanted (fix little things manually if needed), and save both files. Your local clone of the repo should now look like this:

```
Bioinformatics_Onboarding/
├── README.md
├── LICENCE
├── Command_line_tutorial/
│   └── Command_line_tutorial.md
├── GitHub_tutorial/
│   ├── GitHub_CheatSheet.md
│   └── git_and_GitHub_tutorial.md
├── Unix_help/
    └── Unix_CheatSheet.md
```

**We would be ready to document those changes on your forked copy of the GitHub repo, but we need to set up your SSH key first.**

**Disclaimer**
*Outside this module, check with your supervisor or employer and follow institutional/data‑protection policies before putting any sensitive or proprietary material into AI prompt windows. Avoid pasting raw data. You are responsible for any accidental disclosure.* 

---

## SSH Keys

Setting up Secure Shell (SSH) keys allows you to securely push and pull code between your local machine and your GitHub repositories without entering your authentication token every time. The steps below work for **Windows (Git Bash)**, **Mac**, and **Linux**. If you need more detail, see [GitHub's official SSH key guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) or watch this [YouTube tutorial for SSH keys](https://youtu.be/snCP3c7wXw0?si=HpI1Uk76GgxFqJxY).

1. **In your terminal, make sure you are in your home directory:**
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
   - Must be the email address registered to your GitHub account.
   - If you get an error about ed25519 not being supported (rare, but possible on older systems), use:
     ```
     ssh-keygen -t rsa -b 4096 -C "your_email@uea.ac.uk"
     ```
   - When prompted for a file location, press Enter to accept the default.
   - You can set a passphrase *BUT* I suggest leaving it empty (just press Enter again).

   **Windows users:** If using Git Bash, these commands work as written. If using PowerShell, you may need to install OpenSSH and use slightly different commands — see [GitHub's SSH key guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

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

7. **Test your SSH connection to GitHub in the command line:**
   ```
   ssh -T git@github.com
   ```
   - The first time, you may be asked to confirm the connection. Type `yes`.
   - If successful, you'll see a message like: "Hi USERNAME! You've successfully authenticated..."

**You are now ready to push and pull code to and from your GitHub repositories using SSH!**

---

## Git and GitHub tutorial

Complete the Bioinformatics_Onboarding/GitHub_tutorial/git_and_GitHub_tutorial.md. Rember you can open that tutorial by navigating to that directory and running:
```bash
open git_and_GitHub_tutorial.md
```
*And view it in Preview mode if you prefer*

If you need more help, this is a very slow walk-through of what Git and GitHub are ([here](https://youtu.be/mJ-qvsxPHpY?si=sMApMaZvj5QWwTqd), optional).

**Do not proceed beyond this point until you have completed the `git_and_GitHub_tutorial.md`.

---

## HPC

Ok, by now, you're familiar with the commandline to SSH into the HPC, navigate around, and set up your HPC SSH key. Let's do it (*requires VPN*).  

Go to your terminal and type:

```Bash
ssh `<your.abc12xyz.uea.username>`@hali.uea.ac.uk
```
*Enter your UEA password when prompted*
*If it hangs, not asking for password, you have a VPN or other IT issue.*

**Imediately upon logging in, type:**
```Bash
interactive-bio-ds
```
*Until you run that  `interactive-bio-ds` command, you'll be sitting on the login node, which is equivalent to standing in the doorway while others are trying to get in.*

**Note:** 
*`interactive-bio-ds` is specifically designated for this module to allocate all students and their HPC jobs to nodes that have been partitioned for this module. It will not work for you if you have not been added to the user group. All other users outside of this module (including those doing HPC work after this module ends), should simply use `interactive` rather than `interactive-bio-ds`.*

Ok, so you're on the HPC, in an interactive session... Now:

1. Set up a second GitHub SSH key for your HPC home directory (same steps as the SSH Key tutorial above),

2. Clone your /Bioinformatics_Onboarding repo to your scratch/ directory.

3. You can now push and pull work to/from GitHub on both your local machine and your HPC account. Cool!

**Note:** 
*If you push changes to a repo from one location, or edit the repo directly in github.com, you will not be able to push other changes to that same repo until you've resolved the differences among the different copies (you will get an error regarding "divergent branches"); to resolve use: `git pull --rebase origin main` (see GitHub_CheatSheet.md)*

4. For life moving forward, keep your ongoing unfinished work synced through regular commits to private github repos for each project and *add you supervisor and relevant team members as "collaborators" on the repo*. Discuss with your supervisor or employer about if/when/how to publicly archive a repo under a permanent DOI upon publication (super easy with [Zenodo](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content)).

---

*Congrats! You made it. You're ready for Day 1!*

---

## Bonus

**Unix_help/Unix_CheatSheet.md is yours to keep.**
I hope it's useful. Keep it as a notebook and add to it.

**Workshop 1 (group work):**
Material is located in `/gpfs/data/BIO-DSB/Session1`, you're welcome to get an early start.

**"GitHub Education"**

You can access GitHub Copilot Pro for free via [GitHub Education](https://github.com/education).

1. You can register as as [Teacher](https://docs.github.com/en/education/about-github-education/github-education-for-teachers/apply-to-github-education-as-a-teacher) or [Student](https://docs.github.com/en/education/about-github-education/github-education-for-students/apply-to-github-education-as-a-student) - usually a photo of your Student ID or a redacted pay stub works.

2. [Activate and Confirm your free Copilot Pro subscription](https://github.com/settings/copilot/features).

3. I recommend reviewing GitHub Copilot's data & privacy settings and disabling data sharing if you do not want your code or prompts used for product improvement or model training. Specifically:
   - Go to GitHub → Settings → Copilot → Data sharing (or GitHub.com → Settings → Copilot features) and consider disabling:
     - "Allow GitHub to use my data for product improvements"
     - "Allow GitHub to use my data to improve AI models"
   - Note: organisation (enterprise/university) accounts can enforce or override these settings. Check with your employer or supervisor if you use a managed account.
   - Always enable two-factor authentication on your GitHub account.
   - Avoid pasting sensitive or proprietary data (passwords, patient data, private keys) into AI prompts or editors that may be sent to external services.
   - For full details and the latest wording, see GitHub's documentation on Copilot data and privacy: https://docs.github.com/en/copilot/getting-started-with-github-copilot/about-github-copilot-data-collection

*Reminder:* these settings affect how GitHub may use your data; they do not replace institutional policies. 


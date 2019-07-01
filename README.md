# Welcome To Whiteboard!

Welcome! Before we begin your first day of camp make sure you've completed the following things.

Pre-requisites 
Make sure you've done the below!

- Code Academy Javascript Track, [click here](https://www.codecademy.com/learn/introduction-to-javascript) to start! (ps. don't worry you won't need to pay)
- Mac Setup (below)


# Mac Setup

Before you start your first day as a developer, we'll need some tools to start developing.

- Github & Git
- Terminal
- A text editor (Visual Studio CODE) - where the bulk of your challenges will be done
- Installing Javascript and NodeJS

## 1. Create your github account

If you haven't already created your github account you can do so below :point_down:

[Sign up to git](https://github.com/join)

Remember to also include a photo of yourself!

## 2. Install XCode
Apple’s XCode development software is used to build Mac and iOS apps, but it also includes the tools you need to compile software for use on your Mac. 

First off you'll need to open up terminal, you can find this by clicking the magnifying glass on the top right of your computer and searching `terminal` 

![Terminal Setup](https://www.moncefbelyamani.com/images/spotlight-terminal.gif)

Now copy the following command and paste it onto your terminal.

```bash
xcode-select --install
```

You should see the pop up below on your screen. Click `Install` when it appears. 

Click `Agree` when the License Agreement appears:

![License Agreement](https://www.moncefbelyamani.com/images/install-clt-mavericks-step-2.png)

Your computer will then attempt to find the software, and then will start downloading it. The following popup will appear:

![Install](https://www.moncefbelyamani.com/images/install-clt-mavericks-step-4.png)

Once you see the below you're done!

![Complete](https://www.moncefbelyamani.com/images/install-clt-mavericks-step-5.png)

## 3. Installl Homebrew
Homebrew is a package manager for the Mac — it makes installing most open source sofware (like NodeJs) as simple as writing `brew install node`. 

To install open your Terminal and copy the following command and hit enter.

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

This will ask for your confirmation (hit `Enter`) and your user's password.


Now lets update our package manager:

```bash
brew update
```

If you get a `/usr/local must be writable` error, just run this:

```bash
sudo chown -R $USER:admin /usr/local
brew update
```

Error message or not, proceed running the following in the terminal (you can copy / paste all the lines at once).

```bash
function install_or_upgrade { brew ls | grep $1 > /dev/null; if (($? == 0)); then brew upgrade $1; else brew install $1; fi }
install_or_upgrade "git"
install_or_upgrade "wget"
install_or_upgrade "jq"
install_or_upgrade "openssl"
install_or_upgrade "node"
```

After that's all done let's verify everything has installed!

Run the following commands in terminal

```bash
  node -v
```

You should see something like: `v0.10.31`.

To see if NPM is installed (the package manager for nodejs). This should print the version number and you'll see something like `1.4.27` (it doesn't have to be this exact number).

```bash
  npm -v
```

## 4. Upgrade your Node version 

Now let's set up our node version to the latest version.

```bash
npm install -g n
```

Once thats complete let's set our node version to 8.12

```bash
n v8.12
```

## 5. Visual Studio Code - Your text editor

You can install Visual studio code here: https://code.visualstudio.com/ 

You'll want to select stable version when downloading. 

Once it's completed downloading, install it like any app you would.


## 6. Oh-my-zsh - Pimping your terminal

We will use the shell named `zsh` instead of `bash`, the default one.

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Be careful, at the end of this script, it will prompt for your laptop password again. You have to write it correctly (you will not see it when you type) and hit `Enter`. You should get something like:

```bash
        __                                     __
  ____  / /_     ____ ___  __  __   ____  _____/ /_
 / __ \/ __ \   / __ `__ \/ / / /  /_  / / ___/ __ \
/ /_/ / / / /  / / / / / / /_/ /    / /_(__  ) / / /
\____/_/ /_/  /_/ /_/ /_/\__, /    /___/____/_/ /_/
                        /____/                       ....is now installed!
```

Now quit the Terminal (`⌘` + `Q`), and restart it.

You should see something like this:

![ohmyzsh](https://camo.githubusercontent.com/5c385f15f3eaedb72cfcfbbaf75355b700ac0757/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6f686d797a73682f6f682d6d792d7a73682d6c6f676f2e706e67)

Open terminal and head to the top and select `Preferences` select the "Pro" theme as default in `Profiles`.

Quit and restart Terminal, you should see a black background. 


## 7. GitHub

We need to generate SSH keys which are going to be used by GitHub and Heroku
to authenticate you. Think of it as a way to log in, but different from the
well known username/password couple. If you already generated keys
that you already use with other services, you can skip this step.

Open a terminal and type this, replacing the email with **yours** (the
same one you used to create your GitHub account). It will prompt
for information. Just press enter until it asks for a **passphrase**.

```bash
mkdir -p ~/.ssh && ssh-keygen -t ed25519 -o -a 100 -f ~/.ssh/id_ed25519 -C "TYPE_YOUR_EMAIL@HERE.com"
```

**NB:** when asked for a passphrase, put something you want (and that you'll remember),
it's a password to protect your private key stored on your hard drive. You'll type,
nothing will show up on the screen, **that's normal**. Just type the passphrase,
and when you're done, press `Enter`.

Then you need to give your **public** key to GitHub. Run:

```bash
cat ~/.ssh/id_ed25519.pub
```

It will prompt on the screen the content of the `id_ed25519.pub` file. Copy that text,
then go to [github.com/settings/ssh](https://github.com/settings/ssh). Click on
**Add SSH key**, fill in the Title with your computer name, and paste the **Key**.
Finish by clicking on the **Add key** green button.

To check that this step is completed, in the terminal run this. You will be
prompted a warning, type `yes` then `Enter`.

```bash
ssh -T git@github.com
```

If you see something like this, you're done!

```bash
# Hi --------! You've successfully authenticated, but GitHub does not provide shell access
```

If it does not work, try running this before trying again the `ssh -T` command:

```bash
ssh-add ~/.ssh/id_ed25519
```

### 8. SSH Passphrase

In a terminal window, launch this command:

```bash
sw_vers
```

If your OS version (`ProductVersion` line) is greater or equal than **10.12**, you may proceed with the rest of this section. :warning: Otherwise, skip it and go directly to the Ruby install.

In order not to re-type your SSH passphrase at every `git push`, you can add these lines to the `~/.ssh/config` file:

```bash
touch ~/.ssh/config  # Creates the file if it does not exist
st ~/.ssh/config     # Opens the file in Sublime text
```

And then add these 3 lines to the file. **Save**.

```bash
Host *
  AddKeysToAgent yes
  UseKeychain yes
```


## 9. Postgresql

Later down the weeks we'll talk about SQL and Databases the one we'll be concentrating on his Postgresql,
an open-source robust and production-ready database. 

```bash
brew install postgresql
brew services start postgresql
```

Once you've done that, let's check if it worked:

```bash
psql -d postgres
```

If you enter a new prompt like this one, you're good!

```bash
psql (9.5.3)
Type "help" for help.

postgres=#
```

To quit it, type `\q` then `Enter`.

## 10. Computer setup

### Keyboard speed

Go to  > System Preferences > Keyboard. Set `Key Repeat` to the fastest position (to the right) and
`Delay Until Repeat` to the shortest position (to the right).

### Full Keyboard Access

Go to  > System Preferences > Keyboard. Click on the third tab (Shortcuts). At the bottom of the
pane, click the radio button `All controls`. This way when you get a dialog with several options,
you'll be able to type `Enter` to confirm, or `Space` to choose the cancel option. If you have more than
two options, you can use tab to circle between them.

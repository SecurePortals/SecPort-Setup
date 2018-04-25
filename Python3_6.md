## Installling latest stable version of Python 3

### Overview
>1. Install XCode
>2. Install Homebrew
>3. Install Python3
>4. Check Python Version

### Warning
>Along the way you're going to run into issues, and as thorough as I am I can't predict every issue that you'll encounter while configuring your system, so be ready to use those good ol' debugging skills to figure shit out if it doens't look right! (aka Google)

### What is XCode
>Apple products are known to be safe, reliable, user friendly, and don't have many viruses because their products don't come shipped with the tools that allow users to make changes to their products easily. This restricts the user from making changes that could break the computer or software. It's also the reason why Apple products aren't very customizable (like how on Android products you can customize nearly everything whereas Apple you can't really change much, but the trade off is that Android/Microsoft products are more liable to viruses because all the tools are available out of the box). So in order to address this, we need to download XCode in order to give the capability to our computer to read a programming language that can make edits to our computer. 

### Install XCode
>Follow the directions on this link: https://developer.apple.com/xcode/

### What is Homebrew
>Homebrew is a programming language that will help us download other software onto our computer. Just as Python, Java, C# are all programming languages that have their own purposes to code software, Homebrew is what we call a "package manager", and isn't used like the others to develop software. It only can download packages and update/edit files.

### Install Homebrew
>Follow the directions on this link: https://brew.sh/#install

### Making changes to .bash_profile
>There's a lot of stuff coming and going... and your computer doesn't know how to keep track of all these things! We gotta tell the OS through a file called '.bash_profile', where things are, so that it won't get confused. We have to first open the file, then add a line of code, and then save it. Let me break it down for you:

```bsh
nano ~/.bash_profile
```

>Nano is a text editor built into Bash (we'll talk about what Bash is in a little bit). It is my favorite because it is easy to edit lots of text, and the options are inside of the Terminal window while you're using it. By calling 'nano <text file path>' we're executing the Nano text editor, and telling it to open the file that we put in the path. The '~/' is put at the beginning of a path to say "start in my current folder", and the name of the file is '.bash_profile'.
  
> After we've opened the file, we need to paste the following line of code at the bottom of the text editor:

```bsh
export PATH=/usr/local/bin:/usr/local/sbin:$PATH
```

>In order to save and exit Nano, you hit 'control-x', then 'y', then enter. 'control-x', says "I want to close this file", then Nano says, "Do you want to save your changes?" so you hit 'y', and then you hit enter to complete the exit process.

### Intro to Python
>Python is an example of a 'package' that Homebrew can install. Now that we have XCode and Homebrew, we can install Python through the Terminal (also known as the Command Line). 

>Hey Joel, you may ask, why go through all the trouble of downloading all this software and going through all these hoops, when we could've just gone to the Python website and downloaded Python3? You don't make sense! And then I put my hand on your shoulder and I say: as developers we need control. We need to be able to manipulate software and settings/configurations to meet our needs, and the only way to do this is through the most coveted tool to a developer... le Command Line. 

### Note about the Command Line
>The Command Line, which we can access through the Terminal on Mac computers (the names Terminal and Command Line can be used interchangeably), is a very-very... VERY powerful tool (Note, it's a tool, not a programming language. The language that runs on the Command Line is called Bash). Every computer responds to the Command Line, and it is the spine/nervous system of the OS (Operating System, ex: Windows 10 or macOS High Sierra). Without it, we can't communicate to the computer and tell it to do things. ~~So make it your bitch.~~ Get comfortable using it, because it is important! 

### Installing Python
>Simply run the following code in Terminal: 

```bsh
brew install python
```

>And afterwards run:

```bsh
brew postinstall python
```

>Make sure the right Python version is installed:
```bsh
python --version
```
>If it doesn't say Python 3.6.x (x is a wildcard which represents any number), then there are extra steps that need to be taken to complete installing Python 3! You may have to go back to the 'Installing Python' steps, but instead of installing 'python', install 'python3'.


>Next, we install Django!


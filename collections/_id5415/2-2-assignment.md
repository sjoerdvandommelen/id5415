---
layout: course-page
title: "Shaping behavior with code"
permalink: /module2/assignment
description: "Prototyping Connected Product - Assignment 2"
assignment-id: 2
assignment-of: id5415-2
introduction: In this assignment, you will experience the basics of Python programming. You will write a program that control the connected light bulb. You will rely on code written by others developers and share it with the rest of your team.
prog_environment: VS Code
design: 
code_management: Git, GitHub
computational_concepts: 
---

---

* Do not remove this line (it will not be displayed)
{:toc}

---

In the previous module we setup a prototyping environment and we explored the behaviour of a default Python script running on the Raspberry Pi. It is time to start coding and define ourself this behaviour.

# Step 1: Git Flow

## Task 1.1: Getting the Shared Repository on your Machine

To get your shared repository on your machine, we use 'git clone' with the url to your repository. You can find this url on the GitHub page of your repository. Click on the green drop down button 'Code' and copy the url.

In VS Code you can click on the Source Control button (3rd icon in the left panel) and 'clone repository'.

TODO Screenshot

In the text field that open at the top, paste the url of your repository and press ENTER.

You now have a copy of your team repository on your machine. In the left panel you will recognise the tree of files and directories, including the doc,src and README.md.

## Task 1.2 Edit your files

As we were editing the README.md file on GitHub in the previous module, we can do the same here on our machine.

Each team member can, on its own machine, drag and drop a picture of her/himself in the directory doc/images. You note that this file is shown in green font: it is a new file to new file to track.

Then, open the README.md and edit the Contributor section to show the profile picture. We use again the Markdown image command, adding a maximum width 200 pixels (we don't want the pic to appear unreasonably big).

```bash
![John Doe](doc/images/john.jpg =200x)
```

The README.md file appears now in yellow font: it has been modified.

## Task 1.3 Stage and Commit Changes

We can now prepare our files for a new version. We select the changes we want in this new version. This is called 'staging'.

TODO screenshot list of changes, click on the + to stage changes

Then, we create the new version on our machine. This is called 'commiting'

TODO screenshot commit message and validate button

## Task 1.4 Synchronize

At this stage, each team member as a new version of the repository on its own machine. Note that it is a different one. VS Code as a button 'Synchronize' in the bottom left corner.

TODO screenshot synchronize button

Clicking on this button triggers three action:
* it 'fetches' the new version from GitHub
* it 'merges' this version with the local version
* it 'pushes' the new, merged version on GitHub 

If the merge does not succeed automatically, it prompt you to let you choose, for each conflicting block of code, which one to keep (your's, your teammate's or both).

## Task 1.5: Create a Branch

As every team member start making large contribution to the repository, we can quickly see how merging can get complicated. To minimise this challenge, we suggest the combination of 2 strategies:

* Commit your code as often as possible. The smaller the versions, the greater chances of automatic merge.
* Create separate branches for your features.

TODO In Git, a branch is 

TODO screenshot create new branch

By default you are on the 'master' branch. In VS Code you can create a branch by clicking on the bottom left corner on 'master' (the name of your current branch). A menu pops up, click 'Create new branch from'. In the text field, provide the name of your new feature, e.g. 'feature/john-python-exploration'. Then select the branch 'master' (your branch will start from the master).

TODO screenshot selection master

A more complete tutorial on branches is available by [Atlassian](https://www.atlassian.com/git/tutorials/using-branches).

# Step 2: Turn on the light!

Now each team member can explore Python in there own branch, committing new versions of their code without conflict.

## Task 2.1: Create a Python Script

We write Python code into files with '.py' extension. Let's create a new file 'light.py' in the src folder.

TODO screenshot right click on src, create new file

Paste the following lines in the test.py

```python
# This function 'print' the message 'The light is on!' in the Terminal
print("The light is on!")
```

## Task 2.2: Executing

In the terminal, use the python command followed by the path to your file to execute your Python script:

```bash
python src/light.py
```

The sentence 'Turn on the light!' appear in the terminal.

What is happening? The first line (appearing in green) starts with a hash #. It is a comment and is ignored by the Python interpreter. Do not hesitate to use comment extensively to remember the purpose of a piece of code.

The second line is a function call. The function 'print' displays a message in the terminal. It takes 1 argument, the message to display).

# Step 3 Turn on the light! I mean for real!

In this step we will add a structure to our Python script and import the necessary libraries to control the light bulb.

## Task 3.1 Main Function

The main element of a Python program is its 'main' function. As we saw with print(), a function takes care of a task, such as showing a message on the Terminal. Let's introduct the main() function, which is a function you define as the starting point of you Python program.

In the code below we added 'def main():'. This is the syntax to define the behaviour of a function. Notice that what is 'inside' this function is indented, i.e. moved to the right by one tab. This is how Python recognise that these lines are part of the function.

```bash
def main():
    # This function 'print' the message 'The light is on!' in the Terminal
    print("The light is on!")
```

In the terminal, execute your code again.

```bash
python src/light.py
```

What happened? Nothing! The text is no longer showing up, what is going on? Well, we defined a function main(), but we are not calling it. Like print(), to call our function with can write main() at the bottom of the file.

```bash
def main():
    # This function 'print' the message 'The light is on!' in the Terminal
    print("The light is on!")

main()
```

Execute your code again. We now have our message back. We define main(), then we call it.

## Task 3.2 Libraries

Our Python code is far from having the ability to talk to the light bulb yet. Fortunatelly we do not reinvent the wheel for every piece of code, we can use code written by others: these are called libraries. Add the following 2 lines at the top of your code.

```bash
import asyncio
from kasa import SmartBulb
```

This illustrates two ways of importing libraries into your program. The first statement 'import' **the entire** asyncio library. The second statement is **specifically selecting** the definition 'SmartBulb' from the library called 'kasa'.

* 'asyncio' is part of Python (no need to install). By default, statements of our Python scripts are interpreted one after the other, waiting the previous one to be completed. This is a **synchronous** sequence of statements. However, to control the light bulb we need to send a message over the network, and wait for it to answer back. With synchronous statements, you would block the Python program till you receive this response. Asyncio gives us the ability to execute statements in an **asynchronous** way, meaning that we can send our message to the lightbulb, do something else, then come back where we left when we receive a response from the light bulb.

* 'kasa' is the library that we used in the previous module to control the light bulb. To ensure that we install this library for our project without disturbing any other Python settings, we setup a virtual environment that we call 'venv'. To do so, enter the following command in the terminal.

```bash
virtualenv venv
```

VS Code recognise the creation of this new environment and ask you if you want to switch, click 'Yes'.

TODO screenshot 

Kill (little trash can icon) and reopen the terminal to load this environment. Notice the difference, the terminal statement start with (venv) and the Python environment is selected in the bottom panel.

![Virtualenv](./assets/img/courses/id5415/module2/virtualenv.png)

We can now install it 

```bash
pip install python-kasa --pre
```



async def main():
    bulb = SmartBulb("10.0.1.3")

    result = await bulb.turn_on()

    print(result)

    print("The light is " + light_status + "!")

if __name__ == "__main__":
    asyncio.run(main())
```

**Commit and Push!** You've wrote a new piece of code, let's make sure that Git keeps a version of it. To do so, repeat [Task 1.3](#task-13-stage-and-commit-changes) and [Task 1.4](#task-14-stage-and-commit-changes). Your commit message could be 'controlling the light bulb'

# Step 4 Control flow

## Task 4.1 Condition


## Task 4.2 Loops


**Commit and Push!** You've wrote a new piece of code, let's make sure that Git keeps a version of it. To do so, repeat [Task 1.3](#task-13-stage-and-commit-changes) and [Task 1.4](#task-14-stage-and-commit-changes). Your commit message could be 'shaping the light bulb behaviour'
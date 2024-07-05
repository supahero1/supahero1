We've covered commands in the terminal. Now, time for the file system (fs).

By default, when you open terminal, it will open itself in your home directory, that is `/home/your_name/`. Note that Linux uses slashes while Windows often uses backslashes to denote folders. Also, in Linux `/` is the root, while in Windows `Disk:\` is the root, where `Disk` is some partition letter like `C` or `D`.

You can print the current directory you are in by saying `pwd`. You can print the files that are in the current directory by saying `ls`. That's quite a minimalistic way to list them though. You can try `ls -l` to also include data about access rights, owner, size, last date modified, and more. You can try `ls -a` to also display hidden folders that normally don't interest you. You can also combine these arguments by saying `ls -la` or `ls -l -a` or even `ls -a -l`. In most cases, the order of arguments doesn't matter. Read some of `man ls`, it's not that long. `man pwd` is even shorter.

If you don't know any command from now on, just do `man command_name` to look it up. I hope I won't have to remind you to do it yourself.

A lot of commands are abbreviations of some sort. For instance, `ls` is short for `list`, `pwd` for `print working directory`, and so on. If you're interested about the full name, look it up online. Having it be an abbreviation is beneficial for typing speed and also memorization.

Try `mkdir hi` and then `ls`. The first command creates a new directory with the specified name, and you can see it with the second. Now try `cd hi`. `cd` is a command that lets you move throughout the file system. Look it up on man pages if you haven't already.

Oops, you've been trolled. There isn't even a page for `cd`. That's because it's not actually a program, it's a built in functionality. It can't be realized as a normal program.

`cd` accepts a relative or an absolute path as its only argument. You can read in depth about it [here](https://man7.org/linux/man-pages/man1/cd.1p.html). So if you're saying `cd hi`, you're actually saying `change directory to hi from here`. If you try `cd /hi`, it will be outraged by the absence of the folder, since I assume you haven't created any folder in the root directory called `hi`. Absolute path is if you specify it with a slash at the beginning, which means it goes all the way from the root to where you want to go, explicitly, without taking your current directory into account.

As part of your hashira grade training, I recommend you get to know `rmdir`, `rm`, `touch` and `cat` commands, use them, experiment a bit, but don't use these commands in the root folder as they might do some damage. You can use `ls` in the root folder and see what's there and what's inside all the folders there and so on, you can also use `cat` as it doesn't modify anything, but don't make any changes in there with the other commands. You can make changes in your home directory. You can get back to your home directory from anywhere in the file system by simply saying `cd` or `cd ~`. You can also go back to where you were before the last `cd` command by saying `cd -`. Go on, experiment a bit.

Also, `~` is kind of like a relative path, but also absolute at the same time. You can use it like the root directory `/`, so you can do `touch ~/hi.txt` and it will create a file called `hi.txt` in your home folder no matter where you are in the system. Note that if you log in as a different person, your home folder will change, and so will change the definition of `~`.

By scrolling to the bottom of a manual page, you can see similar commands, in the `SEE ALSO` section. Feel free to explore them too. Sometimes, when you are trying to find something but you don't know quite what, you can find it by searching for similar things and then gradually getting closer and closer to what you want. Or you can just use this to learn more commands.

Now, all of this is cool, but so far we've only covered moving around, creating files, deleting them, listing them. So, let's move onto modifying them. You can do that primarily via text editors like `vi`, `vim`, `nano`, or you can use `echo`, however while being one of the most basic commands, it's quite surprisingly difficult to use to achieve file modification, so let's leave that for later.

You should already have `vi` if I'm not mistaken, however be vary that it's difficult to use. You will need to invest a lot of time into learning it. I personally think it's overkill. It is supposed to be very productive once you grasp it, but it's not like I go around all day modifying files in the terminal. I do that from vscode. If I really have to, I can just use `nano` in a much easier way.

Note that you don't have `nano` installed. You need to get a package with it. Type `sudo apt install nano` to get it. That's the first of many packages you will be getting. Run `nano`. Primarily, there's only 2 key combinations you need to know. `CTRL + X` attempts to close the editor, and then there's `CTRL + S` which saves your work up so far. Essentially, most of the time you will want to press `CTRL + S` followed by `CTRL + X` and that's all there is to it. If you want to modify a given file, just run `nano path_to_that_file` and try out what I just described. If you run `nano` without a file, after pressing `CTRL + S` it will ask for the file name to save the text under. Just fill that in and press enter. After that, you can quit the editor with `CTRL + X`.

[←](../terminal/terminal.md) | [→](../advanced_commands/advanced_commands.md)

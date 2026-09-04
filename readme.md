Hi there.

First let's familiarize you with Unix environment.

# Navigation, running programs.

So, assuming you already logged in to the server, what you see is your shell's prompt. It looks like ```username@the:~$```

`the` is the hostname. full hostname is `the.hell.am`.
username is your username.
`~` is your current directory. `~` (tilda sign) always means your home directory.

`$` sign in shell prompt by convention (but that's convention, you can replace it with anything) means you are user, you have user privileges now. Not administrator (root) privileges.

Any time you want to go to your home directory, you can do

```
cd ~
```

let's try.

```
cd /
```

now you're in the upper directory. you can't go further up. It is called root directory. Because all other directories start here. Like the root of the tree.

Do

```
pwd
```

This shows your current directory.

```
ls
```

See?

Now do

```
ls -al
```

Now let's go back to your home directory. Remember tilda sign?

```
cd ~
```

and then again check what is your current directory.

```
pwd
```

That's your current directory. You are back home.

Now do

```
ls -al
```

You see, this is list of files.
And the list starts with `.` and `..`.

If you look in any directory, those files exist.

One dot means pointer to current directory.
Two dots mean pointer to the directory one level up.

Do

```
cd ..
```

then

```
pwd
```

See?

Now do

```
cd -
```

```
pwd
```

How did `cd` know where to return?

It looked in the list of environment variables.
Environment variables are your shell variables. Remember I said you are working in the shell?

Shell writes you a 'prompt' - that line with `$` sign, where you type your command.
Then it interprets what you have been written.

If you have been written `ls -al` then it calls the program `ls` and passes it `-al` arguments.

Where is the program `ls` located?

To find out, do

```
which ls
```

Now where did `which` command find out where to search for `ls` command?

Try to search for other commands. Commands as a rule just programs that are installed in your operating system.

```
which vim
```

Ok now type
```
env
```

Those are your environment variables currently.

Look, there is environment variable `OLDPWD` and environment variable `PATH`.

First always shows your previous (old) directory.
That's why `cd -` knows where to return. It reads form OLDPWD environment variable.

Do

```
echo $OLDPWD
```

And you'll read the variable.
Whenever you put $ sign in the beginning of the variable, you're reading from it.

And btw, not that i love this shell syntax. I have my problems with it.
But it is what it is.

And PATH contains directory paths, in those the shell will look for a program (command) you typed to execute it.

```
echo $PATH
```

If it's not found in the path, you'll get a message about it.


Type

```
buzinga
```

You see, no such command found.

Now do

```
source /etc/studrc
```

Now repeat the command

```
buzinga
```

You don't have to type it, if you use arrow up twice, it should bring the command again. Then press enter! Ha, it works!

Why?

Do

```
cat /etc/studrc
```

You see, we redefined PATH environment variable.
Now whern you "sourced" that file, i. e. loaded environment variables it describes, your shell also looks for commands in that directory.

Do

```
echo $PATH
```

and see that PATH environment variable changed.


Now, let's run program that is called `true`.

```
which true
```

See it is located in `/bin/true`

Now run it:

```
true
```

And after it, lets read its exit status. It always returns 0.

```
echo $?
```

There is also program `false`.
Run it:

```
false
```

and then

```
echo $?
```

See?

Now, open the file `questions.txt` with vim or nano, and answer questions there.
Make sure you can edit and save it. Only then reopen it and answer the questions by editing the file.

Good Luck.



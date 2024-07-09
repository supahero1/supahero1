Terminal can do a lot. And while I am not planning on teaching you all that it can do yet, since there really is too much, there is one more field we need to talk about, and that is command chaining.

Wouldn't it be cool to, for instance, read a file's contents and send it as input to a program? Or say, save the output of `ls` to a file? It would. It would also be cool to chain the output of one command with input or another. And that too is possible.

We're looking at 5 operators here. The first one fowards the output of something to a file, like so:

```bash
ls > files.txt
```

That one is pretty straightforward, like the next one, to read a file's contents and forward it as input to a command:

```bash
xargs echo < files.txt
```

Now here's a pretty important thing. `echo` as a command accepts input as its arguments, so whatever you specify after `echo` will be the output of the command. The `<` operator passes the file contents as input to the program, so one way or the other we need to get the input to ther arguments of the program. You should know by now that input processing occurs after argument processing, so that's kind of problematic. That's why we can't just rely on the program itself - we need another program to do this conversion for us. It will read all the input, then once that's done it will create the program we ask it to with the input as that program's arguments.

```bash
echo < files.txt
```

This won't actually spit anything out. And that's because the file contents go to the program's input instead of the arguments. And that's where the `xargs` program comes into play. I will give more examples of using `xargs` later on.

Note that while you can read a file using this operator (`<`), you can also read a file with `cat` if you've done your homework. `cat` simply reads a file and spits it out in the program output, and terminal shows that output. The difference between these is that `<` must forward the file contents to an input of some program, no wiggle room here. However, if you have a program's output by itself, you can do a lot with it, like forward it to another program, or save it to a file.

And that's where the most important operator of all comes in - the pipe operator:

```bash
cat files.txt | xargs echo
```

The pipe operator chains the output of the left side with the input of the right side. And of course, `echo` accepts arguments and not input, so we forward the input as arguments using `xargs`. The above command is kind of silly as it's as if we're printing twice, once with `cat` and then once with `echo`, but whatever, it goes to show the point.

Naturally, you can chain for as long as you want. You can do something like this:

```bash
cat files.txt | xargs echo | xargs echo | xargs echo | ...
```

Next, last 2 operators that are kind of the reiteration of the first 2. First, the append operator:

```bash
echo "hello, world!" >> files.txt
```

So, the existence of this operator is stimulated by the fact that `>` by itself will overwrite the entire file with the new contents provided. This operator on the other hand appends the new content to the already existing content in the file. A quick `cat files.txt` confirms that.

And the last but not the least, isn't it a bummer that you can only use `<` in conjunction with a file? Well, you can also type out the input yourself like so:

```bash
echo << EOF
hello world!
EOF
```

So basically, the `<<` operator allows you to specify any arbitrary text as input to a command, but it has to know what are the bounds of this custom text you're providing. That's why the first and the last word is a specific word, often EOF, but it can be anything, literally:

```bash
echo << XDXDXDXD
hello world!
XDXDXDXD
```

Now, you can also chain together the 2 first operators I've mentioned, like:

```bash
xargs echo < files.txt > new_files.txt
```

This basically reads `files.txt` and writes it to `new_files.txt`, unchanged, but with a different command the situation might differ, naturally.

There's special files too. You can forward a command's output to the null file (located at `/dev/null`) which annihilates it quite literally so that you don't see it in the terminal screen. You can also forward just the error output to null and keep the normal output alive. This is possible, because by default the operators above work on the default input/output, however you can change that by explicitly writing so. However, that steps out of the bounds of this tutorial, so I'm only mentioning it so that you know it exists.

If you wanted to call a couple of commands at the same time one after another, you can do that unconditionally by telling terminal where one command ends and another begins by separating them with the `;` symbol:

```bash
ls; ls > files.txt
```

You can optionally add a semicolon at the end there too, but end of input means the end of the command as well, so it's implicit.

All programs have an output code. The Linux convention is to return a zero if program execution was a success, and anything else to denote a failure (a non-zero value). If you wanted to chain commands but conditionally, you can do that like so:

```bash
mkdir hi && cd hi
mkdir hello || rmdir hi
```

The first command (the first line) will first attempt to create a folder called `hi`. If it succeeds (if the exit code was zero), then `cd hi` will run, changing our current directory to `hi`. With the AND (`&&`) operator, the right side will only run if the left side succeeded.

The second command (the second line) will first attempt to create a folder called `hello`. If it succeeds, that's it. The right side doesn't run anymore, because the equation is already determined to be 1. If you have a couple of checks, you only care about the result of the equation really, you don't have to calculate everything in the equation if you already found something that proves or disproves it. The OR (`||`) operator only runs the right side if the left one didn't succeed. If at least one side of an OR is true, the result is true. In the case of the AND operator, only if both sides are true is the result true, so in other words, if one side is false, the other isn't checked.

This is sometimes useful in commands that do something that might fail, like downloading something from the web.

[←](../fs/fs.md) | [→](../actual_env/actual_env.md)

# Chapter 2: Hello World

- A full description of this example can be found in Chapter 2.
- Please remember that the examples here assume that you setup the Vagrant machine.
- Make sure to change the `Makefile` accordingly if you wish to build somewhere else, open an issue if you have problems doing so!
- All the dependencies are already handled if you followed the instructions in the main [README.md](/README.md).

**IMPORTANT NOTE**: If you find differences between what you have here and the copy you own, read [this](#differences-with-the-book-copy-you-have)

## Let's do it!

In the vagrant machine:

Enter into this example folder:

```bash
cd /vagrant/code/chapter-2/hello_world
```

Compile the program and the loader

```bash
make build
```

It will create a BPF ELF named `bpf-program.o` and a Loader named `monitor-exec`.

Now you can execute the bpf program with root privileges and leave it running.

```
# ./monitor-exec
```

The program is made in a way that everytime an `execve` syscall is executed it prints `Hello, BPF World!`.

Now, open another terminal in the same Vagrant machine and issue a command that does an `execve`, for example `ls` does.


```bash
ls
```

It should show something like this:

```
            bash-3309  [000] ....  2951.144342: 0: Hello, BPF World!
```


## Differences with the Book copy you have
The build procedure and code in this example can differ from the actual copy of the book you have.
We are updating the book so that future prints and PDFs are updated but your copy might be different.

**What is different?**
- This examples uses a `Makefile` instead of  `compile-bpf.sh` and `compile-loader.sh`;
- Some code in `bpf_program.c` is different;
- Compiled file names differs, both for the loader and the bpf shared object;

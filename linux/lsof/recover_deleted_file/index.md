# Recover or Reclaim space of deleted open file

## Recover File

When you delete an open file, you are just removing the link to its [inode](http://en.wikipedia.org/wiki/Inode). The inode is still open and data blocks are still _not_ made available for writing until the process closes the file. 

Using {manpage}`lsof(8)`, you can find the [file descriptor](http://en.wikipedia.org/wiki/Inode) under the path `/proc/PID/fd/` (PID is the process identifier) and copy the file descriptor. 

As an example, let's create a file

```shell
$ cd /tmp
$ echo "Hello World!" > hello.txt
```

Hold the file open, run `less` to display the contents and press `Ctrl-Z` to suspend it.

```shell
$ less hello.txt 

[1]+  Stopped                 less hello.txt
```

Remove `hello.txt` file

```shell
$ rm hello.txt
$ ls -l hello.txt
ls: cannot access 'hello.txt': No such file or directory
```

The `hello.txt` file is removed.

Now, let's bring the file back. Get the file descriptor, use `lsof` and grep `hello` / `delete`.

```shell
$ lsof | grep hello
less       2066      hwidjaja  4r  REG   8,32  13   61985 /tmp/hello.txt (deleted)
$ lsof | grep delete
less       2066      hwidjaja  4r  REG   8,32  13   61985 /tmp/hello.txt (deleted)
```

From the output, `2066` is the PID of the process and `4r` is the file descriptor (`r` means that it's a regular file).

Copy the file descriptor to restore.

```shell
$ cp /proc/2066/fd/4 restored_hello.txt
```

Verify

```shell
$ cat restored_hello.txt
Hello World!
```

## Reclaim Space

If you can't kill the process and want to reclaim storage used by the deleted file, you can truncate it. 

```shell
$ > /proc/2066/fd/4
```
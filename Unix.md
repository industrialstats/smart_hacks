# Unix
## Find
1. Find size of all files recursively with a specific file extension ex: `*.txt`. More details [SO-Link1](https://unix.stackexchange.com/a/41552/77596), [SO-Link2](https://unix.stackexchange.com/a/202392/77596)
    ```sh
    find . -name "*.txt" -exec du -ch {} + | grep total
    ```
    where `{}` expands the output from find say `file1.txt`, `file2.txt` and `+` tries to batch up execution as `du -ch file1.txt file2.txt` instead of `du -ch file1.txt` `du -ch file2.txt`
2. 


## Git
1. Find the size of git tracked files.
    ```sh
    git gc
    git count-objects -vH
    ```
    The `size-pack` value in output gives the size of the repository



# SQLite build instructions
## Download and instructions
[Download amalgamation](https://www.sqlite.org/download.html)
[Compiling the command-line interface](https://www.sqlite.org/howtocompile.html)
## Linux
### Unzip archive
    unzip sqlite-amalgamation-xxx.zip
### Compile
    gcc -Os -I. -DSQLITE_THREADSAFE=0 -DSQLITE_ENABLE_FTS4 \
    -DSQLITE_ENABLE_FTS5 -DSQLITE_ENABLE_JSON1 \
    -DSQLITE_ENABLE_RTREE -DSQLITE_ENABLE_EXPLAIN_COMMENTS \
    -DHAVE_USLEEP -DHAVE_READLINE \
    shell.c sqlite3.c -ldl -lreadline -lncurses -o sqlite3 -lm
### Errors
#### shell.c:122:11: fatal error: readline/readline.h: No such file or directory
    sudo apt-get install libreadline-dev
#### sqlite3.c:(.text+0x31baf): undefined reference to `log'
Append `-lm` to compile command
### Create symbolic link
    ~/.local/bin$ ln -s ../../dev/sqlite3/sqlite-amalgamation-xxx/sqlite3 sql

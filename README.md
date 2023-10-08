# anycli command line actions from anywhere to anywhere

command line access to your project utilities. This tool has the abilities that YOU have in the current project folder. Easily accessible.

`anycli`` is a wrapper around commands across all your checked out projects in the selected parent folder.


imagine you have another project and in that project exists a folder
```
ansible-project-a
├── contrib/anycli
│   ├── monitor
│   ├── ...

```

Then you can run `monitor` command from anywhere in your system like this:

```
anycli monitor
```

Thats it. `anycli` will find the command in your directory and run it.

anycli is context aware. It will only discover commands in the same parent folder
as you installed it



# One time setup:

```
# will install `anycli` command line tool and make it accessible in your path
$ ./bin/setup


[INFO] current folder: ~/src/project/anycli
[INFO] building anycli project...       OK
[INFO] verify `anycli/bin` in PATH...   OK
[INFO] found
[INFO] will now look for folders with commands to make available:
[INFO] parent folder: ~/src/project
[INFO] FOUND ansible-project-a/contrib/anycli/monitor OK
[INFO] done
[INFO] You can now run `anycli [COMMAND]` from anywhere on your system
[INFO] Suggestions:
[INFO] anycli alias
[INFO] anycli monitor --help
```

Thats it. You are all setup.



You can run all commands  verbosely to learn more with `--verbose` flag


Now anycli when you run it can pick up all commands it will make accessible from there


`anycli alias customer1`:
make an alias for anycli. In this example we alias the command `customer1` and make it available anywhere.

`anycli discover`:
will rediscover your available `anycli` commands in other repositories. The names of folders to find
are configurable. You can modify this in .anycli config file. (defaults to `.anycli,contrib/anycli,bin/anycli`)

`anycli monitor -- [command params]





## caveat: Multible projects with same command

Multiple projects can potentially have the same name. This is very common if you have several projects
with a `monitor` command. in this case anycli will tell you your options:


```
$ anycli monitor

ERROR anycli monitor command not unique:
found
project-a/contrib/anycli/monitor
project-b/contrib/anycli/monitor

1. either add `-p`/`--project` parameter
2. go to the folder and run command again

```

## Global parameters for anycli

`--verbose`/`-v`: be verbose in the output

`--project`/`-p`: specify project

`--dry-run`/`-d`: dont execute the command, but tell what you would do

`The general format of the input is:

```
anycli [ANYCLI_PARAMS] [COMMAND] [COMMAND_PARAMS]


# ROADMAP

## support multiple customers.
company1-cli, company2-cli aliases would be awesome

## history of commands
could be piped into fzf or similar to ease completion of commands
